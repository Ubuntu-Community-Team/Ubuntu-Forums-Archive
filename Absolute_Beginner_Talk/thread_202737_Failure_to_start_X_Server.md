---
title: "Failure to start X Server"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by tntitangal on 2006-06-23
I upgraded to the new 6.06, could not get on the internet.  Decided to reinstall Breezy 5.10.  That did not work.  Then I thought about removing the 6.06 upgrade, started to do that, but I did not apply the application.  Now, my system can not start the X Server.  I reconfigure the system and got a message about choosing a video card driver, given about 30 choices.  I choose voodoo on a guess, then a message about choose an identifier for the driver, which can be a vendor name or a brand name.  What do I do now?  This is very frustrating!!  Someone please help!!  Thank you!!

---

### Post by Winblowz on 2006-06-23
What video card are you using?

---

### Post by tntitangal on 2006-06-24
I assumed that voodoo is the video card?

---

### Post by airzer0 on 2006-06-24
try sudo nano /etc/X11/xorg.conf
then scroll down to driver area and change it to vesa 
hit ctrl x to save 
then type sudo /etc/init.d/gdm restart
that will atleast give you xserver and your os, then you can work on your video card. you must know what video card you have "a voodoo" i think is not much help

---

