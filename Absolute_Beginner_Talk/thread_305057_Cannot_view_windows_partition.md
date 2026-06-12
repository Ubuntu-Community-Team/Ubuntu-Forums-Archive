---
title: "Cannot view windows partition"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2006-11-22
When I try to browse my windows partition i get the error that the drive is unmounted. How do I fix this so I can pull files from my windows partition and use them in kubuntu.

---

### Post by taurus on 2006-11-22
You need to mount it first before you can access it...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by BarfBag on 2006-11-22
Copy and paste the first command into the terminal (Applications > Accessories > Terminal) and press enter, then do the same with the second.  If you want it to automatically mount it at boot, PM me.  That's a little more tricky.

> mkdir /media/windows/

> sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by richiewrt on 2006-11-22
ok, maybe i didnt provide enough information.  i can see the drive in konqueror (along with my linux partition and my disk drive) but when i try to explore it i get an error message "Could not mount device. The reported error was:
mount: can't find /dev/hdal in /ect/fstab or /ect/mtab
 when i tried to copy the fstab file, it says it doesnt exist.
also when i tried the fdisk thing from the link when i got to the the command 
sudo nano /etc/fstab

my screen comes up completly different from what the site shows it just shows down at the bottom [new file] and a bunch of different commands
 pleae help Im new to linux and all this is like greek to me so far.

---

