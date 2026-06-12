---
title: "Ubuntu will not boot"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Snipedogg22 on 2007-05-27
Hi everone here at the Ubuntu forums im a brand new to the amazing world of linux but i have one major problem from stopping me from linux ubuntu will not boot!!! I made my self a live cd and that didnt work at all so i found this new program called Wubi and i installed it a few days ago when i select ubuntu on my boot screen i get this while its loading a dn it just stays there and i cant type any thing and my keyboard i guess frezzes.

find--set-root--ignore-floppies/wubi/boot/linux
(hd0,1)
filesystem type is ntfs,partition type ox7
kernel/wubi/boot/linux find=/wubi/boot/linux quiet ro
(linux-bzImage, setup=ox1c00,size=ox1a82cc)
Initrd/wubi/boot/initrd
(Linux-initrd @ 0x1f85e000,0x791177 bytes)
boot

_


Int 14: Cr2ef800000 er00000000 EIP C020c384 CS 00000060 flags 00010007
stack:C00f7da0 C03f129b c0371d8c 00000002 C00f7da 00f7da0 00000000 00000000 

Please help me anyone i have no idea what to do??!!!???!

---

### Post by riven0 on 2007-05-27
Well, Wubi is in beta, so it may not work for everyone. My advice is to try reburning the liveCD again. Make sure you do it on a low speed - 4 to 6kbs, if possible - and do a md5 checksum. 

I haven't heard many good things about Wubi, so I really wouldn't recommend it, yet.

---

### Post by ugm6hr on 2007-05-27
Might be worth listing your hardware here - if the LiveCD you have is OK - it might be a hardware issue.
The alternate CD sometimes solves the problem.

---

### Post by Snipedogg22 on 2007-05-27
Well my hardware is Hp pavilion a705w with 768 mb of ram and well the live cd works but it says basically the same thing idk wats up

---

### Post by Snipedogg22 on 2007-05-27
ps wats a md5 checksum. \????

---

### Post by ugm6hr on 2007-05-27
> **Snipedogg22 said:**
> ps wats a md5 checksum. \????

It's a code to check whether the CD image is accurate - it's useful because the data could potentially get corrupted either during download or burning the CD, and even a single error is potentially disastrous.

And I thought you said the LiveCD didn't work at all.  But then you said it did work.  I'm a bit confused.

---

### Post by icechen1 on 2007-05-27
> **Snipedogg22 said:**
> ps wats a md5 checksum. \????

It check if the cd(or file) is corrupt or not. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oilchangeguy on 2007-05-27
and just to make sure:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Snipedogg22 on 2007-05-27
Yea the kive cd does the sam thing as wubi but idk i just didnt want to say it work

---

### Post by Pizzarth on 2007-05-27
eh? a livecd shouldn't bring up a bootloader...

did you do it like this?

while the initial boot screen is coming up, the hp thing. Press F8 or whatever it uses to go to the boot menu(or set BIOS), not for operating systems, but what hardware to go from. Then select IDE cd-rom device or somethilng similar to that. that should bring you to a screen with the ubuntu logo and title, with some options like check cd integrity and install/start ubuntu, and that will bring you to the desktop. well it's supposed to

where in there does it not work?

---

### Post by Snipedogg22 on 2007-05-27
When i have the cd in adn restart the computer it brings up the logo and all of that stuff then it goes through that and just sits there like before with the same things

---

### Post by Snipedogg22 on 2007-05-27
When the cds in and i restart it it goes to the logo with the options and then goes through the things i showed and just sits there

---

### Post by ugm6hr on 2007-05-28
> **Snipedogg22 said:**
> When the cds in and i restart it it goes to the logo with the options and then goes through the things i showed and just sits there

I still don't think it's entirely clear what stage you are up to.  More accurate detailed description of *exactly* what happens when you boot from the LiveCD might help.
My advice is to try the "Safe graphics mode" from the "options" after the logo appears.

What Graphics Card do you have?

---

