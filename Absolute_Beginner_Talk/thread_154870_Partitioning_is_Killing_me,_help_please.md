---
title: "Partitioning is Killing me, help please"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-04
I can not figure out how to get the install partitioning to work, I looked for the (express) erase everything and partition automatically option but didnt see it, or it was labled something i didnt understand.  I keep getting the error, "no mount point is assigned for the reiserFS file system in partition #1 of LVM VG Ubuntu, LV swap_1  
it says if i dont go back to partition menu and assign a mount point it will not be used at all.  I am going by the instructions in the wiki, but anyone have a simpler way to explain to a moron please how to set up the partitions??!!?

---

### Post by drummer on 2006-04-04
When you get to the partitioning page in the installer, just select the "erase entire disk: <name of disk>"
I think that's what it's called, or something *very* similar. Note that that will wipe the whole disk and partition it automatically. It will probably make a larg-ish swap partition and one large root ( / ) partition. Search through the forums for howtos, there are some good ones out there, I just can't remember where exactly atm.

---

### Post by mumushi on 2006-04-04
i think you have forgotten the swap partition. try erasing the entire partition then create a new partition then select automatically partition. I very sure that would work now :)

---

### Post by x5452 on 2006-04-04
I just restarted the installer, went through the language choices ect.. and now it comes to the partition disks menu.  it says the following, 

partitioning method:

Resize IDE1 master, partition #1 (hda) and use freed space
Erase entire disk: IDE master (hda) - 30.0 GB HITACHI_DK23EA-30
Erase entire disk and use LVM: IDE1 Master (hda) -30.0 GB HITACH
Manually edit partition table

<GO BACK>

Please help, I have win xp on there but dont care about it, it can be wept clean, which is the "automatic partition" choice.??

---

### Post by Randomskk on 2006-04-04
Erase entire disk: IDE master (hda) - 30.0 GB HITACHI_DK23EA-30

---

### Post by x5452 on 2006-04-04
and that will erase, format, size and partition the hard drive automatically?  
cool thanks, I tried following the manual steps to set mounts and stuff in the wiki but could only get error messages for my trouble.  thanks

---

### Post by Randomskk on 2006-04-04
Yup, that option will just erase the whole disk and set it up nicely for Ubuntu.

---

