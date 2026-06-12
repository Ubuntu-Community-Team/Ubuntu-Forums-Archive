---
title: "filezilla"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by LinuxFish on 2008-04-10
Another linux rookie looking for help. After installing filezilla, I can't get it to run. I tried typing filezilla in the terminal and got "Segmentation fault (core dump)" so I removed the application. This seems very abnormal from what I can tell. Any idea on what I've done to cause this?

7.10 Gutsy AMD 64

---

### Post by nickpaton on 2008-04-10
Hi Linuxfish and welcome to Ubuntu and the forums.

I cannot replicate your problem and Filezilla downloaded & worked fine for me.

May I suggest that if you're using Firefox as your webbrowser and you are looking for a simple client package, that you use fireftp which is a Firefox extension and has always worked great for me.

Grab it [here]("http://fireftp.mozdev.org/")

Good luck!

Nick

---

### Post by stchman on 2008-04-10
> **LinuxFish said:**
> Another linux rookie looking for help. After installing filezilla, I can't get it to run. I tried typing filezilla in the terminal and got "Segmentation fault (core dump)" so I removed the application. This seems very abnormal from what I can tell. Any idea on what I've done to cause this?

7.10 Gutsy AMD 64

If you were running the 32 bit version Filezilla has a pre-compiled binary for 32bit Linux OS.

You can download the source and compile it on your system.

---

### Post by LinuxFish on 2008-04-10
Thanks! I'll give them those a try.

---

### Post by aeiah on 2008-04-10
there's also gFTP. i was never an ftp power user or anything, but for me gFTP seems more or less the same as filezilla

---

### Post by Oldsoldier2003 on 2008-04-10
> **aeiah said:**
> there's also gFTP. i was never an ftp power user or anything, but for me gFTP seems more or less the same as filezilla

Filezilla's biggest selling point as far as I am concerned is that its is cross platform which makes it easier to support windows users without having access to a windows machine or having to run a VM session to look at the windows ftp client your users are using.

---

### Post by aeiah on 2008-04-10
it was just a suggestion for every day use. not for sysadmin use. eesh. so cool it '*Ubuntu User# 21155*' :p

---

### Post by nickpaton on 2008-04-11
> **Oldsoldier2003 said:**
> Filezilla's biggest selling point as far as I am concerned is that its is cross platform which makes it easier to support windows users without having access to a windows machine or having to run a VM session to look at the windows ftp client your users are using.

Agreed, but so is  Fireftp in that it's a Firefox extension which works x platform.  I use it on both Win and Ubu and it's a cinch to install and use for simple uploading to my webspace held on my ISP's servers.

Bottom line - we don't want to get into a "my ftp's better than yours" type of thing but to get LF up and running as painlessly as possible!

I'm also wondering if LF's problem could be because he (you!) are trying to install a 23 bit program onto a 64 bit OS.
If this is the case, because Fireftp is a Firefox extension program, it will be immune to which xx bit OS you have.

Let us know how you get on and good luck.

---

