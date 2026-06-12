---
title: "change window xp files in linux"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-05
change window xp files in linux
i heard there is no way to change files in window xp in linux is it true it is only able to access not to change

---

### Post by logos34 on 2007-07-05
there is a special driver to enable writing to NTFS

**sudo apt-get install ntfs-3g ntfs-config**

---

### Post by zerobinary on 2007-07-05
but how do i use that program
"/media/dis...vx5.2].mkv" cannot be deleted because it is on a read-only disk.
my device is not external one
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-5.png[/IMG]

---

### Post by logos34 on 2007-07-05
ntfs-config

will brung up a gui box to enable write to internal device, tick the box (or is it grayed out?)

reboot

---

### Post by zerobinary on 2007-07-05
k i will reboot first

---

### Post by zerobinary on 2007-07-05
which one should i choose
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-1.png[/IMG]
and result after it 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-2-1.png[/IMG]
is it because i only have one hdd that u need 2 hdd to make this work

---

### Post by deadlikeoscar on 2007-07-05
Click the box and pick a name such as windows and it will be done. Then reboot. You can then find your drive under /media/windows or whatever you picked.

---

### Post by zerobinary on 2007-07-06
no working i name it 84 should i just uninstall this and use or because i have my usb card reader aka external there
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-3-1.png[/IMG]

---

### Post by zerobinary on 2007-07-06
now i couldn't see my window xp stuff in 84 which i name the drive
now i have remove every external usb drive still no goal
see the file 84 has nothing 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-6.png[/IMG]

---

### Post by logos34 on 2007-07-06
post the output to these commands:

sudo fdisk -l  ('l' as in lowercase L)

mount

cat /etc/fstab

---

### Post by zerobinary on 2007-07-06
sorry i am late about it some how is working lol anyways thx for ur help 
ur help has greatly help me

---

### Post by zerobinary on 2007-07-06
wait an second i got another problem don't leave yet 
Error "I/O error" while copying "/media/witc...vx5.2].mkv".
Would you like to continue?
now i can't mount too 
mount: special device cat does not exist

---

### Post by logos34 on 2007-07-06
why don't you run those commands?  It'll give us an idea of what partitions where dealing with, what is mounting or not and if ntfs-config correctly edited the fstab file.  WHat is the full name of the mount point '/media/witc...'?

What were you trying to do before the error?

---

