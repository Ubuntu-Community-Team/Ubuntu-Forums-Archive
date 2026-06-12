---
title: "Ubuntu newbie"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Kyle12 on 2006-08-14
I'm interested in burning Ubuntu for a LiveCD, just to take it for a test run before I switch from Windows XP to Ubuntu, however I'm not sure what to burn as far as folders/files to the CD. So basically what do I burn to the CD? All of the ISO files? I haven't even unzipped the Ubuntu package yet.

I'm also wondering since I'm trying this LiveCD on a laptop, will Ubuntu communicate with a router that is connected to a Windows XP machine? :?: 

If someone would guide me through the process of making a LiveCD and booting from it in BIOS it'd be much appreciated. :confused: 


PS. I know Ubuntu or Linux systems, for that matter, do not run certain Windows programs, but is there a way to allow Adobe Photoshop CS2 to run on a Linux system? I don't want GIMP. 

Thank you.

---

### Post by mostwanted on 2006-08-14
There is only one ISO you need, either the Desktop CD or the Alternate CD (text-based installer) for your architecture (probably an Intel/AMD processor, known as the x86 or 386 architecture).

You burn it to a CD using the "Burn as image/ISO" option of your CD burning program.

Insert the CD into your computer and restart. If it doesn't boot from it, you can usually enter the BIOS by pressing down F2 while the boot logo shows and from there you can change the boot order.

---

### Post by meng on 2006-08-14
Burning ISOs to CD: Many guides available, here's just one
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

Some Windows applications can be run in Linux using wine, however Photoshop CS2 is not one of them, I understand. There are other strategies such as Crossover Office, but if your heart is set on Photoshop, then search the forums for advice.

---

### Post by red_Marvin on 2006-08-14
What file you have to download depends on what kind of computer you have.
Since you are mentioning windows I guess that it's based on the x86 architecture. then you should download the iso named "PC (Intel x86) desktop CD"

---

### Post by La1nE on 2006-08-14
Just burn the iso like you would with any iso. 

If you're on an i386, just download the i386-iso ^_^ 
There's a nifty little guide at -> [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
Just follow the guide, and youll be fine. :)

I not sure about the photoshop question tough, try searching the forums. 

Good Luck!

---

### Post by vsridhars on 2006-08-14
A Live CD is just that --> does not allow you to configure a lot of things, load additional drives, save settings.

(You can save settings in many live cd's by referring to an external USB Drive - though I am not sure about the specifics)


a) Burning the ISO --> The ISO is a single file - that is "expanded" into a directory structure and the appropriate CD Boot Location - when it is burnt properly as an ISO (rather than as a plain simple data file)

If you burn the ISO properly - your CD would display a directory tree showing the CD information. 

b) Once you do that, and if you tweak your BIOS to pick up the CD as the first drive in the boot order (The BIOS entering and switching order - is very specific to individual manufacturers - a combination of Ctrl, Alt, shift, Esc, F1 in different combinations works for most). However would advise you to check your PC/Laptop bios details on the web to see the correct keys that give access to the bios.


Rgds
Sridhar

---

### Post by petersjm on 2006-08-14
I believe Photoshop 5 (or was it 6?) was the last release that you could successfully load in Linux via Wine. I have v7 and it doesn't work :(

You could think about using VMWare Server (it's free - search the forums for a HowTo). It's a virtual machine that you can install Windows on and run all your Windows-specific software through that, right inside your Linux box.

---

### Post by kriding on 2006-08-14
as a photoshop junkie, I can say that CS2 does not work on linux, the older version do however, but I'm not sure of what version numbers.

---

### Post by Kyle12 on 2006-08-14
Isn't that ironic... I have Photoshop 6.0 and Photoshop CS2 :p .

---

### Post by samureye on 2006-08-14
You say you want to switch from XP to Ubuntu, but if you want to install maybe you should opt for a dual boot for a while.

---

### Post by Kyle12 on 2006-08-14
I might end up doing a dual boot, after looking through what Ubuntu wireless cards Ubuntu supports. I have this wireless card:


Dell
Wireless 1370 802.11bg
Broadcom 4318 

Comments for the card above:
Ships with Celeron model Inspiron 1300. Tried ndiswrapper and firmware methods linked [WWW] [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear). lspci reports: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Card starts up but cannot find any way to connect to network with dapper 


Its says with this card it won't "Work out of the box" this card isn't supported in installed system, and it has a question mark in the "Supports network install column." I can't get online with Ubuntu with my wireless card? I connect to a router wirelessly, by the way.

---

