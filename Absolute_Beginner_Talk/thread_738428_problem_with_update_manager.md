---
title: "problem with update manager"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2008-03-28
I tried to run update manager as the icon has appeared on my panel. When I do so I get the following:


'E:Problem parsing dependency Depends, E:Error occurred while processing abiword-gnome (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I appreciate your help.

---

### Post by jan quark on 2008-03-28
run in terminal

```
sudo apt-get update
sudo apt-get upgrade
```

then 

```
sudo dpkg --configure -a
sudo apt-get install -f
```

any error messages??

---

### Post by shredfitz on 2008-03-28
yes. errors. They are as follows:

E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.


W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

dpkg: unable to access dpkg status area: Read-only file system

---

### Post by shredfitz on 2008-03-28
so the steps you suggested and the error messages that I posted and then I tried to reboot.

I got error messages before x started telling me that I had disk errors on the file system. The messages asked me to log in as root and i followed prompts to fix them.

Then I rebooted and the system started as usual. However, I still cannot run update manager and this is the message I get now:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Golem XIV on 2008-03-28
Try cleaning up apt get with
```
sudo apt-get clean
```
and then
```
sudo apt-get update
sudo apt-get upgrade
```

hopefully this will clear it up.

However, if you're getting filesystem corruption errors and it's not because you forced the computer off (i.e. had your power cut or similar) you may have a disk problem developing.  Do yourself a favour and back up your stuff while you still can.

---

### Post by shredfitz on 2008-03-28
using apt-get clean did not work. The error message when I try to run update is still as follows:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

any other suggestions?

---

