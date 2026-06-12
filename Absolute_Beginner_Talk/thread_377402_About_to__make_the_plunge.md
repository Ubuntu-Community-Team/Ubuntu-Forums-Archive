---
title: "About to  make the plunge"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by lsutiger on 2007-03-06
OK. I just made a backup of my windoze hard drive(it is a bigger and faster one than the one I am using for testing). I am going to try and create a dual boot system on that drive after wiping it clean. It s a 60gb. How big of a partition should I use for Linux of I am going to have both on there?

I really like iTunes, and need to use PC Anywhere, VS.Net, and a DOS program for work.

I am still having a few quirks with Ubuntu.
I have to restart networking on every boot in order to get an ip for my wireless. I have to remount my usb flash drive with sudo mount -o rw,remount /media/sda1 everytime I need to write to it. The video drivers for SIS suck...all of the fonts seem dithered and my screen doesn't look 'crisp' for a 1280x1024 lcd...iow it seems much sharper in widoze.

Anyhoo I am taking the plunge. I have a couple of books that are very recommended to get me started and I am also going to build a linux machine for me at work. Not to mention I have 4 PCs here at home :)
Wish me luck!

---

### Post by zanglang on 2007-03-06
Ok, let's see:

1. How big does each partition need to be? That depends... will you be storing music and video files? If you do, do you need to share them between both Linux and Windows? (You said you liked iTunes so I guess you might be listening to mp3s on both.) If you do, I'd recommend a large FAT partition just for that (~30GB), 1 swap (512mb or more, depending on your RAM), and the rest split between Windows and Ubuntu. Otherwise split in proportion depending on how much you'll use each OS. (e.g. 70% Windows ~ 40GB, 30% ~ 20GB) Note that on Windows there's no initial support for the EXT3 file system. There's some open source drivers, but last time I tried they were pretty buggy. So, with NTFS-3g Linux will work fine with Windows, but not vice versa, take that into account.

2. Try installing NetworkManager ('knetworkmanager' for KDE), it handled wireless quite well.

3. Not sure about the flash drive... but works perfectly fine here. Might want to upgrade to Edgy (or a little while more, Feisty)? ;)

4. Seems like there really isn't much love for SiS video cards... Well, keep an eye on the forums I guess, there might be fixes and suggestions for improving your situation.

5. And good luck, too. :D

---

