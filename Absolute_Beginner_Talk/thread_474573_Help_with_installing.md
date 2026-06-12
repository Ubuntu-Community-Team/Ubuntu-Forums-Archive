---
title: "Help with installing"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by cliveuk on 2007-06-15
hi all
i have windows vista installed on my pc but i want to try ubuntu after using the live CD i dont want to risk messing up windows so im trying to install it to an old harddrive.
to stop it seeing the other drives i disconnected them and left only the formatted drive connected i booted from the live CD but it will not see the harddrive ive tried formatting in NTFS and FAT32???

---

### Post by AAM on 2007-06-15
I presume that you are trying the install routine on the LiveCD. Does the GParted (the partition manager) see a disk ("hda?")?

---

### Post by cliveuk on 2007-06-15
yes im trying to install using the live cd.

it shows all the disc details fine but i cannot access it at all to partition it or anything.
soon as it goes to create the partition it just throws up an error

---

### Post by AAM on 2007-06-15
I don't understand what's happening. I would suggest that you attach all your drives and then run the program to the same point and choose the 'old' HDD based on its size and then format. You need to do this because you have to write GRUB onto the Master Boot record, otherwise you won't be able to see it. Whatever bug is causing a problem in GParted might then be gone also.

---

### Post by antoz on 2007-06-15
You most likely have to unmount it before you can change anything.

---

### Post by cliveuk on 2007-06-15
> **AAM said:**
> I don't understand what's happening. I would suggest that you attach all your drives and then run the program to the same point and choose the 'old' HDD based on its size and then format. You need to do this because you have to write GRUB onto the Master Boot record, otherwise you won't be able to see it. Whatever bug is causing a problem in GParted might then be gone also.

ok just done that and its still not availible, the 2 main sata drives are but the ide drive isnt.

in GParted the partion and filespace show as unallocated for /dev/hda
if i try to set a disklabel i get an error saying "error while setting new disklabel"
if i right click on the unallocated space all options other than new and information are ghosted out

---

### Post by cliveuk on 2007-06-15
anyone?

---

### Post by antoz on 2007-06-16
Well if you right click just select new and create your partitions. You need at least 2 one for your install format "EXT3" and one for swap format "SWAP" this one should be about 1.5 times your RAM.
You could create another one for Home (also ext3) but it is not necessary.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by cliveuk on 2007-06-16
no it does not work, i cannot create any partions on the harddrive :(
oh well looks like i`ll give up on this idea even the partioning software doesnt work right

---

### Post by bigken on 2007-06-16
try the gparted live CD to create your partitions

---

