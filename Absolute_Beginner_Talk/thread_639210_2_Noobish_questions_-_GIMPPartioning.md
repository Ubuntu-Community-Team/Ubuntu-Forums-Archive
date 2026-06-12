---
title: "2 Noobish questions - GIMP/Partioning"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-12-12
Ok first very noobish question is how do I unlock my HDD so I can edit the partitions? I want to combine /dev/sda3 with sda1 and I don't want to erase anything. If that's not possible how can I make it so I can write files to sda3?


Next Question,


How do you install painbrushes in GIMP I have some downloaded ,but am having trouble figuring out where the GIMP folder even is located. 

Thanks

---

### Post by t0p on 2007-12-12
> **449 said:**
> Ok first very noobish question is how do I unlock my HDD so I can edit the partitions? I want to combine /dev/sda3 with sda1 and I don't want to erase anything. If that's not possible how can I make it so I can write files to sda3?


You can only mess with partitions that are unmounted.  The best thing to do is to run a Live CD.  The Gutsy Live CD has a partition editor on it.

---

### Post by 449 on 2007-12-12
> **t0p said:**
> You can only mess with partitions that are unmounted.  The best thing to do is to run a Live CD.  The Gutsy Live CD has a partition editor on it.

So can I at least make it so I can put files on it?

---

### Post by t0p on 2007-12-12
Whether you'll be able to write to the partition depends on what sort of partition it is.  I've got a dual-boot - I have an Ubuntu partition, /dev/sda2, which is ext3; and an XP partition, /dev/sda1, which is NTFS.  Back when I was running Feisty, I was able to write to the NTFS partition, but I see to remember that I had to install the package ntfs-config first.  Now that I'm running Gutsy, /dev/sda1 has been writable and auto-mounted from the get-go.

---

### Post by natehall on 2007-12-13
> **449 said:**
> Ok first very noobish question is how do I unlock my HDD so I can edit the partitions? I want to combine /dev/sda3 with sda1 and I don't want to erase anything. If that's not possible how can I make it so I can write files to sda3?


Next Question,


How do you install painbrushes in GIMP I have some downloaded ,but am having trouble figuring out where the GIMP folder even is located. 

ThanksTo find something go to Places>Search for files>look in folder>file system then type it in. I came up with /usr/share/gimp

---

### Post by disturbedite on 2007-12-13
brushes belong in ~/USER/.gimp2.4/brushes.

---

### Post by 449 on 2007-12-14
> **t0p said:**
> You can only mess with partitions that are unmounted.  The best thing to do is to run a Live CD.  The Gutsy Live CD has a partition editor on it.

I know you already answered my question  ,but now I'm leaning towards just keeping the partition and using it for backup/storage. How would I make it accessible to put files on?

---

### Post by diatribe on 2007-12-14
mount it

---

### Post by -MoonDoggie- on 2007-12-14
i'm actually having the same problem. it's not a mounting problem because its already mounted. the problem is that i need root permission to access this partition. this partition is ment to be a share of space between vista and ubuntu. did i just make it the wrong format? it's a ext3 format and named it /media/share, so its sitting on my destop. i just can't get into it to write files to it, in either linux or vista (i know that another driver is needed to write to it from vista though). whats the deal?

---

### Post by Incense on 2007-12-14
If you format the partition as Fat32, then you will have an easy time being able to read and write files to it regardless of the OS, or the permissions. Not the best option, but one that makes my life easier.

BTW: Don't forget to backup any important data before you format any partition. Better to be safe right?

---

### Post by -MoonDoggie- on 2007-12-14
solved my issue. am posting this for the original topic poster just in case his problem was the same as mine.

[http://ubuntuforums.org/showthread.php?t=389479](http://ubuntuforums.org/showthread.php?t=389479)

easy.

---

