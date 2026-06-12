---
title: "dual boot xubuntu with vista"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Mutant Corn on 2008-03-19
I'm trying to install xubuntu to my system's 10GB D: partition(what used to be the useless recovery image), but I can't figure out how to make it install there...I'm sure this is something simple, but I'm utterly lost. Help? :confused:

---

### Post by Xiong Chiamiov on 2008-03-19
Are you familiar with the installation process with another Distro, or is this your first time installing Linux?
You'll have to remove the "D" partition and create a new one, since Windows uses a different file system than Linux.  Actually, you'll want 2, one for swap space and one for the rest (the "root" partition).  See [installing xubuntu]("https://help.ubuntu.com/community/InstallingXubuntu?highlight=%28install%29%7C%28xubuntu%29").

---

### Post by Mutant Corn on 2008-03-19
well that's my problem right there...I was trying to install to an ntfs partition. Thanks!

 I've installed linux before, just not as a DB...I always had the whole disk to use...

---

