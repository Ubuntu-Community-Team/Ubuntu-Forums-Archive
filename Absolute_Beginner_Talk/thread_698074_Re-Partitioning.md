---
title: "Re-Partitioning"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by zyvx on 2008-02-15
Alright, I have a 120GB dual-boot (Vista/Ubuntu 7.10) laptop with 5 partitions and I really want to streamline them as they are a mess right now. I think i have narrowed down how i want to do it but there are some roadblocks and i don't know how to get around all of them.
I did fdisk and this is what came out

```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c57afcc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         649     5212995    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            1286       14557  106603 520    7  HPFS/NTFS
/dev/hda3             650        1250     4827532+  83  Linux
/dev/hda4            1251        1285      281137+   5  Extended
/dev/hda5            1251        1285      281106   82  Linux swap / Solaris

Partition table entries are not in disk order

```

As you can see it's a mess. As of now this is my allocation plan:

10GB Ubuntu
10GB Vista
2 GB Swap
98GB Shared

First off, is that enough space for the OS'? And what file system should i use for the shared? I believe Vista will be NTFS while Ubuntu and the swap will be ext3 but i have no idea on the shared,and i do want to be able to utilize it by both. 

Next, one of the partitions is a recovery drive for windows and while i could leave it i don't see a point for having a separate drive and I would rather have it share the vista partition to save space. I also have a crap-ton of files on the 100GB partition (mostly vista) and i really don't want to lose all of it. Any info on slimming down vista would be amazing too because even though I just started w/ linux, i like it alot and I would like to make it my primary OS, but I still am going to need all the windows capability. I heard GParted was an awesome utility that makes it alot easier but i have never used it so yea... Any info/advice would be greatly appreciated.

---

### Post by agim on 2008-02-15
I have heard 10GB is not enough for Vista. I was told 20GB minimum and 30GB to be safe and install programs.
This said, I hope you go to Ubuntu full time soon. I did myself recently and have found no reason to regret it. And freeing up all of those system resources that were being held onto by Vista has been great.

Edit: Another great thing about Ubuntu, you can read and write to your Windows side. Double check on the safety of this procedure... I have done it in the past without issue, but would hate to give bad advice. Ubuntu is much more efficient with your resources and needs less space, especially with the ntfs write capability.

---

### Post by sandysandy on 2008-02-15
as brought out by agim, Ubuntu Gutsy 7.10 onwards you can both read and write to NTFS. That means once u log into Ubuntu you can access the Windows partitions also for reading and writing.

i am using a separate NTFS partition myself for common use between windows and Ubuntu 7.10.

u have rightly said that ubuntu&#347; partition on which u install the OS will be ext3. 

Gparted is good.

regards

---

### Post by zyvx on 2008-02-15
That's what i was afraid of, so i assume 10GB is enough for ubuntu? I hadn't had problems yet but i read that ubuntu cant actually write  to NTFS but it can read it but if it can do everything then hotdamn! 

So I guess an allocation revision is in order:

30GB Vista NTFS
10GB Ubuntu ext3
2GB Swap ext3
78GB Shared NTFS

Safe enough?

As wonderful as ubuntu has been so far I still like the familiarity of windows and i'm going to need it if i get an IT job. Plus there are programs for windows that are essential to me that are not linux available (i.e. BitComet)

> **sandysandy said:**
> as brought out by agim, Ubuntu Gutsy 7.10 onwards you can both read and write to NTFS. That means once u log into Ubuntu you can access the Windows partitions also for reading and writing.
i am using a separate NTFS partition myself for common use between windows and Ubuntu 7.10.
regards

So i can read/write? tits. How is your setup?

---

### Post by oedha on 2008-02-15
to write on NTFS....you just need to install NTFS configuration tool
easy way  :==> applications - Add/Remove
seacrh for ntfs in all avaliable applications
10gig is too big (for me) for ubuntu....i will be confuse to fill it :)
i just use 6.5gig

---

### Post by agim on 2008-02-15
I didn't need to use any tool to write to NTFS/Windows. I just wrote to it, I believe it is default in 7.10.

---

### Post by zyvx on 2008-02-15
I have not had problems before but i went ahead and installed the NTFSconfig tool. I just  used 10GB because i saw it in another post. Does it really take up only that much space? I figured i just didn't have alot installed because i have it on 4.5GB right now and i have only used 3.3GB. That's insane that I have it running alright on 3.3GB and windows needs around 30GB. Interesting

---

### Post by sandysandy on 2008-02-16
> **zyvx said:**
> That's what i was afraid of, so i assume 10GB is enough for ubuntu? I hadn't had problems yet but i read that ubuntu cant actually write  to NTFS but it can read it but if it can do everything then hotdamn! 

So I guess an allocation revision is in order:

30GB Vista NTFS
10GB Ubuntu ext3
2GB Swap ext3
78GB Shared NTFS

Safe enough?

As wonderful as ubuntu has been so far I still like the familiarity of windows and i'm going to need it if i get an IT job. Plus there are programs for windows that are essential to me that are not linux available (i.e. BitComet)



So i can read/write? tits. How is your setup?

i am using 20 gb for win xp and 15 gb as common partition (NTFS). rest i am using with different distros (currently six linux distros) installed. i am using ubuntu 7.10 with 5gb partition and it works fine (initially it was about 3gb and i had to use gparted to expand it).

regards

---

### Post by kwacka on 2008-02-16
> **zyvx said:**
> As wonderful as ubuntu has been so far I still like the familiarity of windows and i'm going to need it if i get an IT job. Plus there are programs for windows that are essential to me that are not linux available (i.e. BitComet)?

Sorry to go off topic - but what is special about BitComet? What other applications do you use that are essential? 

Apart from new games & specific professional applications you can find equivalents.

BTW My laptop has Ubuntu in a 7.5GB partition, uses 4.6 GB. Desktop has an 8.77GB partition,using 6.1 GB.

---

### Post by zyvx on 2008-02-16
I love the way it handles torrents and I am used to it. Can't really think of any, lol. If i get the IT job then I will be using those specific professional programs. I'm really just trying to have all bases covered. I would have OSX if I could.

---

