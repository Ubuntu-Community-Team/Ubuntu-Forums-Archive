---
title: "How do I know which partition is which.."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by sc2 on 2007-11-18
I go to Gparted to erase my Ubuntu partition (I'm doing a clean install because of a recent kernel panic) and all I find are:

/dev/sda1  ntfs   HP (label)   boots (flag)
/dev/sda3 ext3 


The other two are busy or they are labeled recovery (which I know I shouldn't delete)


Windows was the first partition on the system, does that mean windows is sda1, and ubuntu is sda3? (sda2 is recovery)


But Ubuntu was on the top of the Grub list, so it booted first..is the one with the "Boots" flag Ubuntu?

Which is which? :confused:

---

### Post by doomster on 2007-11-18
i would say that sda3 is the linux partition, as it is formated in ext3 . the ntfs formated partition must be the windows one:)

---

### Post by terdon on 2007-11-18
Well, ntfs is the windows file system, so the ext3 drive should be ubuntu. The easiest way to tell is to run ```
mount
```

and look for the> dev/sdaX on /

partition number X will be your root partition.

---

### Post by mdpalow on 2007-11-18
I think you got it right. You should also be able to tell which is which by the size of the hard drive shown in your gParted (Partition Editor). Just remember which is which and when you go to install again, stay away from the other partitions when you get to the partition part. If you know sda3 is linux (I agree) then delete the partitions that are under that drive and create new ones.

Remember to leave the other ones alone. :)

Good luck...

---

### Post by sc2 on 2007-11-18
> **mdpalow said:**
> I think you got it right. You should also be able to tell which is which by the size of the hard drive shown in your gParted (Partition Editor). Just remember which is which and when you go to install again, stay away from the other partitions when you get to the partition part. If you know sda3 is linux (I agree) then delete the partitions that are under that drive and create new ones.

Remember to leave the other ones alone. :)

Good luck...


I made them both the same size because I have a 320gb internal hard drive. :lolflag:

So I just click on sda3 and hit delete? Or is it more complicated than that? (I don't feel like breaking the computer again, I sounded like a women with PMS and my family sorta got scared, lol)

---

### Post by Pumalite on 2007-11-18
What happened to:
sudo fdisk -lu

---

### Post by sc2 on 2007-11-18
> **Pumalite said:**
> What happened to:
sudo fdisk -lu

What do you mean 'what happened to it'? 

I'm not on the live cd right now, I'll get back to you after my starcraft session. :D

---