### Post by Snipedogg22 on 2007-06-01
Sry im back i couldn remeber my user name stuff but w.e it goes all the way to the ubuntu start up where it has all those optionns then i hit eneter on start/install ubuntu it goes through a green loading thing linux kernal and then it says what i typed in the beginning of the thread.

---

### Post by Snipedogg22 on 2007-06-01
Ps *** of right now im running on the motherboards graphics do i need a graphics card to run ubuntu?? if so isa 256mb one good enough.

---

### Post by Lucifiel on 2007-06-01
To everyone reading this thread, I managed to find the specs of his computer off the net:

[http://cgi.ebay.com/Refurbished-HP-Pavilion-A-705w-Desktop-Computer_W0QQitemZ130108503632QQihZ003QQcategoryZ140072QQcmdZViewItem](http://cgi.ebay.com/Refurbished-HP-Pavilion-A-705w-Desktop-Computer_W0QQitemZ130108503632QQihZ003QQcategoryZ140072QQcmdZViewItem)

* Computer Model (Company maker, Model Number desktop/laptop): HP Pavillion a705w

* Operating System: Win XP Svc Pack 2

* Processor: Celeron 2.93 GHz

* Ram: Brand new Ram! 512MB, Max Ram 3G
* Video: Intel 82845G/GL/GE,PE/GV
* Hard Drive: 30G HD
* List All Players (CD Drives, 31/2 floppy, zip, card readers...) : Lite On Combo CDRW/DVD
* List All Internet Devices : Agere Systems PCI Soft Modem, Realtek Rtc8139/810X Network Adapter
* Sound: Audio- AC97
* Card reader/USB Ports(Front/back and number of them): Smart Media Card, Render Compact   Flash1/11, MMc/SD, MS/MSpro, 5 USB Ports
* Motherboard: MS-6577 N-Atx

*List All Software Extras: All pre-installed HP Software, Windows XP Label of Authenticity

---

### Post by Lucifiel on 2007-06-01
An intel onboard graphics works fine with Ubuntu, dude!!

It has far better driver support than nVidia and Ati.

---

### Post by Snipedogg22 on 2007-06-01
For one thanks for finding the specs on my computer ill save that just incase i need that again and why wont it work then does anyone know what code is i said on the first page is that just a start up thing or does it tell me something and im missing it???

---

### Post by Lucifiel on 2007-06-01
Okay, sorry for making three posts at once in a thread but here we go:

I managed to find a thread where someone had a similar motherboard to yours. He could not install any Linux distribution on his computer. 

> edwardteac said: I got the Ubuntu installer to run using the parameter "linux acpi=off". 

I think you can put in those codes by pressing F6 at the Ubuntu screen when the livecd loads. Then, type in everything within the quotes and do NOT type in the quotes. 

[http://www.neowin.net/forum/index.php?showtopic=337271](http://www.neowin.net/forum/index.php?showtopic=337271)

Let us know how it goes.

No, I don't know anything about Wubi.

---

### Post by Snipedogg22 on 2007-06-01
Ok that worked all i did was type that in and it worked and ubuntu is GREAT but now my next problem how to i acces the internet if i have a wireless connection i found my router name on ubuntu but when i type in my wep key it dosent work??

---

### Post by Lucifiel on 2007-06-01
Oh crud... I think you'll need to use ndiswrapper or something to set up wireless on your pc?

I'm not sure since I don't own any wireless stuff.

I hope the others will be able to help you out and good luck! :D Btw, try using proper punctuation. It'll allow people to help you more easily. 

Also, be sure to provide the model numbers of all your wireless equipment like router, etc.

---

### Post by Snipedogg22 on 2007-06-01
Ok and thank you

---

### Post by Lucifiel on 2007-06-01
Sure, no problem! :D

Hmmm... still, be sure to provide the model numbers of all your wireless equipment like router, etc. That way, the others can help you. :)

---

### Post by Lucifiel on 2007-06-02
Bump! :D

---

