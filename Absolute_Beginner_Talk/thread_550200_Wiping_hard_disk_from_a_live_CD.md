---
title: "Wiping hard disk from a live CD"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Typeface on 2007-09-13
One of my windows computers has messed up seriously, luckly throught using a Live Cd ive benn able to save all my important files. However reformationg from windows doesn't seem to be an option as ive ended up with three copies of windows running on top of each other. Is it possible to compleatly wipe the hard disk with a live CD so i can have a fresh start?

---

### Post by rolnics on 2007-09-13
Wouldn't it be easier to format from a windows setup disk?

The only program that might help on the live cd is gparted, but some of the other experients might know a better solution

---

### Post by CaptainInsaneO on 2007-09-13
Sure is. Boot the livecd and under Applications>System Tools (I believe) you will find partition manager. It may be under the System menu instead, I'm not completely sure but it's there. You can wipe out everything from there.

---

### Post by Nulifier on 2007-09-13
if you boot up a live Cd there should be a program called Gparted and you cna simply delete all the partitions or make a partition scheme to install ubuntu and XP side by side (I know that was a shameless plug).

I do belive that XP and vista both have methods of creating partitions (albeit not as great as ubuntu) but Gparted should solve your problems.

Then you should be able to create a partition in the windows installer bu tif you can't (I dont remember I haven't installed in a while) then just make a ntfs (assuming XP or vista) partition) whatever size.

good luck.

Oh and make sure you have all your data bakced up and off the HD before you begin as deleteing partitions tends to erase data...

---

### Post by LowSky on 2007-09-13
> **Typeface said:**
> However reformationg from windows doesn't seem to be an option as ive ended up with three copies of windows running on top of each other.   

You have 3 partitions of Windows?

Or have you just been Repairing Windows?

Because when ever I do a Fresh install it wipes my hard drive

---

### Post by Typeface on 2007-09-13
Is there any way i can delte only specific files with a live CD? im encountering problems at the moment as i need root access to change the files?

In awnser to low sky im not quite sure i wasnt the one re installing windows however its ended up that we have three copies of windows on the same disc withowt partition

---

### Post by CaptainInsaneO on 2007-09-13
You can access the hdd that your installs are on. To get root access you just need to sudo a nautilus window (don't do this all the time and be very careful so you don't mess something up, unless you don't care. :))

```
sudo nautilus
```

---

