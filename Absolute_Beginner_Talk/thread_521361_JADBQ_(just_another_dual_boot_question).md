---
title: "JADBQ (just another dual boot question)"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Koz-D on 2007-08-09
Hi all,

I've searched the forum, but can't find the answer to my problem;

I can't get a dual boot XP-pro/Ubuntu on my hp nc6000 (laptop).


I've followed the instructions on the documentation site, but I don't even get the choices I should get during install.
My laptop has a 40GB HDD, which has only 1 ntfs partition with windows XP pro installed along with numerous programs I use. Since it's around 50% free, I wanted to instal Ubuntu (7.04) on the remaining space.
I use the Desktop Installation CD (live CD).
During install you'll get to the point of partitioning, here's where my first problem starts: I only get 2 options; 1) Guided - use entire disk and 2) Manual. According to the documentation, I'm missing one option (guided - resize and use freed space).
Since I know a thing or two about partitioning a hdd, I choose manual, where my second problem occurs: I can only choose the partition which is already on the hdd and change its file-system (can NOT add or resize).

Ubuntu recognises the drive as being 'SCSI1 (0,0,0) (sda) - 40.0 GB ATA', with the following partition parameters; drive: '/dev/sda1', system: 'ntfs', mount point: '/media/sda1', size: '39999 MB', used: 'unknown'.

So what do I do now? (plz dnt advise me to use 3rd party partitioners, I had real troubles with those, like losing 0.7 terabytes of data on my server, of which I had only a partial backup (I don't know of 700+ GB of backup units :p))

---

### Post by Inxsible on 2007-08-09
Maybe, you should go into the Windows side and resize the partition and leave some unallocated space and then put in the LiveCD and use the unallocated space to install Ubuntu.

Or you could use GParted(its on the LiveCD) to first partition the drive the way you want it and then go ahead and install. Keep in mind that if you use this option you will first have to unmount the drive. Only then will you be able to change partitions on it.

---

### Post by Koz-D on 2007-08-09
Can't seem to resize the partition in XP, and like I mentioned, I don't trust 3rd party partition wizards.

Does this mean I'm out of options other than wiping disk and start over? (just as my XP install is stable, well as stable as XP gets anywayz)

Why doesn't the regular option 'Guide - resize and use..' appear when the native partition manager starts up?


*Note; GParted is not on the CD I got

---

### Post by Inxsible on 2007-08-09
> **Koz-D said:**
> Can't seem to resize the partition in XP, and like I mentioned, I don't trust 3rd party partition wizards.

Does this mean I'm out of options other than wiping disk and start over? (just as my XP install is stable, well as stable as XP gets anywayz)

Why doesn't the regular option 'Guide - resize and use..' appear when the native partition manager starts up?


*[COLOR=Red]Note; GParted is not on the CD I got[/COLOR]
  It is...as long as you got the desktop version of Ubuntu installation CD. Have you looked for it under System-->Administration-->GParted  ?

and you can use the manual option and then create the partitions

---

### Post by Dr Small on 2007-08-09
If it isn't on the cd, you can always download it real fast from the repositories with 'sudo apt-get install gparted'

Dr Small

---

### Post by Koz-D on 2007-08-09
Ah, I see, so it should be on your *system* when live CD is actually *running*? (opposed to *on* the CD when exploring it)...


...and no I can *not* use manual partition creation, read my initial post '....where my second problem occurs: I can only choose the partition which is already on the hdd and change its file-system (can NOT add or resize)'


@Dr. Small; I actually can't, network isn't working when running live CD (but I have more PC's, so I should be able to get it eventually  ;) )

---

### Post by Koz-D on 2007-08-09
...found GParted, but it can't repartition my drive for some reason (outputs an empty error file).

---

