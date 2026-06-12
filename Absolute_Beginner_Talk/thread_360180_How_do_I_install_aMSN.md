---
title: "How do I install aMSN?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-02-12
Hey.
I downloaded the package .tar.gz, but I don't know what to do with it.
I followed some "make" and "./configure" steps I saw in other websites, but they didn't work.
Thanks a lot!

---

### Post by master.zen on 2007-02-12
Applications >> Add/Remove Appz >> Internet >> check aMSN  >> OK

---

### Post by meng on 2007-02-12
Enable universe repositories
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

sudo apt-get update
sudo apt-get install amsn

Don't bother installing from source, it's not the Ubuntu way.

---

### Post by Dr Small on 2007-02-12
> **master.zen said:**
> Applications >> Add/Remove Appz >> Internet >> check aMSN  >> OK
That only works if you have "gnome-app-install" installed. If you do, you can do it that way.
But most of the time, I try to use synaptic or apt-get ;)

Dr Small

---

### Post by aalr1986 on 2007-02-12
hey to you all, I got it now
Thanks for ur help!!!

---

### Post by y-lee on 2007-02-12
Users of aMSN 0.97  may want to look at this thread: [aMSN 0.97b - non compiling & antialising fonts & no tab bug & lot more! ]("http://www.ubuntuforums.org/showthread.php?t=216689"). In my case the text in aMSN 0.97 didn't look at all right, and this fixed the problem.

---

