---
title: "apt-get problem"
date: 2012-02-13
forum: Any Other OS
---

### Post by /bin/sh on 2012-02-13
I have linux mint with the mate desktop (looks like the ubuntu-10.04 desktop).
When I run ```
sudo apt-get install [something I allready have]
``` it says this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
[something I allready have] is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 mintmenu : Depends: python-mate-desktop but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
The [something I allready have] has NOTHING to do with anything, this happends whenever I try to install anything.
So then I try ```
sudo apt-get -f install
``` it says:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-mate-desktop
The following NEW packages will be installed
  python-mate-desktop
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/83.9 kB of archives.
After this operation, 422 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 276739 files and directories currently installed.)
Unpacking python-mate-desktop (from .../python-mate-desktop_1.0.2-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python-mate-desktop_1.0.2-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/gtk-2.0/evolution/ecal.la', which is also in package python-evolution 2.32.0-0ubuntu6
Errors were encountered while processing:
 /var/cache/apt/archives/python-mate-desktop_1.0.2-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I do not care how I need to fix it (except for reinstalling linux) but I just need it to work.

---

### Post by philinux on 2012-02-13
Moved to other OS / distro forum.

You could also try the Mint forum.

---

### Post by bluexrider on 2012-02-13
Welcome

I would do this

```
sudo apt-get update
```update is used to resynchronize the package index files from their sources. The
           indexes of available packages are fetched from the location(s) specified in
           /etc/apt/sources.list. For example, when using a Debian archive, this command
           retrieves and scans the Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before an upgrade or
           dist-upgrade. Please be aware that the overall progress meter will be incorrect as the
           size of the package files cannot be known in advance.

```
sudo apt-get clean
```clears out the local repository of retrieved package files. It removes
           everything but the lock file from /var/cache/apt/archives/ and
           /var/cache/apt/archives/partial/. When APT is used as a dselect(1) method, clean is
           run automatically. Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

```
sudo apt-get autoremove
```autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for some package and that are no more needed.

```
sudo apt-get update && sudo apt-get upgrade
```Update again to renew / upgrade is used to install the newest versions of all packages currently installed on
           the system from the sources enumerated in /etc/apt/sources.list. Packages currently
           installed with new versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages not already
           installed retrieved and installed. New versions of currently installed packages that
           cannot be upgraded without changing the install status of another package will be left
           at their current version. An update must be performed first so that apt-get knows that
           new versions of packages are available.

---

### Post by /bin/sh on 2012-02-14
Thanks, it worked!

---

### Post by bluexrider on 2012-02-14
Good. Glad to help. Please mark this
(SOLVED

---

### Post by perspectoff on 2012-02-14
Yeah, those errors show up whenever you have installed any program whatsoever with continued unmet dependencies.

There is often a chainlink effect when one dependency is not met -- it can affect several nested program dependencies.

A big problem especially when upgrading systems, is that two different programs require different versions of the same library and fight over it.

This has always been my biggest argument against rolling upgrades, which give me a constant headache. (It's also why I now stick to LTS versions only).

---

