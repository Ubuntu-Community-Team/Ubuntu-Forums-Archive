---
title: "Mount error with live-cds"
date: 2013-03-28
forum: Any Other OS
---

### Post by Eesaurus on 2013-03-28
Does anyone have a clue why do i get this error message when trying to  boot some Linux distros live-cds? Well, usually it's usb stick, but the  same error comes with dvd. 
```
(Initramfs) Stdin: error 0
 Mount: Mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error

 Can not mount /dev/loop0 (/cdrom/casper/filesystem. squashfs) on //filesystem.squashfs


```
I've tried to make the bootable stick with UNetbootin and USB-Creator,  no difference. And with two or three different sticks too. Different  burning apps also, when using dvd-disc. Nothing helps.
 

 That happens at least with Puppy Linux, JoliOS, Comfusion Linux, LXLE,  LinuxLite, Deepin etc. Quite many of them really, and some better known  ones too, but i can't remember what they were. Some other distros work  normally, Ubuntu, Xubuntu, Lubuntu, Crunchbang, Antix, Elementary etc...   I find that very strange.

---

### Post by Eesaurus on 2013-03-29
Forgot the specs of my machine. It's HP Pavilion P6-2062 desktop with i3, 6Gb RAM, Nvidia GeForce GT 520 etc... Nothing fancy, just a basic PC.

Ask me, if something important info is missing or the problem itself is unclear.

---

### Post by sudodus on 2013-03-29
This is strange. Obviously you know how to make boot media, since you can make Ubuntu flavours boot.

I have succeeded with Puppy Linux, JoliOS and LXLE. Notice that LXLE states explicitly to use a cloning tool (not Unetbootin) to make a USB boot drive. I was brave and used ***dd*** (nick-named 'disk destroyer'). But I have very good experiences with Unetbootin for most linux distros.

Remember to check that the download was successful. There are often ***md5sum*** or ***shasum*** data at the web-site and you should use it before starting to burn a CD/DVD or make a USB boot drive.

I have found that ***k3b*** is more reliable than Brasero to burn a CD/DVD.

*Edit*: Check if those boot media (CD/DVD/USB drives) work in some other computers!

---

### Post by Eesaurus on 2013-03-29
> **sudodus said:**
> This is strange. Obviously you know how to make boot media, since you can make Ubuntu flavours boot.

I have succeeded with Puppy Linux, JoliOS and LXLE. Notice that LXLE states explicitly to use a cloning tool (not Unetbootin) to make a USB boot drive. I was brave and used ***dd*** (nick-named 'disk destroyer'). But I have very good experiences with Unetbootin for most linux distros.

Remember to check that the download was successful. There are often ***md5sum*** or ***shasum*** data at the web-site and you should use it before starting to burn a CD/DVD or make a USB boot drive.

I have found that ***k3b*** is more reliable than Brasero to burn a CD/DVD.

*Edit*: Check if those boot media (CD/DVD/USB drives) work in some other computers!

I guess my USB drive works, because i can do everything else with it. Every live-cd/usb i've tried starts, i can see the grub menu, but after i've chosen "live-session" or "install" it ends up with that error message. Sometimes i have to use "nomodeset" to get even to that error... And yes, i have tried to burn DVDs with K3B also.

Something to do with UEFI maybe? Well, maybe not, 'cause many distros does install just fine.

---

### Post by sudodus on 2013-03-29
> **Eesaurus said:**
> I guess my USB drive works, because i can do everything else with it. Every live-cd/usb i've tried starts, i can see the grub menu, but after i've chosen "live-session" or "install" it ends up with that error message. Sometimes i have to use "nomodeset" to get even to that error... And yes, i have tried to burn DVDs with K3B also.

Something to do with UEFI maybe? Well, maybe not, 'cause many distros does install just fine.

You are probably right, that UEFI is creating the problem. Some linux distros can manage it (Ubuntu 12.10 and some others). There are several threads in the Ubuntu Forums about this issue. I think you can search for them and find some clues. Select **Advanced Search** at the top of this page, search for keywords 'uefi windows 8' or somthing similar, and User name 'oldfred'.

Good luck :-)

---

