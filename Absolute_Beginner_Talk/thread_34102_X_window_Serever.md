---
title: "X window Serever"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by kobiewolke on 2005-05-13
Hi 

I installed ubuntu on my pc, it's got a AMD64 processor, now I'm not sure if it could be that, but it installs fine, after installation, it tries to start the UI but just flashes, and then gives and error that says, the windows server might need configuration.

Can anyone help in this regard?

Thanx

---

### Post by codejunkie on 2005-05-13
what kind of video card do you have?

---

### Post by kobiewolke on 2005-05-13
[QUOTE=codejunkie]what kind of video card do you have?[/QUOTE]
 I have a Geforce 4 mx 4000

---

### Post by codejunkie on 2005-05-13
same here mine installed fine but i don't have the amd athlon 64 that could be the problem you could try booting into safemode at grub and type dpkg-reconfigure xserver-xorg this will let you manuallly setup the video choose vesa as the driver insted of nv this should work but i cant be sure.

---

### Post by codejunkie on 2005-05-13
also if you have onboard video and the nvidia card make sure the onboard video is disabled in the bios.

---

### Post by kobiewolke on 2005-05-13
[QUOTE=codejunkie]same here mine installed fine but i don't have the amd athlon 64 that could be the problem you could try booting into safemode at grub and type dpkg-reconfigure xserver-xorg this will let you manuallly setup the video choose vesa as the driver insted of nv this should work but i cant be sure.[/QUOTE]
 alright, how do I boot into safe mode with Ubuntu, I'm really new to Linux, as new. So can you explain how to do that if its not too much trouble.

Thanx

---

### Post by codejunkie on 2005-05-13
when you reboot the computer it shows options like ubuntu kernel name,ubuntu kernel name safemode, memtest, and windows if installed.just scroll thru the boot menu until you see safe mode or safe settings. if you don't see that menu you should see something like booting in 5 secs press the esc for menu press the esc key and it will show the boot menu hope this helps.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=kobiewolke]alright, how do I boot into safe mode with Ubuntu, I'm really new to Linux, as new. [/QUOTE]

Safe mode is just the commandline in Linux.

---

### Post by kobiewolke on 2005-05-16
Allright, I typed this in on safe mode : dpkg-reconfigure xserver-xorg  then it said, xserver-xorg not installed? What does that mean, I'm sure it gnu got installed. What can be the problem, I tried it using a RADEON ATI 9800 SE as well, same thing.

Do I have a bad copy?

---

### Post by codejunkie on 2005-05-16
root@ubuntu:~# dpkg-reconfigure xserver-xorg 
it should look something like this you have to be logged in as root if you dont see the root@ubuntu~# you may be just logged in under your normal user account try using sudo dpkg-reconfigure xserver-xorg it will ask for your password enter the password and it should work. if that doesn't work try sudo apt-get update then sudo apt-get install ubuntu-desktop this should get you going if something went wrong installing the xserver. keep me posted on your results

---

### Post by kobiewolke on 2005-05-16
hi 

ok I was logged in as root, as when you go into safe mode, I am automatically root, it still said that it wasn't installed. I have downloaded another copy of Ubuntu, I'm gonna try it, as this is the version for an amd 64. I'll keep you posted as to what happens, if you get some other clues, please let me know.

Thanx

---

### Post by codejunkie on 2005-05-17
another thing to check is if you choose server install when you installed ubuntu if you did that option doesn't provide a gui by default so try sudo apt-get update then do sudo apt-get install ubuntu-desktop either way this should fix the problems with the xserver hope this helps keep me posted on your results.

---

### Post by kobiewolke on 2005-05-17
Hey there, I got it right, I downloaded the version for the AMD64 and it is working fine. Now can I change the or install XFCE? I would just like to know how if it is at all possible.

Thank you

---

### Post by codejunkie on 2005-05-18
open up a terminal and type sudo apt-get update and the sudo apt-get install xfce4 answer yes when prompted and apt will install all the required packages logout click session and choose xfce  that should do it.

---

