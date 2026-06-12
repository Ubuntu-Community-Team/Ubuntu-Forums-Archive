---
title: "Hard drive permission to write problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by mlucian72 on 2007-06-12
I have UBUNTU installed on a SATA drive, and I have another IDE drive (200GB) that I just formated with GParted.
 I've created one partition on the entire drive formated to ext3.
 I can mount and unmount the drive as many times as I please, however the drive is owned by "root" and I can't change permissions for it.
 Also there is a folder called "Lost+Found" om the drive, what is it?
 I've tried to use sudo commands to change ownership and permissions...no luck!
 I've tried to use "right click" on the drive and then "Properties", and so on...no luck!
 How can I do this?I want to create a directory on the drive and save data on it, but I don't know how to do it.
 Does really all this stuff have to be typed in in "terminal" window, or is there a shortcut or easier way?
 
  Thank's for reading!

---

### Post by ryanVickers on 2007-06-12
Have you tried various disk tools that can be found in the Add/Remove - some of them seal with these prblems.

As for this:
> Also there is a folder called "Lost+Found" om the drive, what is it?
It is automatically created on every linux device and has no purpose and no one can ever accessit as far as I'm conserned.  So if you were worried, don't, this is a normal thing, (but as far as I know, useless).

---

### Post by Inxsible on 2007-06-12
Did you try changing the permissions on the mount point ?
```
sudo chown -R <your username>:<your group> <path to mount point>
```

---

### Post by mlucian72 on 2007-06-12
Thak's for the quick reply! The Lost+Found folder is quite big! It's like 3GB. Is this normal?
 As for the aplications in the ADD/Remove menu...do you have any sugestions?
 I am very new to UBUNTU but I am willing to learn! Thats why I scrapped windows XP all together, and I run Ubuntu only on my system!
 You guys are great ! Thanks for all the support you give us !

---

### Post by mlucian72 on 2007-06-12
I did...and then I unmounted and mounted again..."root" is still the owner...and still can't write:(

---

### Post by ryanVickers on 2007-06-12
> Thak's for the quick reply! The Lost+Found folder is quite big! It's like 3GB. Is this normal?
um, no.  It's usually empty I think!  But once again, I have no idea what it is, it's just there - it's probably system stuff, or maybe transfer falures, etc.  No idea

As for the programs, "Storage Device Manager" is pretty good, especially with some/very little knowledge(but some) of the fstab and mtab files.  Ok on it's own too I guess.

Also, I don't know the name, but the Disk Manager that 6.06 installer came with was nice, but I haven't been able to find it since!

---

### Post by mlucian72 on 2007-06-12
I forgot to mention...I'm running Ubuntu 7.04 32 bit version

---

### Post by ryanVickers on 2007-06-12
I have a xp partition, and the owner is root, but I have full read/write to it, so I don't know - try going gksudo nautilus and look under permissions of the mount point folder.  See if everything, or at least you and/or root can read and write!  Once again, the Storage Device Manager is quite nice!  You can tell it to not mount everything as /media/disk-#! :p

---

### Post by mlucian72 on 2007-06-12
how do I go about gksudo nautilus?

---

### Post by ryanVickers on 2007-06-12
open a terminal and type it in. :)

It just runs the file browser as root.  The "gk" part is so that if you want, you don't have to keep the terminal open!  Hooray!

---

### Post by mlucian72 on 2007-06-12
I've used "Storage device manager", still can't create a folder on the drive! Why does it have to be so complicated? :(

---

### Post by mlucian72 on 2007-06-12
This is the mount options that are on the drive now:
 rw nosuid nodev noexec data = ordered

 Is there a way I can chage these ?

---

### Post by Dev0205 on 2007-06-12
Mlucian72,

One of the first main issues I had when I came over to Ubuntu was with Hard Drive Partitions/Permissions. I can't tell you how many hours I spent trying sudo this sudo that, editing files...everything. I know there is a great deal of things you can or may have tried..but if it comes down to it, reinstalling is always an option. That's what I finally ended up doing and like by some Linux magic, the install assigned the correct permissions and such. I know it's not the most fun thing to do but it did work for me.

Cheers,
Dev

---

