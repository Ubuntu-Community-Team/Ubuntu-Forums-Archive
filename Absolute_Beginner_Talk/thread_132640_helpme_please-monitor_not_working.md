---
title: "helpme please-monitor not working"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by adambeazley on 2006-02-18
Well i installed ubuntu and I have a dual head video card and the vga monitor is working but the dvi monitor says "out of range".
How do I fix this??
Also I cant seem to get my fat32 partition to mount.

Sorry im a total newbie to linux, im very good at windows and very computer literate, but when it comes to linux, I feel pretty dumb.
so keep that in mind when explaining stuff to me because it will be very easy to go over my head.
thanks
adam

my specs:
AMD 64
radeon 9800pro 256MB-dual head (avg & dvi)
dual booting with XP

---

### Post by knalle on 2006-02-18
read this to get drivers for your ati card

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by adambeazley on 2006-02-19
yea i did that last time and it made my server x or x server crash on startup so I only had command prompt.

---

### Post by adambeazley on 2006-02-19
well i tried it again and after the:
sudo dpkg-reconfigure xserver-xorg
and reboot, the x-server crashes and im stuck in command prompt. This is becoming a pain in the butt, I see why 80% of the world uses windows.
please help

---

### Post by adambeazley on 2006-02-19
well i found something:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

and it talks about getting an old library file here: [http://mail3.mpr.org/mlomker/libdri.a.gz](http://mail3.mpr.org/mlomker/libdri.a.gz)

but now my problem is that I only have command prompt in ubuntu so I dont know how to go download that stuff. Also I tried a tutorial in this forum to mount a fat32 partition but thats not working either.
I need some serious hand holding help here, someone please reply.
Adam

---

### Post by Netisan on 2006-02-19
[QUOTE=adambeazley] 
but now my problem is that I only have command prompt in ubuntu so I dont know how to go download that stuff. Also I tried a tutorial in this forum to mount a fat32 partition but thats not working either.[/QUOTE]
For download and install what you need the command prompt is just OK!
What you need is another question, and I understand you. What I can advise you right now is to check/revise your X configuration with the command **X -configure**. 
Also, you can get more useful help if you copy/post the content of file: **/var/log/Xorg.0.log**. 
The stuff with fat32 partition is quite simple, I think. Please, provide the mount instructions from fstab!

---

### Post by adambeazley on 2006-02-19
well i tried everything, three different tutorials and the ati driver from their website. Anyway I just reinstalled ubuntu and now im back to point A where I need to setup dual monitors. How do I do that? I know it has something to do with writing some stuff to the xorg.conf file but im not exactly sure what to write.
thanks
Adam

---

