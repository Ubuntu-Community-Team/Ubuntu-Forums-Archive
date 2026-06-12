---
title: "how do i use wine?  call me sally and slap me silly"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-07-16
i can't believe i have to ask....

As I've been using ubuntu (feisty fawn) more and more I'm finding far less reasons to use winblows.  One of the last few reasons i need winblows is the myspace im.  Tonight I downloaded wine but i'm unsure of how to use it.  I'm on a toshiba laptop with vista home premium on the other partition.  I'm also on a wireless network and i have madiwifi because i have an atheros chipset.  I must say that ubuntu is far easier to work with than fedora and gentoo!! I would really love to know how to use wine if any of you guys or gals can point me in the right direction to a thread or how to etc i would really appreciate it.  Also let me know if wine works like virtualbox.  I tried putting XP on virtual box and i could not connect to my wireless network.  I messed with the bridge and everything but that's besides the point i guess. if anyone can help please let me know!!

---

### Post by wolfen69 on 2007-07-16
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by avik on 2007-07-16
Normally after you've installed WINE, you can double click on .exes and they'll open through WINE.  To make sure you get any error messages (in case the program won't run), you can run it via the terminal:

```
wine /path/to/file.exe
```

Also make sure you've configured WINE:

```
winecfg
```

---

### Post by kvonb on 2007-07-16
Once you've installed WINE, there should be an entry in your menu under System-Preferences called "WINE Configuration", run that before doing anything else, and it will do all the basic setup stuff (creates a folder .wine in your home folder).

Then you should simply be able to click on the Windows installer .exe and it should install and usually also put either an icon on your desktop and/or a menu entry as well :).

Although I have never had much luck with any Windows messenger progs sadly, they need way too much Windows guff to run!

---

### Post by bradmayne on 2007-07-16
i appreciate the help but i can't find the program that i need it may be because i didn't save the file when i downloaded the program?? i just did the run command. This is on my winblows partition i'm speaking of at this point.  i have my windows partition configured so that i can read and write w/ ntfs -3g.  If anyone can do a walkthrough or point me to one let me know! Thanks for the quick replies so far everyone!!

---

### Post by trak87 on 2007-07-16
> **bradmayne said:**
> i can't find the program that i need it may be because i didn't save the file when i downloaded the program??

Well, you must find the program first before you can run it with wine. If the file was downloaded in Ubuntu you can do a "slocate .exe" and it will find all your .exe programs assuming it ends with .exe. However, if you downloaded this program in windows, by default, slocate won't find anything on your windows partitions. To fix that you need to make a change to /etc/updatedb.conf and then run 'sudo updatedb'. The change is to remove '/media' from the PRUNEPATHS line.

Does that help?

---

### Post by phr0ze on 2007-07-16
Just copy it out of windows on a thumb drive.

---

### Post by bradmayne on 2007-07-17
ok thanks guys/gals I'm gonna see what I can do in the morning! I really appreciate everyone's help and comments!! If I can get WINE to work I don't think I will be using windows at all anymore!  Like I said before I really think that ubuntu is a lot easier to work with than fedora and gentoo!!

---

