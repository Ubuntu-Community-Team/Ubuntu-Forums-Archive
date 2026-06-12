---
title: "Beryl on gnome and kde?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by TooRight on 2006-12-18
I finallyyyy got it all worked out how to install beryl  with XGL on gnome...not a small feat when your comp has an  ATI Radeon X600 card and  I was sooo stoked!!

Until, that is, I installed kubuntu. Kubuntu is my baby, I musttt have it, I love it!! But beryl doesn't seem to, lol. When I try to start beryl in the terminal on kde, I get:

> 
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl-xgl: No composite extension



Is there something extra I have to do to get it working in both gnome anddd kde?

---

### Post by zgornel on 2006-12-18
Do you have 
```
Section "Extensions"
	  Option "Composite" "Enable"
EndSection

``` in xorg.conf ?

---

### Post by TooRight on 2006-12-18
Nope, I have that disabled

> 
Section "Extensions"
        Option      "Composite" "Disable"
EndSection


I installed gnome  first, then Beryl on that, then installed kubuntudesktop on it as well. Beryl works in gnome but not in kde.

When I try to start "beryl" in the terminal in kde, i get this error: 

> 
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension


I can't think of what would be the problem, unless perhaps it's conflicting with the settings in the kcontrol appearance area? I'm certain though that i have seen people running kde with beryl on it :(

---

### Post by bailout on 2006-12-18
beryl certainly works with KDE. I have it installed on my laptop, however, that has an intel chip so I can't help you with the nvidia bit.

Have a look at the howto on the beryl site and look at their forums if you haven't already done so.

---

### Post by pormogo on 2006-12-18
I think the issue you are having is with X or gdm and not with KDE or Gnome. Have you altered the KDE session in /usr/share/xsessions to start in Xgl? If you did not KDE is most likely starting using xorg 7.1 (which is using AIGLX). 

make sure your xgl.sh script looks like this, pay close attention to the bottom line it changes between kde and gnome.

[i]#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec startkde[/i]

beryl attempts to use AIGLX if it is unable to find XGL meaning that is most likely not running in your case.

---

### Post by TooRight on 2006-12-18
That would explain it!! Thanks for your input; i'll give it a try and post back to let ya know how it went!! :D

---

### Post by TooRight on 2006-12-18
Nope, it didn't work :(

I get the ole xorg has crashed twice message and the, please add the following your your xorg.conf file (the composition enable thingy... but my graohics card is an ATI Radeon X600 that is using its propriatory driver :confused:

---

### Post by TooRight on 2006-12-19
Well, I am officially an IDIOT :P hehehe

Okay, what happened was that when i went through the beryl install I made a session name called XGL-Gnome. Then later when I changed the last line of that one file to make it say "exec startkde" I just went and clicked on my session named KDE, thinking it meant it would change my "KDE" session.

Just now I made a change to the xorg.conf file, putting the Option "Composite" to "0" instead of Disable", and i wanted to make sure it hadn't messed up my beryl on my gnome session, so I logged into that one to see, and lo and behond... KUBUNTU with Beryl!! Wooo hooooooooo!!! :P:P

Thanks everyone for your responses and suggestions!! dayummm, i sooo love Ubuntu :D:D:D

---

