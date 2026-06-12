---
title: "thinking of switching"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by filmore on 2007-08-25
hiya, I am a professional technician, I work in a small shop where I see about 30-40 systems a week, I have a bench system that I use for virus scanning, data copying, data recovery, registry backups and restores, and soforth.
I need to have cd-dvd writing, read write access to ntfs and fat partitions, internet access, and maybe even some data recovery programs.
So far I have tried ubuntu, opensuse, and fedora, and they seem to be limited on what a user can do as far as mounting partitions and whatnot.
so without going on forever what is the distro for me ?

---

### Post by nvteighen on 2007-08-25
> **filmore said:**
> hiya, I am a professional technician, I work in a small shop where I see about 30-40 systems a week, I have a bench system that I use for virus scanning, data copying, data recovery, registry backups and restores, and soforth.
I need to have cd-dvd writing, read write access to ntfs and fat partitions, internet access, and maybe even some data recovery programs.
So far I have tried ubuntu, opensuse, and fedora, and they seem to be limited on what a user can do as far as mounting partitions and whatnot.
so without going on forever what is the distro for me ?

There are no limits in mounting partitions! What you need is to install the ntfs driver so your GNU/Linux OS can manage those Windows partitions. At least in Ubuntu, you can install it by typing this in Terminal:

```

sudo apt-get install ntfs-3g

```

---

### Post by Dr Small on 2007-08-25
Ubuntu can basically do all of that.
I am a small computer repairman, and I use it.

Dr Small

---

### Post by Anzan on 2007-08-25
You can install Gparted to work with partitioning.

---

### Post by Malta paul on 2007-08-25
HI Welcome,

Well it comes down to what you are happy with as there are some very good Linux distros available. you might like to check these links:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

Good luck with your choice :wink:

---

### Post by PilotJLR on 2007-08-25
> **filmore said:**
> 
So far I have tried ubuntu, opensuse, and fedora, and they seem to be limited on what a user can do as far as mounting partitions and whatnot.


Can you expand on what you mean by this? You can do anything with partitioning that you want - way more so than with windows.

---

### Post by dptxp on 2007-08-25
> **filmore said:**
> hiya, I am a professional technician, I work in a small shop where I see about 30-40 systems a week, I have a bench system that I use for virus scanning, data copying, data recovery, registry backups and restores, and soforth.
I need to have cd-dvd writing, read write access to ntfs and fat partitions, internet access, and maybe even some data recovery programs.
So far I have tried ubuntu, opensuse, and fedora, and they seem to be limited on what a user can do as far as mounting partitions and whatnot.
so without going on forever what is the distro for me ?


Knoppix. Will r/w NTFS. Download version 5.1.1. CD or DVD. Great Hadware Detection. Best for Data recovery. Tons of programs.

Knoppix any day. Runs live well. Needs a bit of work to install.

---

### Post by filmore on 2007-08-25
> **PilotJLR said:**
> Can you expand on what you mean by this? You can do anything with partitioning that you want - way more so than with windows.

sure, it seems like all of the drives I try to connect aren't accessible, or I don't have permission to write or read, or make cd's , or "there are no file systems you have permission to mount",and stuff like that,  I'm sure it's just my unfamilierarity with linux .

---

### Post by toidi on 2007-08-25
To gain easy read/write access in ubuntu just install the ntfs config tool.
```
sudo apt-get install ntfs-config
```

You then have a nice gui in Applications/system tools that lets you do what you want with ntfs drives and partitions.

I can't answer any of your other questions as I have only really used ubuntu and do very little data management and backups.

The above, however has worked a treat for me in gaining access to several internal/external drives.

---

### Post by PilotJLR on 2007-08-25
> **filmore said:**
> sure, it seems like all of the drives I try to connect aren't accessible, or I don't have permission to write or read, or make cd's , or "there are no file systems you have permission to mount",and stuff like that,  I'm sure it's just my unfamilierarity with linux .

If you have specific examples, or if you would like to address them one by one, we can help...

You can mount and utilize almost all filesystems through a linux computer now, so there is likely a solution for what you'd like to do.

---

