---
title: "iBook G3 &amp; Split Screen Problem"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by chipbutty on 2006-06-13
Each time I run the Ubuntu CD (Dapper Drake), either to use live or try to install it on my iBook G3, the screen is split. The upper and lower halves are reversed, so the top of an Ubuntu window is actually on the lower half of my screen. I tried installing it on my iMac G5 but the fan went into warp speed and sounded like the machine was about to take off. I've since read the problems with the iMac but not the exact issues I'm having with my iBook. I have the resolution set at 800x600 and wonder if Dapper needs better. Is there anything I can do to get Dapper installed properly on the iBook?

---

### Post by xfile087 on 2006-06-13
Can't you just do the text based install? I don't know about the PPC version but i'm sure with the x86 version when you boot from CD you can boot the LiveCD install or install text based.

---

### Post by chipbutty on 2006-06-13
I don't know about that. If a text install is possible (and I haven't done one before,) will it sort out the problem I have, or once installed will the screen still be divided? This is frustrating as I'd really like to get Ubuntu running on my iBook.

---

### Post by RIVE on 2006-06-16
I had the same problem when trying to install dapper from the live cd, i resolve that writing in the xorg.conf file the HorizSync and VertRefresh from a console, or installing dapper from the "alternate" cd, -this is the easiest one-, with that you won't have problems.

:p

---

### Post by chipbutty on 2006-06-18
Thanks for the advice . I'll download the alternate cd while I'm watching the world cup! Not sure what the alternate cd is but the Live one just never worked out at all.

---

### Post by timothyt on 2006-07-14
I am having the same exact problem.
I received a fresh disc in the mail, first tried the Live Cd and the screen was split. I formatted the drive and installed from the disc and I am still getting the same split screen. 

iBook 366 G3  576 MB RAM

---

### Post by avtolle on 2006-07-14
If you can, you should download the Alternate CD; there seems to be many issues w/the Live CD, and as you installed from it, you wish to use 6.06. From the silence on this thread, I presume the alternate CD install went well for the OP. Note that if you do not have good web access, this may well be difficult to accomplish. Perhaps you should start a new thread?

---

### Post by ixus_123 on 2006-07-17
I'm having this problem too.  The alternative CD is not an option for me as my iBook (366mhz indigo clamshell) doesnt want to read CDs of Ubuntu that I or any of my friends have burnt.

I just recieved the Live CD in the post & in Live mode & install teh screen is split.

Also, after install the reolution is too high (1024x768 i think) for my iBook whos display maxes out at 800x600

any tips / help would be most welcome

---

### Post by ixus_123 on 2006-08-02
anyone??

---

### Post by avtolle on 2006-08-03
[http://www.ubuntuforums.org/showthread.php?t=223046&highlight=g3](http://www.ubuntuforums.org/showthread.php?t=223046&highlight=g3) especially post #4, about editing your xorg,conf file, which is what I think needs to be done. HTH.

---

### Post by ixus_123 on 2006-08-04
Apple; Apple iBook 800x600; 0; 28-50; 43.0-75.0

^ note to myself about horizontal & vertical refresh rate settings for my iBook.

---

### Post by ixus_123 on 2006-10-03
> The magic word is "iMac G3". The Live CD does not set up xorg.conf properly.

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt - may take a few tries)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome (note: with the Dapper Live CD, use sudo killall -HUP gdm if Gnome won't restart.)

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

That worked great for me - I'm bumbping this withe quote as this is the thread that comes up when searching this issue - hopefully it will help out others

---

