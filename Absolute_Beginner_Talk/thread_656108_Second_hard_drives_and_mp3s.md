---
title: "Second hard drives and mp3s"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Famous Mortimer on 2008-01-02
New installee of Ubuntu, and I was checking my other hard drive (the one with all my mp3s on it). Problem is, it's only showing about two-thirds of them. Don't know why, I've started re-getting some of them but a few will prove difficult. Any idea what's gone on? Any ideas to what I could do to find them again? Judging by the used size of the hard drive, they're still there (somewhere).

---

### Post by LaRoza on 2008-01-02
Do the names of these MP3's begin with a period?

Press Ctrl + h to see them then.

---

### Post by Famous Mortimer on 2008-01-02
If it's that simple, I'll be an extremely happy man. Thanks LaRoza!

(I'm at work at the mo, I'll see if it works when I get home).

---

### Post by Famous Mortimer on 2008-01-02
It's not that, as it turns out. Any other ideas, anyone?

---

### Post by cecure on 2008-01-02
Is it possible that your hard drive has more than one partition and that the files could be on another partition.

You could also run a search, if you havent already.
Goto Places>Search for Files... enter the name of one of the mp3s or folders you are looking for and search. *make sure you have the correct hard drive selected for the search*


If this doesnt help could you tell me if you are looking for them in the gnome filemanager or in Nautilus

Hope this helps

---

### Post by Famous Mortimer on 2008-01-03
No partition on it, and I'm using the Gnome Filemanager. I also added my entire music folder to Rhythmbox and it only detected the same ones that the file manager detected...

No biggie. If they're unable to be read for whatever reason by Ubuntu, then it's not going to take me that long to track them down and replace them. I just need to figure out where the files are so I can delete them.

---

### Post by PreviousN on 2008-01-03
Before you freak out, you may consider this. I think you have a partition that exists but isn't mounted. You can check this...

1. Open up a terminal
2. Type "sudo fdisk -l"

Be very careful with fdisk (especially when sudoing). It reads/writes/modifies the partition table of all the disks. This command (a lowercase L, not an I) tells it to "list the partitions". 

Then, type this in a terminal:
3. "df -h"
This shows you disk usage (and mount points) and the -h means "human readable" (it gives you bytes instead of bits).

Ok, once you have that, compare the two. I think you may have a partition that is not mounted. Here's an example of mine...

previousn@raptop:~$ sudo fdisk -l
[sudo] password for previousn:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7154597

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  83  Linux
/dev/hda4            2433       19457   136753312+   5  Extended
/dev/hda5           19216       19457     1943833+  82  Linux swap / Solaris
/dev/hda6            2433       10334    63472752   83  Linux
/dev/hda7           10335       19215    71336601   83  Linux


## hda1 is my root filesystem. It's mounted as "/"
## hda4 is a logical partition. This allows me to have more than four partitions on one hdd. This is not mounted intentionally. 
## hda5 is my swap space. This is similar to windows' "virtual memory". This doesn't show up in df -h either, but intentionally.
## hda6 some partition (its absent below!!) = which indicates that this partition needs to be added to /etc/fstab
## hda7 some partition.

previousn@raptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G   12G  7.1G  63% /
varrun                442M  228K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   76K  442M   1% /dev
devshm                442M     0  442M   0% /dev/shm
lrm                   442M   33M  409M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hda7              69G   42G   27G  62% /media/hda7

In my "df -h" I don't have a /dev/hda6. This means that the partition exists but isn't mounted. So, you'll need to edit your "/etc/fstab" to put it in. Of course, this is only if the device isn't mounted and the partition exists. We'll cross that river if we need to cross it.


Is it the case that you have a partition that isn't mounted?

---

### Post by Famous Mortimer on 2008-01-03
I don't leave work for another three hours, but I'll give it a try when I get home. Fingers crossed!

---

### Post by Famous Mortimer on 2008-01-03
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54ac2310

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             147G   19G  120G  14% /
varrun                760M   88K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   64K  760M   1% /dev
devshm                760M   12K  760M   1% /dev/shm
lrm                   760M   34M  726M   5% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             233G  204G   30G  88% /media/New Volume



To my untrained eye, that looks about right (the other stuff is from my system hard drive). Actually, it might not be. *scratches head*

---

### Post by hyper_ch on 2008-01-03
Which harddisk is the other stuff on it?

You could rund this command to see what is missing (or what is being found)

```

sudo ls -alR /path/to/other/harddisk > /home/USER/Desktop/mp3.txt

```

Just add the correct path to where you mounted the harddisk and replace USER with your username. That should create a textfile of everything on that harddisk.

---

### Post by Famous Mortimer on 2008-01-03
Weirdly, files are apparently disappearing - opening Rhythmbox this evening and three mp3s have been missing since yesterday at 4:40 pm. Curiouser and curiouser.

---

