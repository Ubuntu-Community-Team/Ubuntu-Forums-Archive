---
title: "Desktop Effects could not be enabled ?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Mafia on 2007-12-09
I am using Ubuntu 7.10 , until yesterday i was using 7.04 but i upgraded today using a live dvd 

everything runs fine except for the desktop effects which were running fine in 7.04 

when i goto system > admin > appearence enable desktop effects it says desktop effects could not be enabled

I have tried using both drivers for my Intel Card : 
i810 and the Custom One 
I dont have any restricted drivers

Terminal > lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

Terminal > compiz

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2992' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

I have also tried reinstalling compiz 

and i have attached the entire hardware info of my pc

any help ?

---

### Post by TWO on 2007-12-09
I too am having the same problem in that I recently upgraded to Gutsy Gibbon and am unable to use Desktop Effects.

I am running the distro on a Dell Inspiron 1300. Running the same lspci command as Mafia shows the following details: 

Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Desktop effects has worked on my computer before as this is not the first time that I have installed Gutsy Gibbon.

---

### Post by Mafia on 2007-12-09
This seems to be a very common problem and is probably related to incorrect settings file or something ?

---

### Post by dhobbs on 2007-12-09
The Intel chips have been blacklisted by compiz because of a bug that crashes video playback.  The 810 driver should not be blacklisted though.  There's a way to skip the checks when enabling compiz which will let you use the newer intel driver but you'll have to tweak totem and other video playback application to not use a certain type of playback to avoid crashing.

This link will help in getting the blacklisted card to work, though it will definitely make your system unstable in certain scenarios.  There are a lot of threads about the intel drivers and getting compiz to work with them.  I would suggest a search on these forums or google to get more information.

[http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php](http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php)

---

### Post by Mafia on 2007-12-10
thnx buddy it worked

i used this command :  SKIP_CHECKS=yes compiz

it worked for me , thnx again

---

