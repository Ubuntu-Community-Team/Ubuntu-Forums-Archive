---
title: "DVD not seen"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by imagesbytjm on 2007-09-18
Brand new to linux (Mac user). Installed Dapper to Dell 8000 laptop as learning tool. Lots of video issues on install but found answers in How To's and forum.  Can't seem to find post on getting DVD player to work.

Dell inspiron 8000, PIII, 256ram, LG DVD ROM.  Matshita CD/RW, Dapper 6.06.1 only (no Windoze partition).

In Disk Manager both the CD and DVD show up as CDROM's. It see's the DVD and even see's it a LG DVD ROM and calls it device /dev/hdb. The CD/RW is reognized as Matshita CD-RW and is /dev/hdc.

If I put a DVD in the player I get a message  the DVD's title and icon come up on the desktop but I get a message:"Totem could ot play "dvd:////Title"
                               No URI handler for "dvd"

I tried going into Terminal and doing mount (mount /dev/hdb) and I get the message "can't find /dev/hdb in /ect/fstab or /ect/mtab. 

The CD/RW works fine. 

How do I get Ubuntu to recognize the DVD player.

Thnks

TJ

---

### Post by klytu on 2007-09-18
Have you installed the multimedia codecs and libdvdcss? If not or if you have no idea what I mean, check out this link:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

and especially this one for DVD playback:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability)

---

### Post by mikeyphi on 2007-09-18
This guide might help: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability)

and you could consider installing a newer version of ubuntu - a lot of early issues have been improved, I've looked at Gutsy (7.10)  due for general release in October - it's got a lot going for it!

---

### Post by imagesbytjm on 2007-09-18
Ok, looks like the solution is to download and install a software package.  I 've come across the same solution for several of the other issues (fan control, screen resolution).  Is there anyway to download the package to another computer, copy to cd and transfer to the linux machine? I tried it with i8kurils and now have the package sitting on my Ubuntu desktop but can't figure out how to load it.  

I was planning on fixing most of the issues first before I fought the wifi war (Apple Airport WEP), but it looks like I need to get it on-line before I can fix the other problems.  

Thanks for the pointer to the 6.06 manual, looks like lots of good info. 

TJ

---

### Post by mikeyphi on 2007-09-18
Try the suggestion in this thread: [http://ubuntuforums.org/showthread.php?t=547328](http://ubuntuforums.org/showthread.php?t=547328)

---

### Post by imagesbytjm on 2007-09-18
I am not sure that's a logical plan, install Ubuntu on one of my Mac's so I can download the software to get the Dell PIII linux test bed working....

Guess I'll go fight the wifi wars.  It's always something...

Thanks for the pointers. 

TJ

---

