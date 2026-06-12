---
title: "Users with limited capabilities?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by chattanoga on 2005-12-28
Hi, this is my first post.

I am a Newbie on Linux. Earlier experiments (Slackware, Debian, Fedora and Various LiveCDs) has failed due to lacking skills/motivation. Anyway I decided to give Ubuntu (Hoary) a shot on a spare computer, and to my amazement after a couple of hours I ended up with a system that fulfills all my needs (except for gaming). 

A couple of questions:

Question1: 
I want the kids (3 and 6 years old) to be able to use the computer without risking the system or the files, especially on HDB[FAT32]. I plan to let them share one user ID and having it automatically login at boot.
Can I create a user for the kids giving them full access to the computer capabilities and files but not to change the system or add/edit/erase any files, apart from their own home directory? 
I would apreciate if it can be done using graphical dialogues.

Question2: 
Can anyone recommend a 3D graphic card guaranteed to work with Linux?
The current onboard graphics does not handle more demanding games.

Question3:
I want the following* to appear at the bottom of all my posts, how?:confused: :


*Computer: 
HP pavilion 413.se, 512 Mb RAM, Athlon 1800; no graphics card (Nvidia GeForce2 built into the mother board?)
Disks: 
HDA, 40Gb (EXT3, Ubuntu 5.10), 
HDB, 80Gb (FAT32, shared media files, docs, mp3s, images..)

/Chattanoga

---

### Post by Dr Von Bon Bon on 2005-12-28
Well, I'm sorry I can't help you with questions 1 and 2 (I'm still a dirty, dirty noob) but for question 3 click on "User CP" (it's on that brown bar underneath the ubuntu forums logo, on the left) and then you go to the edit signature button from here.

When you get there type in your message and then save the changes.
:cool:

---

### Post by Kimm on 2005-12-28
> 
Can anyone recommend a 3D graphic card guaranteed to work with Linux?
The current onboard graphics does not handle more demanding games.


I recommend pretty much any Nvidia card, I use an NVIDIA FX5500 and I dont have any trubble with games so far (not related to that card anyway).

However: when you change graphics cards X **will** fail to start when you start the computer, so you will have to manualy change the graphics driver, to do that, type this (in terminal, after card is changed):

sudo vim /etc/X11/xorg.conf 

then find the section "Device" and change the driver to "nv", then press escape and type: ":save! /etc/X11/xorg.conf" and press enter

to quit, type: ":quit"

now, X will be able to start, but without 3D support, to get that, download the drivers from the NVIDIA website and run the install script (you cant do this inside X), to do this, you will nead kernel-headers for your kernel installed. Then follow the README specified by the nvidia installer in order to configure your card to use the new driver.

I strongly suggest you dont get an ATI card!

> 
Can I create a user for the kids giving them full access to the computer capabilities and files but not to change the system or add/edit/erase any files, apart from their own home directory?
I would apreciate if it can be done using graphical dialogues.


Sure you can, just create a new user and thats it. In linux no normal user has write access to any system files (but can read almost everything). Only problem is that they might still be able to mount the Fat32 partion, but I doubt that they have the knowledge to acctually do it.

PS.
> 
HP pavilion 413.se, 512 Mb RAM, Athlon 1800; no graphics card (Nvidia GeForce2 built into the mother board?)


If the integrated grapjics card is an NVIDIA card, X might not fail when you install the new card, since it probably uses the same drivers.

---

### Post by sciurus on 2005-12-28
[QUOTE=chattanoga]
Question1: 
I want the kids (3 and 6 years old) to be able to use the computer without risking the system or the files, especially on HDB[FAT32]. I plan to let them share one user ID and having it automatically login at boot.
Can I create a user for the kids giving them full access to the computer capabilities and files but not to change the system or add/edit/erase any files, apart from their own home directory? 
I would apreciate if it can be done using graphical dialogues.
[/QUOTE]

