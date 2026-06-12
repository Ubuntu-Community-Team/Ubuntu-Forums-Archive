---
title: "OneTouch III"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-03-11
Heya!

I'm having a problem here... Got a nice Maxtor OneTouch III, 300 Gb drive, it does show up in device manager (why call it that, there's not much to manage from there) as an unknown device, with an oxford semiconductor chip... Would like to copy my files back to my pc... 
Anybody got ideas?
thx.

---

### Post by diatribe on 2007-03-11
when you plug it in does it mount the drive?  ie appear on your desktop or under places in the gnome menu?

---

### Post by Ashrael on 2007-03-11
nope...

---

### Post by diatribe on 2007-03-11
when you plug it in you will have to manually mount it then , if it is your only external drive the command should be

sudo mount /dev/sda1 /media/mount_point

---

### Post by Ashrael on 2007-03-11
tried that, but it comes back: mount point does not exist...
so it's still not showing...
i seem to be the only one with this problem, drive is alright, tried it on a windows machine ....no probs....
?????

---

### Post by diatribe on 2007-03-11
ok where I had mount_point, that would be the mountpoint
say you want it to mount to /media/music, you would go to a console and type:

sudo mkdir /media/music

then type:

sudo mount /dev/sda1 /media/music

---

### Post by Ashrael on 2007-03-11
yeah, got that, but it's a bit different, sda is my sata drive..and i think it it should be something with usb? maybe it's got something to do with fstab or mtab???

---

### Post by diatribe on 2007-03-11
well, you could check fstab to see if it is listed, if it is all you would have to do is type 

sudo mount /dev/whatever

and it should mount it automatically to its mount point.

you could also try 

sudo mount -a

---

### Post by Ashrael on 2007-03-11
it's not listed in fstab... tried both (with my names..) both not work.... I'll attach some (3) screenshots of device manager... maybe you see something...thanx for your help mate!

ashrael

---

