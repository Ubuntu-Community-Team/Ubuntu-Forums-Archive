---
title: "Kingston Datatraveler problem"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by rex66 on 2008-03-17
Hi folks,

  I am trying to use a Kingston Datatraveler USB 2.0 flash drive on my pc running gutsy with all current updates. It recognizes it fine but when I try to copy anything to it I get a "You do not have permissions to write to this folder." error message. I've tried to change the permissions in the property tab but it tells me it is a read only disk. Any suggestions? One other piece of info, it works fine on windows so I'm quite sure the flash drive is okay.

Thanks

Rex

---

### Post by PmDematagoda on 2008-03-17
What file system does the flash drive use?

---

### Post by rex66 on 2008-03-17
I've just been at their website but I can't find the file system. I would assume FAT32 but I'm not sure. Sorry, I'll keep looking.

---

### Post by kleo skywalker on 2008-03-17
I had a similar problem once, it was solved [here]("http://ubuntuforums.org/showthread.php?t=528703").

---

### Post by Arthur Archnix on 2008-03-17
No need to visit the website. 
```
lsusb
```
Shows whether or not its connected.
```
sudo fdisk -l
```
Will give you some info about the filesystem. If you plug it in, then do
```
sudo dmesg | tail --lines=20 | grep Write
```
that will show you if "write protect" mode is enabled.

---

### Post by rex66 on 2008-03-17
Thanks pm, kleo and arthur.....before I got back and read your posts I had popped the usb drive into the windows PC to get the filesystem... it was FAT....while I had it in there I reformatted it and now it seems to work fine in ubuntu.....next time I will try your way! I had searched and read through many posts but couldn't find one specific. Thanks again as always!

---

