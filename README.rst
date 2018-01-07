Purpose
=======
Make `pacman` parameters looks like `pkg` as in FreeBSD.

Reference
=========
`man 8 pacman`, `pacman` page in archlinux wiki, for `pacman`.
`man 8 pkg`, and Chapter 4.4 in FreeBSD 11 handbook for `pkg`.

Road map
========
Use plain shell script or command line utility at most.
Command `bootstrap`, `convert`, `shell`, `stat` in `pkg` are not applied in `pacman`.
Avoid AUR before every following stuff is done for simplicity. Thus, `create` and `add` in `pkg` are not in scope for now.
Command `help` in `pkg` would be implemented when things are mostly done.

Parameters that I do not know how to translate from `pkg` to `pacman`:

- `annotate`
- `backup`
- `register`
- `repo`
- `rquery`
- `query`
- `set`
- `updating`

Todo list
=========

+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Purpose                                          | `pacman`                          | `pkg`                            | Done? |
+==================================================+===================================+==================================+=======+
| Change the origin for an installed package       | ?                                 | `pkg set -o __from__:__to__; and | ?     |
|                                                  |                                   | pkg install -Rf __to__`          |       |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| List locked packages                             | AUR?                              | `pkg query -e '%a = 0' %o`       | ?     |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| List non-locked packages                         | AUR?                              | `pkg query -e '%a = 1' %o`       | ?     |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Lock packages                                    | `pacman --asexplicit __package__` | `pkg set -A 0 __package__`       | ?     |
|                                                  | seems not permanent               |                                  |       |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Unlock packages                                  | ?                                 | `pkg set -A 1 __package__` or    | ?     |
|                                                  |                                   | `pkg lock __package__`           |       |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Check for missing dependecy                      | ?                                 | `pkg check -d -a`                | ?     |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Check checksum of installed packages             | ?                                 | `pkg check -s -a`                | ?     |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Audit installed packages for security advisories | ?                                 | `pkg audit`                      | ?     |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| List installed packages                          | `pacman -Qe`                      | `pkg info`                       | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Query infomation about installed packages        | `pacman -Qs __package__`          | `pkg info __package__`           | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Determine which package installed the file       | `pacman -Qo __file__`             | `pkg which __file__` or          | No    |
|                                                  |                                   | `pkg shlib __package__`          |       |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Search for remote packages                       | `pacman -Ss __package__`          | `pkg search __package__`         | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Install packages                                 | `pacman -S __package__`           | `pkg install __package__`        | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Install from a file or resources                 | `pacman -U __file__`              | `pkg add __file__`               | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Remove packages                                  | `pacman -R __package__`           | `pkg delete __package__`         | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Fetch                                            | `pacman -Sw`                      | `pkg fetch`                      | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Update list, but not upgrade packages            | `pacman -Sy`                      | `pkg update`                     | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Upgrade from remote repository                   | `pacman -Syu`                     | `pkg upgrade`                    | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Clean cache                                      | `pacman -Sc`                      | `pkg clean`                      | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Remove unneeded packages                         | `pacman -Qdtq \| pacman -R -`     | `pkg autoremove`                 | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
| Version                                          | `pacman -V`                       | `pkg version`                    | No    |
+--------------------------------------------------+-----------------------------------+----------------------------------+-------+
