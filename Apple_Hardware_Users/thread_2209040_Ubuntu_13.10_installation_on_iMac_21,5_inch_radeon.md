---
title: "Ubuntu 13.10 installation on iMac 21,5 inch radeon 4670 black screen"
date: 2014-03-03
forum: Apple Hardware Users
---

### Post by m-mrvos on 2014-03-03
Dear Ubuntu community,

I have installed Ubuntu 13.10 on iMac 21,5 inch mid 2010 with radeon 4670...
I am Linux user for more than 12 years...but this is first time i am willing to install it on my iMac and change osx for Linux...
It is working realy great...BUT...

To be able to install it i needed to connect extern monitor on my displayport and that way my iMac monitor would became active...Ones active i can disconect hdmi cable (displayport) and remains active...
When i restart iMac (with extern monitor disconected) i see grub loader and i can choose ¨Ubuntu¨...it starts up , but iMac monitor stays inactive...than after couple seconds i hear start up chime...it comes to log in without problem but i can´t see it.... Than i connect extern monitor (TV) and intern iMac monitor became active again...

When is active everything is working great...i have 3d acceleration, i use steam on it...works great, no problem...

I have tried radeon.modeset=0 and nomodeset and single 1 nomodeset.... i tried even to play with xrandr -q , xrandr --output eDP --mode 1920x1080... no results... i must connect extern monitor to it to became active...it is very anoying 

I hope you guys have solution for me...i really wanna stay on ubuntu...

Thank you in advance

Best regards

Miki

---

### Post by entangled on 2014-03-04
Welcome m-mrvos. 
I seem to have the same type of system as you (iMac mid-2010, modelID 11,2, with radeon 4670) and I've also tried to install linux, in my case alongside OSX.
I agree that, to install linux, you need an external monitor. 
I believe this is because the linux kernel radeon module has its video output connections reversed for this system. 
The internal monitor connection is called 'eDP' and the external connection is called 'DisplayPort0'. The radeon kernel module seems to default to 'DisplayPort0' at startup, or resume after sleep. If that connection is not terminated (cable plugged in to monitor) X doesn't run. Even virtual terminals are missing.
If you plug external cable to a monitor (switched on or not) then you will get virtual terminals, but not X, unless you start kdm manually. X then shows on 'eDP'.
I have set this up only for Fedora 20 so far, booting from refind, installed in OSX. 
Ubuntu disks and USB sticks seem to be unbootable despite trying several different methods of preparing them. My OSX disk is gpt with protective MBR.
Sorry I haven't got an answer but I may have explained why it happens. 
I have reported the radeon module problem to fedora and ubuntu; I believe it has been passed on to kernel developers.
I really would like to switch to linux, but this video problem is too severe to cope with, so I have installed linux in virtualbox on OSX for now.

---

### Post by m-mrvos on 2014-03-04
Hi Entangled,

Thank you very much for explenation... i was thinking it has something to do with video channel or frequentie or even resolution but it is not the case... whole video system remain off until you jump start it with external monitor....
This is not really usable situation for me... i will be trying something else probably...

Do you know if debian or older ubuntu working normal ?

Is there any distro that works with this kind of hardware ?

Thank you in advance

Best regards

Miki

---

### Post by m-mrvos on 2014-03-05
I have solution... I don´t need to connect extern monitor/tv anymore...

I have made dummy displayport -> hdmi ->dvi ->vga connector... 

You need 3 resistors 75 ohm and vga to displayport connector... This way you can made imac think old monitor is connected and graphics card remain active...
It is working GREAT...

on VGA connector you need to place resistor between pins 1 and 6           2 and 7             3 and 8      thats it.....[IMG]http://homepage.ntlworld.com/zath.ras/pic/dummy-2.jpg[/IMG]

I have now fully working imac without black screen....

I am happy

Best regards

Miki

---

### Post by Quackers on 2014-03-06
That's a good fix! :)
Hopefully changes will be made so it's not necessary soon.

---

### Post by m-mrvos on 2014-03-06
Thanx :) It is working very wel... I hope that radeon driver would get some atention so that this  problem get fixed in software...

Best regards

Miki

---

