---
title: "X Server!!!!"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by itsvan on 2008-04-18
Hi everyone,Ubuntu was fine,,until my friend restarted the X server using 
Sudo dpkg -reconfigure -phigh xserver- org and now everythign is messed up,,my special effects wont work,,video wont work,,3d desktop etc,,it was all fine until he used that code,,what can i do to fix it or even better redo it?? please i need help!!!!!!!!!!

---

### Post by joshrobinson on 2008-04-18
reinstalling your video drivers should clear it up
or re-enter the name of your video driver in your xorg.conf file in the driver section

---

### Post by ad_267 on 2008-04-18
If you're using Gutsy then go to System - Administration - Restricted Drivers Manager and enable your graphics card driver then restart X by logging out and back in or ctrl-alt-backspace

---

### Post by itsvan on 2008-04-18
i shall try this,,thank you for your time,,,hope this works,,,keep checking it might not work!!!

---

### Post by itsvan on 2008-04-18
yo i did that,,but an error screen comes out saying i need this  linux-restricted-modules-2.6.22-14-rt
any suggestions???

---

### Post by DrCoolSanta on 2008-04-18
Install it using System->Administration->Synaptec and download the package . . .
You would need to use the search function to find the package . . .

---

### Post by itsvan on 2008-04-18
THANK YOUUUU VERY MUCH GUYS<<<<YEYEYEYEYEYEYYE:guitar:

---

### Post by erginemr on 2008-04-18
Alternatively, there should be a back up of your previous X screen settings before the application of the reconfigure command. Use Nautilus file manager to browse to /etc/X11 and try to find the back up "xorg.conf-*" dating a few days before. 

You may then try your luck by replacing it with the current one. From a terminal:
```
cd /etc/X11
sudo cp *the_previous_xorg.conf_file_here* xorg.conf
```
and restart your X server with Ctrl+Alt+BackSpace.

EDIT: Ooops! You seem to have solved your problem. Great then. :)

---