Creating the limited user account and logging them in automatically is easy. Go to System-Administration-'Users and Groups'. Select "add user" and under the "Advanced" tab set "Profile" to "Desktop". Now go to System-Administration-'Login Screen Setup' and set the user you just created
as the "automatic login username" and "timed login username"

You have multiple options for protecting the fat32 partition on /hdb. One is probably to set it to automatically mount read only in your /etc/fstab file. The fstab entry would look something like */dev/hdb1       /media/files   vfat    ro,user,fmask=0111,dmask=0000    0    0*, with /media/files replaced by whatever your actual mountpoint is.
When you use the computer, you could then manually unmount it and remount it read/write. This would take two commands *umount /media/files* followed by *mount -w /media/files*.

A better option might be to automatically mount it r/w, but only give write permission to you. I think the /etc/fstab entry for that would be */dev/hdb1  /media/files  vfat   rw,user,uid=1000,dmask=0022,fmask=0133  0  0* to produce effective permission on directories of 755 and files of 644 with the user created when ubuntu was installed as the owner..

[QUOTE=chattanoga]
Question2: 
Can anyone recommend a 3D graphic card guaranteed to work with Linux?
The current onboard graphics does not handle more demanding games.
[/QUOTE]

Do you have an AGP slot? What sort of games are we talking about? If you need basic video acceleration for things like composite, OpenGL screensavers, and games like Tuxracer, I highly recommend the $30 Radeon 9250. If what you mean is more along the lines of Quake 4, then a $100 Geforce 6600 might be an economical solution. Note: To make the Geforce work you need  [special drivers]("http://www.ubuntuforums.org/showthread.php?t=75074"). The advantage of the Radeon 9250 is that it has native linux support. To make later radeons like the 9800 or x600 work you also need [special drivers]("http://ubuntuforums.org/showthread.php?t=75378").

---

### Post by chattanoga on 2005-12-28
[QUOTE=sciurus]Do you have an AGP slot? What sort of games are we talking about? If you need basic video acceleration for things like composite, OpenGL screensavers, and games like Tuxracer, I highly recommend the $30 Radeon 9250. If what you mean is more along the lines of Quake 4, then a $100 Geforce 6600 might be an economical solution. Note: To make the Geforce work you need  [special drivers]("http://www.ubuntuforums.org/showthread.php?t=75074"). The advantage of the Radeon 9250 is that it has native linux support. To make later radeons like the 9800 or x600 work you also need [special drivers]("http://ubuntuforums.org/showthread.php?t=75378").[/QUOTE]


Yes I have an AGP x4 slot according to this page:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=bph07585](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=bph07585)

Since the computer may be used as a Windows desktop in the future I probably should focus on a higher end Video card, such as Radeon 9800 (or FX5500 mentioned earlier). 

Can anyone explain to me why there aren't any high end 3D video cards for Linux?  This seems to be the final obstacle for making the switch from windows on the home computer.

---

### Post by Dr. Nick on 2005-12-28
[quote=chattanoga]
Can anyone explain to me why there aren't any high end 3D video cards for Linux?  This seems to be the final obstacle for making the switch from windows on the home computer.[/quote] 
The same cards that work in windows work in Linux.
Nvidia has released some pretty good linux drivers for their cards, One package will work with all cards newer then the geforce2 and another will work with all cards older than a gf2.

Ati on the other hand has relesed drivers for their cards that are not that great compared to the windows versions. I have heard that if you go for a ati card shoot for a radeon 9200 or below, which is older and not top of the line , but the driver bugs are worked out.

I to would recommend nvidia cards and then install their drivers from synaptic to enable 3d acceleration.

My card is equivelant to a gefoce 4 mx 440 and I have no trouble playing some games on it, But I dont play the most demanding ones so if you plan to play newer games in linux or windows go for a better card, but regardless of which you choose if its nvidia it shouldnt be to hard to get 3d acceleration in ubuntu

EDiT
To put text at the bottom of all post go to the user cp tab at the top under the ubuntu logo and hit edit signature on the top of the sidebar and paste it their

---

