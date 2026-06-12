---
title: "desktop trouble in dapper"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by unisol on 2006-07-13
i finally got dapper to boot to a gui(the graphical install crashed the alternate cd hung at selecting software so i had to do a server install and try to installthe desktop from there) however alot of the apps dont work such as openoffice places for your drive icons i viewed /etc/fstab it says hde3 the root for dapper is corrupt i dont expect to have the gui to last for long as it seems that everytime install a package something else breaks. i have a p3,384mb mem,250gb hd (hda1 86 gb winxp, hde2 swap 1gb,hde3 root for dapper30gb) i tried linux for about a year but technically im still a noob can someone help i would greatly appreciate it

---

### Post by mcduck on 2006-07-13
the easiest way to get the desktop working would be to install package 'ubuntu-desktop'

You can do it from command line with 'sudo apt-get install ubuntu-desktop'.

As you have only 386MB of RAM, you could also try using XFCE4 instead of Gnome, by installing 'xubuntu-desktop' instead (or get them both and see wich one you like more)

---

### Post by unisol on 2006-07-13
i try to install ubuntu-desktop and it stops at installing python2.4 im using synaptic at this point when i use apt-get i get dpkg returned an error code 1 maybe ill try xfce although i have always used gnome someone said do a oem install what do you think

---

### Post by mcduck on 2006-07-13
there's absolutely no reason to do OEM install, it's only usefull if you want to sell computers with Ubuntu preinstalled and only makes things more complex with no benefits for normal user. 

But you could use the Alternate CD to do a normal install in text mode.. :)

---

### Post by unisol on 2006-07-13
i tried that and it crashed at selecting and installing 86% so i did the server install and then the desktop install and like i said certain elements dont work open office i click on computer and the cursor starts to spin but i get nothing when i put a cd in the drive it doesnt shoe up on the desktop guess ill kepp working til i get it right](*,)

---

