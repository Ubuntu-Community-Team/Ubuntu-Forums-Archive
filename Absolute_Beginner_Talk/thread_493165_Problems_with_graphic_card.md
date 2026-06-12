---
title: "Problems with graphic card"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by needhalp on 2007-07-05
i followed some guide on the internet and messed with the graphic card

went into the xorg files and deleted somethings and added other

now when i start the os, it xserver error and always just goes to the command prompt

ive tried opening xorg to like see ifthe original data is still on there somewhere but whenever i try to it says permission denied

---

### Post by dwanders on 2007-07-05
If you have inadvertently run some configuration, there may be a back up of your original config file in /etc/X11/xorg.conf.yyyymmddhhmmss. 

if that file is there, you can get back to where you were by:
boot into the command prompt, and type the following:
cd /etc/X11 <cr>
cp xorg.conf.yyyymmddhhmmss xorg.conf
reboot

see if everything works. If not and you need to completely rebuild your X configuration, try:

Get the information you need for setting up your Video card & monitor (e.g.:

Monitor Make & Model
HZ & Vert Sync

Video Card Make & Model
Amount Ram etc... 

then reboot your computer and run:

dpkg-reconfigure xserver-xorg <cr>

Answer the questions correctly and with your equipment information (take defaults if you have no answer for the questions given) - in the end it will re-write a new xorg.conf for you. Then reboot, cross your fingers and hope everything went well.

---

