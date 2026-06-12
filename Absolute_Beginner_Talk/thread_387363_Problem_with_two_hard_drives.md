---
title: "Problem with two hard drives"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by PhosPhoton on 2007-03-18
I have an interesting problem. When I first installed Ubuntu, I used a 3.2 GB just for system files and stuff. Now I decided I'm going to need a lot more than that so I stuck in a 40 GB HDD as slave for good measure. I configured BIOS settings and it all looked fine, but when I went into Ubuntu I couldn't find it.

---

### Post by AtrejuT on 2007-03-18
how did you try to find it?
what does
```

sudo fdisk -l

```
give?

---

### Post by oilchangeguy on 2007-03-18
have you gone to, system, admin, disks? it should show up there.

---

### Post by McMarley on 2007-03-18
your programs will be saved on to the master disk as a default.
if nothing else works, but the second disc as master, then it'll have to work, but its a risk to take...

PS: excuse the indiscretion, but how can you survive with a total of only ~45 GB?
      I have 580 GB and i have plowed though them in no time!

---

### Post by oilchangeguy on 2007-03-18
also what did you do in the bios? you should not have to make any changes just because you add another hard drive. just make sure you set the jumper on the drive to slave. and you plug it in to the same ide cable the master drive is on.

---

### Post by Vandorius on 2007-03-18
This is what i get: 

vandorius@vandorius-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9557    76766571   83  Linux
/dev/hda2            9558        9964     3269227+   5  Extended
/dev/hda5            9558        9964     3269196   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2433    19543041    7  HPFS/NTFS

Under system...admin i dont have any disk button, and i still cant see the contents of this 20 GB disk.

---

### Post by Vandorius on 2007-03-18
BUMP

I wuld really like to see the contents of the disk. So anyone that knows how welcome to teach a noob.

---

### Post by oilchangeguy on 2007-03-18
go to system, admin, disks, partitions, browse.

---

### Post by Vandorius on 2007-03-18
Under system, admin i dont have a disks button!

---

### Post by McMarley on 2007-03-18
BUMP

that hurts.
i know that problem. i don t have printers...
and still havent found a solution

---

### Post by Vandorius on 2007-03-18
So the question is next..... How to see the second disk if i DONT have the disks button under system administration?

---

### Post by PhosPhoton on 2007-03-19
darn! I need this hard drive working! It has important stuff on it. I'm thinking of getting a couple of 200GB (one for my Windows PC as well) later on, but right now I'm broke, so I'm going to have to stick with 40GB for now.

---

### Post by justleen on 2007-03-19
> **Vandorius said:**
> This is what i get: 

vandorius@vandorius-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9557    76766571   83  Linux
/dev/hda2            9558        9964     3269227+   5  Extended
/dev/hda5            9558        9964     3269196   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2433    19543041    7  HPFS/NTFS

Under system...admin i dont have any disk button, and i still cant see the contents of this 20 GB disk.

looking at this output.. you dont have a 40gb disk?
i can see you have a pratitioned 80 gb drive, on which you have linux
and a 20 gb ntfs drive..
where is your 3.2 gb??

It would be intresting to know what your did in the BIOS.. Does is show up in there as an available drive?

---

### Post by PhosPhoton on 2007-03-19
That was Vandorius' post with the 80GB HDD, not mine.

All I did in the BIOS was check whether the Hard Drive was there. Sure enough it was, but in linux it appears to be 'disabled'

---

### Post by justleen on 2007-03-19
> **PhosPhoton said:**
> That was Vandorius' post with the 80GB HDD, not mine.

All I did in the BIOS was check whether the Hard Drive was there. Sure enough it was, but in linux it appears to be 'disabled'

Right.. My bad :-#

Can you post your output of 
```

sudo fdisk -l
sudo cat /etc/fstab 

```

---

### Post by bobpur on 2007-03-19
I've had these drive recognition problems before, too.
Is the 40 gb drive formatted to something that linux will recognize? For instance, Ubuntu won't "see" my WinXP drive (NTFS) but it will "see" the same drive formatted to FAT32.
                                                
                                                      Good Luck!

---

### Post by bobpur on 2007-03-19
Oh yeah, if the drives are from two different manufacturers, you might have to play with the jumper settings. Instead of "master/slave" try "cable select/slave" or "master/cable select."

---

