---
title: "[SOLVED] Repairing broken packages"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Gorlinux on 2007-08-21
I'm very new to Linux (Ubuntu). Just installed feisty fawn on the weekend (with some difficulty I might add). Anyway, after grueling hours I was finally able to install it to my system. But I have a couple of kinks to resolve:
1/  can't run add/remove programs
2/  can't run update manager
3/  can run synaptic package but there are 3 broken packages namely which (I am guessing) is causing problems 1 and 2, and furthermore preventing me from updating or upgrading. I been trying to fix the problem using synaptic edit fix broken packages but to no avail. The following are the broken packages:
initscripts
upstart
upstart-compat-sysv

If I use terminal to get upgrades, this shows up:

gorlinux@gorlinux:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  initscripts: Depends: sysvutils but it is not installable
  upstart: PreDepends: sysvutils (>= 2.86.ds1-14.1ubuntu11) but it is not installable
  upstart-compat-sysv: Depends: sysvutils (>= 2.86.ds1-14.1ubuntu11) but it is not installable
E: Unmet dependencies. Try using -f.

When I try to use -f, this shows up:

gorlinux@gorlinux:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  initscripts startup-tasks system-services ubuntu-minimal upstart
  upstart-compat-sysv upstart-logd
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 1212kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19381 package `zenity':
 `Depends' field, invalid package name `libatk1.0-': character `' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

I don't know what to do at this point. Please help. Thanks.

Regards

---

### Post by heimo on 2007-08-21
I'd start by running:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-broken
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get install -f
```Which will make a backup of your current package database status file, and then replace it with a backup that was previously made (automatically).


EDIT: war -> was

---

### Post by Gorlinux on 2007-08-21
Thanks. It's fixed now. Yipee!:)

---

### Post by heimo on 2007-08-21
> **Gorlinux said:**
> Thanks. It's fixed now. Yipee!:)

Excellent. You can mark this thread solved using Thread Tools menu.

---

