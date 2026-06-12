---
title: "Ubuntu to xubuntu [Resolved]"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-01-31
hi

im running ubuntu 6.10 but i would like to run xubuntu 
is there any way to install xubuntu over my ubuntu but still have all my docs and package i installed

Thanx,
            Nolander

---

### Post by taurus on 2007-01-31
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by Nolander on 2007-01-31
The termial rights:
Unknown command "xubuntu-desktop"
aptitude 0.4.1
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

---

### Post by taurus on 2007-01-31
```
sudo aptitude update
sudo aptitude **install** xubuntu-desktop
```

Mooooo...

---

### Post by Nolander on 2007-01-31
thanx it work

but i dont see the diferents between the to script

and wats with the 'MOOOOOOOOOOOOOOOOOOOOO'

---

### Post by taurus on 2007-01-31
You forgot to include **install** in there.  That's why you got this error message at the end.

```
This aptitude does not have Super Cow Powers.
```
In other words, mooooo...  :lolflag:

---

### Post by aysiu on 2007-01-31
> **Nolander said:**
> 
but i dont see the diferents between the to script You probably typed ```
sudo aptitude xubuntu-desktop
``` You were supposed to type ```
sudo aptitude install xubuntu-desktop
```

---

