---
title: "Ubuntu a good choice for this scenario?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by revray35 on 2008-01-03
Good afternoon,

I am of course new to Ubuntu and really excited about it.  Here is the scenario we have, I would like to get more experienced advice on which if either of the ubuntu installations would fit the bill.

I am a youth pastor that works in a smaller church.  We have about 8 computer workstations, all windows, which connect to a server which is running (as far as I can tell) command line linux.  All this server does is support shared drives and printer scripts so we can all use a networked printer in the office.

With the issue of future and people proofing the system, we need to move to something more user friendly than the command line linux system.  

My questions are as follows:

1.  Is Ubuntu the right program to do what we need?
2.  Should we do an installation of ubuntu desktop or server?
3.  Is it possible to install ubuntu on top of the current command line linux, or do we have to wipe the drives and start over.

Thank you for your time reading this post.  I look forward to your responses.

---

### Post by LowSky on 2008-01-03
if all the server is doing is  running shared drives and printer, then I would leave it alone. It could potentially be running a windows server client with out a graphical interface as well. I would try to contact the person who orginlly designed your system and ask if he could explain what he built.

---

### Post by Perfect Storm on 2008-01-03
There's several options here. If you want to use Ubuntu as server with gui, just install Ubuntu default or install Ubuntu server then install a gui upon it (may not be as easy for beginners).


I guess the linux distro that are installed aren't Ubuntu, so a wipe out may be the current option here. Backup of important stuff first is essential.

---

### Post by p_quarles on 2008-01-03
First thing I would do is try to figure out if it actually *is *a Linux server, and if so, what kind. If you can get into the command line shell, type this to find the info:
```
lsb_release -a
```
That should give version info for just about any Linux distribution.

---

### Post by Paulmd on 2008-01-03
> **revray35 said:**
> Good afternoon,

I am of course new to Ubuntu and really excited about it.  Here is the scenario we have, I would like to get more experienced advice on which if either of the ubuntu installations would fit the bill.

I am a youth pastor that works in a smaller church.  We have about 8 computer workstations, all windows, which connect to a server which is running (as far as I can tell) command line linux.  All this server does is support shared drives and printer scripts so we can all use a networked printer in the office.

With the issue of future and people proofing the system, we need to move to something more user friendly than the command line linux system.  

My questions are as follows:

1.  Is Ubuntu the right program to do what we need?
2.  Should we do an installation of ubuntu desktop or server?
3.  Is it possible to install ubuntu on top of the current command line linux, or do we have to wipe the drives and start over.

Thank you for your time reading this post.  I look forward to your responses.


Ubuntu server would do the job, but you'd have to wipe the drives an start over.

First order of business is to find out the specs of your server.

Processor, RAM, hard drive space. and video card. (I can't guarentee that all these commands will work on all variations of linux, but they are reasonably generic)

```
 cat /proc/cpuinfo
```
will give you your cpu specs

```
free -m
```

gives you how much RAM you have, in megabytes.

```
df -h
```
will give you a nice summary of how much space you have available in your filesystems.

```
lspci |grep VGA 
```

will give you the video card.


There could be a good reason you're running a command line only system.

Next, find out what version of linux it is currently running.

```
uname -a
```
to find out the version of the kernel

mine says:
```
Linux paul-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686  GNU/Linux

```



```
cat /etc/*-release
```
to find out the OS

mine says 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

You may be able to simply install gnome or kde on top of your current version. Installing a desktop environment (ubuntu uses gnome, by default), rather than a whole OS.

---

