---
title: "how do I check my harddisk?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by tompie on 2007-08-27
how do i check if there are any bad sectors on my HD?

---

### Post by estaticd on 2007-08-27
fsck is *the* tool used for checking Linux file systems.  There are others, but it's best to start with that.

Also you may want to give a shot with the manufacture of your hard drive, usually they will have a tool that can do a low-level check of the hard drive and repair errors if needed.

---

### Post by tahitiwibble on 2007-08-27
Hi there.

I'm new too. My system checks itself every 20 boots or so with fsck. It's fantastic.

Perhaps someone might let me know if this is 'normal' for 7.04?

Does one even have to think about doing a manual check under 'normal' circumstances?

---

### Post by david_e on 2007-08-27
Normaly the filesystem status is checked every 30 mounts or so. If you have reasons to think that your root partition could be damaged you can force the fsck at the next boot with the command:

```

sudo touch /forcefsck

```

fsck on non-root partitions can be run "at runtime". Just **[COLOR="Red"]umount [/COLOR]** the partition and run "fsck" on it. (fsck on a mounted partition can seriously damage the filesystem!).

---

### Post by ArtF10 on 2007-08-27
Oh do post how you got that to happen.....every 20 boots.  Do post what you did sir.  That is really great.

---

### Post by david_e on 2007-08-27
> **tahitiwibble said:**
> 
I'm new too. My system checks itself every 20 boots or so with fsck. It's fantastic.

The actual number of mounts before the check is calculated depending on the size of the partiion. This can be adjusted with the use of "tune2fs".

---

### Post by tahitiwibble on 2007-08-27
> **david_e said:**
> The actual number of mounts before the check is calculated depending on the size of the partiion. This can be adjusted with the use of "tune2fs".

Thank you for all that ...... much appreciated.

---

### Post by ArtF10 on 2007-08-27
can you post the command that would have to be entered into a terminal please?

---

### Post by david_e on 2007-08-27
> **ArtF10 said:**
> can you post the command that would have to be entered into a terminal please?
Suppose you want /dev/sda1 to be checked every 30 mounts:
```

sudo tune2fs -c 30 /dev/sda1

```

If you are not sure of the name of your device look at the output of the command:

```

mount

```

to see what is mounted where. 

For other uses of "tune2fs" such as disabling routine  checkes(not recomended!); or using date based check instead of mount based counts look at:

```

man tune2fs

```

---

### Post by tompie on 2007-08-28
Thanks for the help... however, this is what i get in the Terminal:

tom@CompaqPresario:/$ sudo umount /home
umount: /home: device is busy
umount: /home: device is busy
tom@CompaqPresario:/$ umount /home
umount: /home mount disagrees with the fstab
tom@CompaqPresario:/$ 

What did i do wrong?

I also typed:
sudo touch /forcefsck
and did a restart to be able to check my complete HD. After that i restarted my PC. How do i know if my filesystem got checked at start-up? Where can i find this?

rgds,
tom.

---

### Post by david_e on 2007-08-29
You can't umount the /home partition when you are logged in. Moreover it looks like you don't have a different partition for the home directory.

You should type "sudo touch /forcefsck" then reboot. If everything went fine you should see that the hd is being checked at the beginning of the boot sequence. You should see ubuntu exit from the graphical boot and then displaying on a terminal the work of the fsck.

---

### Post by tompie on 2007-08-29
Thanks for the help... however, this is what i get in the Terminal:

tom@CompaqPresario:/$ sudo umount /home
umount: /home: device is busy
umount: /home: device is busy
tom@CompaqPresario:/$ umount /home
umount: /home mount disagrees with the fstab
tom@CompaqPresario:/$

What did i do wrong?

I also typed:
sudo touch /forcefsck
and did a restart to be able to check my complete HD. After that i restarted my PC. How do i know if my filesystem got checked at start-up? Where can i find this?

rgds,
tom.

---

### Post by david_e on 2007-08-29
> **tompie said:**
> Thanks for the help... however, this is what i get in the Terminal:

tom@CompaqPresario:/$ sudo umount /home
umount: /home: device is busy
umount: /home: device is busy
tom@CompaqPresario:/$ umount /home
umount: /home mount disagrees with the fstab
tom@CompaqPresario:/$

What did i do wrong?
As I already said. You don't have an standalone home partition, according to the output you are reporting. So you can't umount it. Moreover you couldn't have umounted it even if it was a separated partition as your home directory is busy since your login.   

> **tompie said:**
> I also typed:
sudo touch /forcefsck
and did a restart to be able to check my complete HD. After that i restarted my PC. How do i know if my filesystem got checked at start-up? Where can i find this?

rgds,
tom.
You should have seen it at the moment of the restart. At the beginning of the boot sequence ubuntu should have entered textual mode and should have shown you the progress of the hd check. In any case ubuntu will check the hd for you every 20-30 boot so you really don't have to force the fsck...

---

### Post by ArtF10 on 2007-08-29
Funny, I had completely forgotten about doing this today morning and suddenly the loading process was interrupted for GUESS WHAT......an automatic disk check!!!!  

It said "Forced Check" after 24 mounts or remoonts...something like that.  But the knowledge of the commands is bound to be useful.

---

### Post by david_e on 2007-08-30
It's not that usefull... Linux partitions like ext3 or raiserfs are really safe. A check every 25 mounts is really enough. :mrgreen:

---

