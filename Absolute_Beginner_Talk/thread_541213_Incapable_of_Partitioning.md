---
title: "Incapable of Partitioning"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by VISIGODO on 2007-09-02
I can't find a way to re-partition the existing set up. I have tried with Gparted but as my keyboard is an USB one does not start until XP is recognizable. I am therefore trying to do it from the Feisty Fawn CD. The intention is, at first, have a dual system installed i.e. XP+ Feisty.
When I reach the point of partitioning I have the following lines:

/dev/sda ...and nothing else. I assume that is the whole volume.

   /dev/sda1  /media/sda1 (box) 250.048 MB. I have tried to edit this file to redimension it to 50Gb and leave it as primary and under NFTS format...NO WAY.

 free space...(box) 8 MB.... Obviously, it does not allow to mount anything inside such small capacity

Could somebody assist, step by step PLEASE. i AM TOO NEW TO FOLLOW EXPERTS !!!

Thanks

---

### Post by InGunsWeTrust on 2007-09-02
Could you provide a screen shot of your partitioning screen because you made very little sense in your explanation of the problem

---

### Post by VISIGODO on 2007-09-02
Hi there and thanks for quick reply.

Here is the screenshot you asked for. I have still spent all this time trying without success.

Will await your indications to my mistakes with interest.

Visigodo
Barcelona/Spain[ATTACH]42412[/ATTACH]

---

### Post by InGunsWeTrust on 2007-09-02
If there is a padlock next too linux-swap right click it and choose deactivate or swapoff (I don't know which exactly it says) then delete linux swap and delete the extended partition. Then start the installer and when it asks how you want to split up the drive select "use largest contiguous free space"

---

### Post by jw5801 on 2007-09-02
Ok... well for starters there will be an option somewhere in your bios to "enable legacy support for usb devices" or something along those lines that will let your bios enable your usb keyboard before the OS actually boots.

Secondly I'd suggest trying the GParted LiveCD (see the link in my signature) as it's a much newer version than is on the Ubuntu LiveCD and you'll have far fewer issues using it.

Finally what are you aiming to do, and what happens when you try to do it? At the moment you have an NTFS drive and linux-swap with some random blank space. I'm assuming that you have a Windows install on the NTFS partition? You mentioned that you wanted to shrink this to 50GB, you should be able to do that by right clicking on it and going to "resize/move." Then if you want to install Ubuntu on the rest of the drive, I'd delete the linux-swap partition (the installer will create it's own if there isn't one there), and just tell the installer to use the rest of the free space.

If you're getting an error when trying to resize the NTFS partition it's most likely because Ubuntu is automounting it. The easiest way to get around this is to do your partitioning using the GParted LiveCD, then go back to the Ubuntu installer.

---

