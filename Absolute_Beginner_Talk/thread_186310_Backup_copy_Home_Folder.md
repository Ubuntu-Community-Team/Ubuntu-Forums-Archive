---
title: "Backup copy Home Folder?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-06-01
I would like to make a backup of my home folder before I upgrade to Dapper.

Last time I tried to do this (in gnome) it seamed like not all files were copied.

Is there a command I can type into the terminal to copy my Home folder to:
/media/sda1

?

Thanks

---

### Post by Trab on 2006-06-01
cp /home/* /media/sda1/
that should work.
what you should REALLY do (after upgrading to dapper, or while if ur doing a clean install is a perfect time) is have your /home directory on a seperate partion. ive had the same /home directory for almost 2 years throughout 4 different linux flavors, and various reinstallations. (thought you will probably need to clean that partion out yourself a bit, i cleaned mine out when i got my new HDD and upgraded to breezy)
cheers
-TJ

---

### Post by catlett on 2006-06-01
If you use the -r option (recursive) it will copy all subfolders etc.
```
cp -r  /home/you /media/sda1
```

---

### Post by aktiwers on 2006-06-01
Thanks a lot!

I was thinking about making a home partition, but there are a few things im not sure about.

If I do a fresh install, how do I tell ubuntu that my /home partition is the one its going to use as home? Wont it just make a Home folder as usual anyways?

Also how big should I make this Home folder?

Thanks a lot! Im copying it now! :)

---

### Post by catlett on 2006-06-01
If you use the Dapper live cd it will have a graphical partitioning area where you will have drop down boxes with options of /, home, swap and some other more obscure ones if you really want security with everything on seperate partitions boot, var etc
If you are using the text installer like in breezy (but for Dapper of course) you have to choose that partition. It will send you to another screen. It will ask you what filesystem i.e ext2, ext3, fat32 etc. It will also ask you a mount point. Enter /home. Then choose done with this partition. You need to pick the partition for swap and go through this. Choose filesystem type (swap) choose mount point (swap, actually I think it is automatic when you choose swap as filesystem) and of course choose the partition for root. Filesystem ext3 and mount point ( / )

---

