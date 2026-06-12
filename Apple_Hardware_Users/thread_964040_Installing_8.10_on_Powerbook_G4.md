---
title: "Installing 8.10 on Powerbook G4"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by moviemaniac on 2008-10-30
Hi guys,

my brother tried installing 8.10 (alternate) on his powerbook G4 but he told me the installation failed somewhere after the kexboard detection when the installer is looking for the repositories - it didn't find them. We also tried the update-script from CD (8.04 is currently installed) but it also fails with some repository-error (he's in bed right now so I can't post the full error at the moment).

Anyone with a similar problem?
thanks,
Klaus

PS: He also tried the 8.10 RC live - CD a few days ago and it also failed to load...

---

### Post by mkvnmtr on 2008-10-30
I just tried to upgrade to 8.10 on my powerpc Ibook twice. The error said malformed release file. Looks like it is a repository problem. I guess I will wait until somebody says they have been able to upgrade. I want to see how I do with an upgrade. I have never been able to get one to work before. I also think I will look for a torrent just to have for a last resort.

---

### Post by tiresia on 2008-10-30
I did an upgrade in the last days with 'aptitude dist-upgrade' (after editing my sources.list). I had problems at the beginning with X11, but now everything is working well :)
You can download here a torrent file
[http://ubuntuforums.org/showthread.php?t=963868](http://ubuntuforums.org/showthread.php?t=963868)
But I'm seeing that several people have problems with the installer, because it can't detect the CD-ROM

---

### Post by mkvnmtr on 2008-10-30
Can you tell us how you edited your source file? Or maybe it would be better to start another thread.

---

### Post by tiresia on 2008-10-30
I answered you in another thread:
[PowerPC - How to upgrade from Ubuntu Hardy Heron (8.04) to Intrepid Ibex (8.10)]("http://ubuntuforums.org/showthread.php?p=6068296#post6068296")

---

### Post by moviemaniac on 2008-10-31
Okay, here's a bugreport on launchpad for everyone who has the same issue installing/upgrading from CD:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)

---

