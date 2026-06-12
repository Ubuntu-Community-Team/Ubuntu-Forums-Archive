---
title: "Need to free up space on / partition"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-04-28
Even after 18 months on Ubuntu, I'm still like a noob.  I've started getting a message in lower right pop up when starting Dapper that says / is 99% full.  Since this was my first Ubuntu install, I've certainly tried out a lot of programs out of curiosity because I was new to open source programs.

My question is where can I see how much resources different programs are using so I can make decisions about what to drop?  Some of the programs I've got that I might guess are "hogs":  Gimp, Kino, Myth.  My / partition was 5 GB, swap is 1GB (2xram) and rest is /home on a 200GB drive.

Thanks.

---

### Post by taurus on 2007-04-28
From a terminal run,

```
sudo aptitude clean
```
Then, you need to look in /var to see what directory/directories is/are taking up the space.

```
sudo du -h /var
```

---

### Post by mikewhatever on 2007-04-28
I do not know the answer to your question, but have a suggestion. Since your /home partition is rather big, why don't you shrink it a little and allocate the space to the root. You can do it with Gparted when running Ubuntu from the Live CD.

---

### Post by flyingsolo on 2007-04-28
Thanks Taurus--your suggestion shows me the larger files are var/log/mysql (363M) &var/lib/mysql/mythconverg (77M), both of which are related to my trying Myth.  All the other files are much smaller (most less than 1M) but there are _many_ of them.

Maybe mikewhatever's suggestion is best but is it safe?  Can I really stretch the / partition?  Does it not physically reside next to the existing /home partition that has much data (though certainly not full).  Just checking.

---

### Post by Tomosaur on 2007-04-28
> **flyingsolo said:**
> Thanks Taurus--your suggestion shows me the larger files are var/log/mysql (363M) &var/lib/mysql/mythconverg (77M), both of which are related to my trying Myth.  All the other files are much smaller (most less than 1M) but there are _many_ of them.

Maybe mikewhatever's suggestion is best but is it safe?  Can I really stretch the / partition?  Does it not physically reside next to the existing /home partition that has much data (though certainly not full).  Just checking.

Well that depends on how you set up your partitions in the first place :P
If you type:
```

sudo fdisk -l

```
into the terminal and paste the output here, we'll be able to tell you.

---

### Post by flyingsolo on 2007-04-28
OK, here is the fdisk info. (FYI--hda is 1st drive with winXP & hdb is 2nd drive for ubuntu in my dual boot)
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5       14588   117145980    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         637     5116671   83  Linux
/dev/hdb2           24134       24321     1510110    5  Extended
/dev/hdb3             638       24133   188731620   83  Linux
/dev/hdb5           24134       24321     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Thanks

---

### Post by mikewhatever on 2007-04-30
> Maybe mikewhatever's suggestion is best but is it safe? Can I really stretch the / partition? Does it not physically reside next to the existing /home partition that has much data (though certainly not full). Just checking.
Reply With Quote
Obviously the /home partition would have to be next to / to do it. It is relatively safe, but depends on how full is /home is.

---

### Post by Najand on 2007-04-30
Can you run ```
 df 
``` command and copy/paste it here?

---

### Post by Pobega on 2007-04-30
Your best bet is to run 'aptitude search "~i"' and look for programs you don't really use anymore, and purge them from your system (aptitude purge <prog>).

You could also clean out /var/cache/apt/archives/, but I think what Tauras said to do would have done that for you (aptitude clean).

---

