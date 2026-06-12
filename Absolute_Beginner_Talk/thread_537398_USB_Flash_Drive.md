---
title: "USB Flash Drive"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-28
How do i get it to recognize it, it wont show up on the desktop?

---

### Post by redfox1160 on 2007-08-28
doesnt anyone know anything about this???

---

### Post by the.phantom on 2007-08-28
does it show up in the file system?

Places>computer?

and a small hint
if you are in a hurry i would suggest going to the irc channel
bumping every 10  min will not make people happy here ;D

---

### Post by redfox1160 on 2007-08-28
it doesnt show up there, and i dont know how to use the irc channel

---

### Post by redfox1160 on 2007-08-28
anyone wanna help????

---

### Post by the.phantom on 2007-08-28
[http://ubuntuforums.org/showthread.php?t=537373](http://ubuntuforums.org/showthread.php?t=537373)

ya think maybe you are flooding the forum a bit?

---

### Post by browndog on 2007-08-28
redfox,

What file system is your USB drive formatted in?  I've had a relatively easy time with my USB drive formatted as FAT32, but more difficulty with my second drive formatted as NTFS.  If it is in fact NTFS, there's a utility you can download and install under in the Synaptic Package Manager called NTFS-CONFIG...not sure which repository it's under so make sure they're all enabled.  

Also, to use the IRC (Internet Relay Chat) option for help, use the add/remove programs feature from the tool bar to install XChat.  After that you can connect to the Freenode server and join the #ubuntu channel. 

Hope this all helps.

---

### Post by redfox1160 on 2007-08-28
> **browndog said:**
> redfox,

What file system is your USB drive formatted in?  I've had a relatively easy time with my USB drive formatted as FAT32, but more difficulty with my second drive formatted as NTFS.  If it is in fact NTFS, there's a utility you can download and install under in the Synaptic Package Manager called NTFS-CONFIG...not sure which repository it's under so make sure they're all enabled.  

Also, to use the IRC (Internet Relay Chat) option for help, use the add/remove programs feature from the tool bar to install XChat.  After that you can connect to the Freenode server and join the #ubuntu channel. 

Hope this all helps.

When i click it in windows xp, it says that the file system is FAT...

---

### Post by splintercellguy on 2007-08-28
Can you post output of sudo fdisk -l?

---

### Post by redfox1160 on 2007-08-28
> **splintercellguy said:**
> Can you post output of sudo fdisk -l?

do i just type that into the terminal

---

### Post by splintercellguy on 2007-08-28
Yes, if you are asked for your password, enter it, then just copy what it outputs.

---

### Post by redfox1160 on 2007-08-28
i cant copy it unless it is short, cause ubuntu is on my other computer...

---

### Post by redfox1160 on 2007-08-28
Disk/dev/hda: 13.0 GB, 1302069888 bytes
255 heads, 63 sectors/track, 1582 cylinders
Units=cylinders of 16065 * 512 = 8225280 bytes

      Device Boot   Start      End     Blocks            ID       System
/dev/hda1               1         647     5196996        c       W95 FAT32 (LBA)
/dev/hda2              648    1535     7132860       83      Linux
/dev/hda3             1536    1582    377527+       5       Extended
/dev/hda5             1536    1582    377496         82      Linux swap/Solaris

---

### Post by maalmike on 2007-08-28
What happen when you type lsusb on terminal?

post the result

---

### Post by redfox1160 on 2007-08-28
i didnt, what will that do?

---

### Post by maalmike on 2007-08-28
List the usb devices plugen into your pc, if the usb device that you want is conected it must show there

---

### Post by maalmike on 2007-08-28
Sorry for the bad english, just not my born languaje

---

### Post by redfox1160 on 2007-08-28
> **maalmike said:**
> What happen when you type lsusb on terminal?

post the result

nothing...

---

### Post by maalmike on 2007-08-28
if your flash drive was pluged then it's not detected, that happen to me once, it was the usb port, tried one of the ports at the back of my cpu and it worked just fine, maybe it's the same for you.

Even whe the flash led turns on it wasnot detected

---

### Post by redfox1160 on 2007-08-29
i only have two usbs on the back and neither of them work...

---

### Post by fjf314 on 2007-08-29
I'm not sure if this really helps any, but I remember when I first installed Dapper, my USB flash drive (formatted as FAT32) wasn't initially recognized, either. I had a script on there that I needed to connect to my University's network and I couldn't access it. After I was able to use the script via a CD-R, connect, and download all of the updates that were available for Dapper, my flash drive worked without any problems.

---

### Post by cubeist on 2007-08-29
First of all, do your USB ports work with other devices?  This is the first thing to check, so if you have a mouse or keyboard or anything to check that is the first thing to rule out.

Second, in order to troubleshoot it would be great if you posted the output from typing "lsusb" in the terminal.  It won't fry your computer... for example, here is mine... it just shows if a device is registering in a USB port.

--  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
--

If you can't post that, then the best thing to do is backup the data on the pen drive on your windows box and then reformat the drive as FAT32, then move your data back over to the pen drive.  This is what I had to do for mine to be automatically recognized in linux.  Yours should work as long as your usb ports are working

cheers

---

### Post by redfox1160 on 2007-08-29
nothing poped up when i typed lsusb... also, how would i know if the USB ports on the motherboard even work? And can i put the file in a zip folder so i can fit it on a floppy?

---

