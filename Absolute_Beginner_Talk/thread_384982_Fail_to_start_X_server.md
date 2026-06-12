---
title: "Fail to start X server"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by zhongwei on 2007-03-15
Hi everyone

complete noob here! I was recently given ubuntu x64 live disk, 

I have tried to run the bootfromcd but receive an error after selecting the option:

start or install ubuntu.  

I see a whole lot of oks go by and then I receive this message:

Fail to start X server (your graphical interface) it is likely that it is not set up correctly. Would you like to view server output to diagnose the problem?
yes         no

I select yes:

X Window system 7.0.0
Release Date 21 December 2005
X Protocol Version 11, Revis 0, Release 7.0
Build Operating System: Linux 2.6.15.7 x86_64
Current operand....
Module loader present
Markers (--) probed, (xx) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) Informational
(WW) warning, (EE) error, (NI) not implemented, ?? unknown

(==) log file: "var/log/X.org.0.log", time: Fri Mar 16 2007
(==) Using config file: "/etc/x11/xorg.conf"

Would you like to view detailed x server output as well

I select yes.

looks same as above

X server is now disabled. Restart GDM when it is configured correctly. 



**Could someone please tell me what this all means and what I should do to fix it? I have got lost in the maze of support files....**

My system 

Athlon64 processor 3700+ 220 Mhz
1 gb ram
nvidia geforce 7600gs

---

### Post by Kateikyoushi on 2007-03-15
It happens because you video adapter is not detected correctly. 
Try this [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3") but use nvidia or nv instead of ati.

This thread has more details. [LINK]("http://ubuntuforums.org/showthread.php?t=379807")

---

### Post by zhongwei on 2007-03-15
hi Kateikyoushi

I followed the link as intstructed. changed graphics card to nvidia (the card was set to nv)

Still did not work

Perhaps this is related to a similar problem I am having with windows xp. Thus the reason I am giving ubuntu a go (also the cool user interface...) 

Problem with xp is unknown to me, ever since I had the graphics card replaced i have had continual faults.. Results in me being unable to play any video (though media players still play sound), despite reistalling xp and all codecs. I am sick of xp! hehe

If anyone out there has any idea how I can get Ubuntu to run (I saw it running on my friends pc, which has specs far below my machine. I am envious ;-)"'' ' Please feel free to drop me a hint!

If this helps (though I have no idea if will)
Graphics card info grabbed from vdtool in xp:

NVIDIA GeForce 7600 GS
Bus Type: AGP 0x/8x
VGA Driver version: 6.14.10.9371

---

### Post by annda on 2007-03-15
first off, i think that in the beginning nv is a better choice than nvidia as driver because (to the best of my knowledge) it doesn't require restricted drivers for the kernel.

also, have you tried vesa? very basic, but it almost always runs correctly.

there are other boot options: F4 gives you some choice. and F6 (extra boot options) lets you directly enter a desired resolution. the most common example being: vga=791 (meaning: resolution=1024x768).

by the way, install problems with video do not translate 1:1 on istalled systems. very likely you will not have those issues after an up-to-date installation.

---

### Post by zhongwei on 2007-03-17
thanks for help. installed now with vesa setting. Now having difficulties changing to correct drivers.. lol I post everywhere

---

