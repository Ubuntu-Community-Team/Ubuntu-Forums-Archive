---
title: "Flickering screen (live cd session on PPC)"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by gegadeath on 2009-06-07
Hi everybody, 
I've been attempting to install ubuntu on a Mac PowerBook G4 for a while. My problem is once the cd (witch is a PPC bootable version of ubuntu 7.10) boots an optional boot menu appears, and when i type live the system starts to load and after 3 or 4 seconds the screen turns black and start flickering. Let me tell you that I tried out all the menus options (nosplash, ofonly..etc)

What should I do please ?!

---

### Post by gegadeath on 2009-06-09
hello folks; 

It seems like my problem has no solution since nobody replied. Could you please confirm that to me, thanks !

---

### Post by 311005901 on 2009-06-10
> **gegadeath said:**
> ...My problem is once the cd (witch is a PPC bootable version of ubuntu 7.10) ...

Have you tried Jaunty yet? The newer version of Ubuntu may solve your problem.

---

### Post by aporeg on 2009-06-12
hi

i have the same problem 
after installing ubuntu 9 on my [B]Apple PowerBook G4 (PowerPC G4 500MHz, 512MB RAM

Well i have to say that, first i try to install with the desktop cd and when i was confronted with the flicker issue i downloaded the alternate cd with that i was able to install ubuntu,well the boot up process went fine ,i even hear the ubuntu startup sound ,but the display screw up in different colours

i then try Ctrl + Alt + F2 to get an command shell ,and then sudo su to get root rights 
after that nano /etc/X11/xorg.conf and i saw NOTHING xorg.conf file was empty

i the try [/B]dpkg-reconfigure xserver-xorg and thats where i stuck right now ,i have to figure it out what i have to put there 


if i know more i will post it

---

### Post by aporeg on 2009-06-13
ok now i have found this xorg.conf in an suse forum 

Option       "DPMS"
  Option       "PreferredMode" "1280x854"
  VendorName   "APPLE"
  VertRefresh  50-70
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x854" "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x854" "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x854" "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x854" "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


i used this ,the flicker stops i have now  vertical color lines in the left corner
problem still not solved,i will post more

---

### Post by gegadeath on 2009-06-24
thnx for ur replies guys, i appreciate that, I will download end try to install jaunty and then tell u if things go well. thanx again !

---

