---
title: "Hard Drive Space"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-08
I was trying to copy some music earlier to my desktop Via mp.3 when I did it said there was not enough space so I checked my hard drive space and I came up with this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             3.2G  2.6G  403M  87% /
varrun                121M   96K  121M   1% /var/run
varlock               121M     0  121M   0% /var/lock
udev                  121M   92K  121M   1% /dev
devshm                121M     0  121M   0% /dev/shm
lrm                   121M   34M   87M  29% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             3.9G  309M  3.6G   8% /media/Removable
/dev/sdc1             2.0M  471K  1.5M  24% /media/Removable_

```

Now I have a 40GB Harddrive yet it says here I have only 3.2?

---

### Post by ELF_O8 on 2008-04-08
> **Orcaporka said:**
> 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             3.2G  2.6G  403M  87% /

```

It seems to me that you are using Ubuntu from a memory stick or USB jump drive.
You have only partitioned 3.2 GB of space for Ubuntu so that is all you get for "Filesystem"
Try putting the files on another disk. You can still access them from Ubuntu.

---

### Post by Ieatmacs on 2008-04-08
> **Orcaporka said:**
> I was trying to copy some music earlier to my desktop Via mp.3 when I did it said there was not enough space so I checked my hard drive space and I came up with this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             3.2G  2.6G  403M  87% /
varrun                121M   96K  121M   1% /var/run
varlock               121M     0  121M   0% /var/lock
udev                  121M   92K  121M   1% /dev
devshm                121M     0  121M   0% /dev/shm
lrm                   121M   34M   87M  29% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             3.9G  309M  3.6G   8% /media/Removable
/dev/sdc1             2.0M  471K  1.5M  24% /media/Removable_

```

Now I have a 40GB Harddrive yet it says here I have only 3.2?

Sounds like that is your partition size? Umm, download a software called unetbootin and use it to install 'gparted' then repartition your hard drive.

---

### Post by Orcaporka on 2008-04-08
> **ELF_O8 said:**
> It seems to me that you are on partition 4 of your harddrive.
You have only partitioned 3.2 GB of space for Ubuntu so that is all you get for "Filesystem"
Try putting the files on another disk partition. You can still access them from Ubuntu.


Is there anyway to increase the size of the partition for Ubuntu?

---

### Post by Orcaporka on 2008-04-08
> **Ieatmacs said:**
> Sounds like that is your partition size? Umm, download a software called unetbootin and use it to install 'gparted' then repartition your hard drive.

I just downloaded unetbootin but I was told I dont have a program that allowes the automatic installation of it?

---

### Post by ELF_O8 on 2008-04-08
[quote=ieatmacs]Sounds like that is your partition size? Umm, download a software called unetbootin and use it to install 'gparted' then repartition your hard drive.[/quote]

I think that if you repartition your drive you will erase your OS.

---

### Post by fela on 2008-04-08
> **ELF_O8 said:**
> I think that if you repartition your drive you will erase your OS.

if you repartition, you clobber filesystem. As in: LOSE ALL DATA, not just OS.

---

### Post by SlappyPappy on 2008-04-08
It seems odd that it's not sda1 for your install.

What you can do is boot from the LiveCD, go /system/administration/partition editor and then you can see what's available for that partition in the way of unused space.

I did that when I cloned my hard drive to a larger drive and then used gparted to resize the partition to its full size. Worked great.

Good luck.

---

### Post by Orcaporka on 2008-04-08
> **fela said:**
> if you repartition, you clobber filesystem. As in: LOSE ALL DATA, not just OS.

does this mean I have to pretty much wipe? because I cant survive on just 3.2GB

---

### Post by ELF_O8 on 2008-04-08
> **Orcaporka said:**
> does this mean I have to pretty much wipe? because I cant survive on just 3.2GB

Like I said before, Ubuntu can read the mp3's from another hard drive or disk. You 
don't need to wipe it. They don't need to be in the 'Filesystem'

---

### Post by Orcaporka on 2008-04-08
> **ELF_O8 said:**
> Like I said before, Ubuntu can read the mp3's from another hard drive or disk. You 
don't need to wipe it. They don't need to be in the 'Filesystem'

I get that but Ill only have a small amount of space for anything else, like documents, picutres etc. i create on ubuntu?

---

### Post by fela on 2008-04-09
I don't think you can make a partition larger without wiping it, so my best approach if you want a bigger installation partition would be to backup your files and reinstall, this time making a bigger partition for the install.

---

### Post by ELF_O8 on 2008-04-09
you could always mount the other partitions inside your folder.
set the mount point as /dev/home/user/Stuff/ or something like that.
that way it is easily accesible

---

