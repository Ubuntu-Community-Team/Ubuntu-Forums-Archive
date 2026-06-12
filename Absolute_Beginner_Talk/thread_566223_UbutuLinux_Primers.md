---
title: "Ubutu/Linux Primers?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by VorlonShadow on 2007-10-03
Is there any good documentation out there anywhere that would help me understand some basic concepts of Linux?  I started in DOS, and moved to Windows, and have started to dabble in Linux lately.  I've just installed Ubuntu, and so far it seems pretty nice.  However, I'm struggling with the following concepts:

1.  The file system, and how it works.  Specifically, where files go, and why you put them there.  Also, how everything (including hardware devices) seem to be hooked into the file system some way or other.

2.  How Installation of programs work.  I'm used to downloading an installation file in Windows, run it, and it puts everything wherever it needs to go, creates some Icons, and installs and starts services (if need be), and you're done.  Installation doesn't seem to be as straight forward in Linux, or at least, it's just different.

If anyone knows of any documents, or help pages on the net that can give me a better understanding of these things (especially from the perspective of a Windows user), that would be great.

Thanks,
Jesse

---

### Post by Paul820 on 2007-10-03
Here's some good info to get you started

[http://tldp.org/LDP/intro-linux/html/index.html]("http://tldp.org/LDP/intro-linux/html/index.html")
[http://www.cutlersoftware.com/ubuntuinstall/]("http://www.cutlersoftware.com/ubuntuinstall/")

---

### Post by Jussi Kukkonen on 2007-10-03
> 2. How Installation of programs work. I'm used to downloading an installation file in Windows, run it, and it puts everything wherever it needs to go, creates some Icons, and installs and starts services (if need be), and you're done. Installation doesn't seem to be as straight forward in Linux, or at least, it's just different.

Very different, yes. Personally I consider software installation (and updates) one of the areas where Linux (and Debian/ubuntu in particular) are lightyears ahead of Windows.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) may help.

---

### Post by freesitebuilder on 2007-10-03
My bookmarks have got a lot of stuff for beginners as I'm a beginner myself :)
[http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder](http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder)

But monkeyblog (How to Install anything in Ubuntu) has gone - domain name expired. Hope this is just a glitch as it was really useful.

---

### Post by VorlonShadow on 2007-10-03
Thanks for the info, I'll read through those.

Jesse

---

### Post by joddbeem on 2007-10-03
This has been a good source of information:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

I am not at all into Linux yet, but:
1. Harddrives, CDroms, floppys and usb-pens, will all be mounted as a file in ubuntu. After mounted they are part of your file system. They are not like in windows, where each new device is its own root. In my Ubuntu the extra HD is /media/hdb/ (hda is the first disk, hda1 & hda2, first and second partition. 

When I installed ubuntu, I chose to have my /home folder on a seperate disk. Within linux I can't tell differense. cd ~ (or cd /home) gets me there, a little confusing, since my /home folder is much bigger (60 GB) than my / folder (40 GB)

2. I downloaded the ubutu live CD. This works like nothing you never seen in the windows world. In one instance, it was extremely slow, due to hardware conflict, but on all my old pc's ubuntu live cd was so easy to use. After some 3 - 5  minutes, you can try out the ubuntu without install, if you choose to, there is a nice GParted program for partitioning, wery flexible, almost like Partition Magic but faster, easyer and a lot more flexible (IMHO).

If live CD works well, a dual boot install should work fine. Multiboot is easyer to build with an existing windows install, than the other way.

---

I find Ubuntu a refreshing experience, the command line interface is a lot more powerfull than msdos and cmd in win, it's still a challenge, and due to the many possibilities of combining I find it somewhat confusing to read other peoples code example.

I also think its fantastic that after less than a hour, you have a complete install with most of the software you ever need installed, like open office word and excell like progs.

gl

---

### Post by Niniel on 2007-10-03
Getting it installed can be a pain though. I wasted quite a few CDs because something went wrong during the iso burning process. And of course it wasn't obvious until I tried to run the CD - sometimes nothing would happen, sometimes the start menu would show, and sometimes it even started to boot before things froze. Lots of fun. :)

---

### Post by VorlonShadow on 2007-10-03
That's strange.  I had no problem creating a CD.  I actually installed it in a Virtual PC on my Windows XP machine, but I used some directions I found for that which were VERY GOOD: [http://arcanecode.wordpress.com/2006/12/19/installing-ubuntu-on-virtualpc-step-by-step/](http://arcanecode.wordpress.com/2006/12/19/installing-ubuntu-on-virtualpc-step-by-step/)  I had to use version 6.06, though, version 7 wouldn't work for some reason.  Once I tried version 6, things seem to be working well.

Jesse

---

### Post by hyper_ch on 2007-10-03
also two good places are:

[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

