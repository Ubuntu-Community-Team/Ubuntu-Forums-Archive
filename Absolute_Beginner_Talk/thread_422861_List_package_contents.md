---
title: "List package contents"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by drjimmy42 on 2007-04-25
Hi guys.  I'm a recent gentoo convert and I'm looking for some help with apt.  

I can't seem to figure out how to do a lot of the things with apt that I used to be able to do with rpm or emerge, like:

* list the files that a package contains
* search packages and have it show the state of those packages, installed, not installed, version numbers etc.
I dont' think that apt-cache search counts here.  --full is too much info and default output just lists packages.  Are they installed? what version? etc.

That sort of thing.  Its all information that is in synaptic, but I'm a command line junky and I'd like to understand what is going on and be able to do ssh admin.  

Thanks a lot.

---

### Post by Nythain on 2007-04-25
```

aptitude 0.4.4
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

```that would the the help for aptitude...
search and show are very usefull
you could also use a gui like synaptic... its grrrrrrrreat!!!

---

### Post by Nythain on 2007-04-25
screenshot of synaptic doing just about everythign you want it to

---

### Post by drjimmy42 on 2007-04-25
Synaptic is cool, but not over ssh.  I did find dpkg however.  I thought that apt was the bottom level but it appears to use dpkg for actual package management.  

I'll also check out aptitude.  Thanks for the pointer.

---

