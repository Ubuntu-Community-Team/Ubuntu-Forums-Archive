---
title: "Hard drive problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by SIlvio77 on 2008-02-01
Hi there,
I'm currently running Gutsy Gibbon and it seems there is a little discrepancy between the volume mentionned and the actual volume of one of my hard drives. 
When I go to the properties of the drive it tells me that there are a total of 85 items for a total of 12.1 GB but at the bottom, where there is the pie it says I am using 135.8 GB and that there is only 13.1 GB free.
I have emptied the trash a couple of times and i have rebooted a couple of times as well.
I don't what can be the problem, can anybody help me.
Thanx

---

### Post by hyper_ch on 2008-02-01
please run:

```

df -l

```

and paste the output...

---

### Post by SIlvio77 on 2008-02-01
Hi there,

Here is what i get

phoenixor@Phoenixor:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19236308   8948744   9310412  50% /
varrun                 1553684       216   1553468   1% /var/run
varlock                1553684         0   1553684   0% /var/lock
udev                   1553684       112   1553572   1% /dev
devshm                 1553684         0   1553684   0% /dev/shm
/dev/sdb1            153834852 100727976  45292460  69% /media/share
/dev/sdd1            115377640 101806104   7710624  93% /media/share2
/dev/sde1            156288320 142442000  13846320  92% /media/New Volume
phoenixor@Phoenixor:~$ 

The drive in question is sde1

thanx

---

### Post by hyper_ch on 2008-02-01
13.2 GB free on that drive...

run

```

cd '/media/New Volume'
ls -al

```

---

### Post by SIlvio77 on 2008-02-01
Here u go

phoenixor@Phoenixor:~$ cd '/media/New Volume'
phoenixor@Phoenixor:/media/New Volume$ ls -al
total 229288
drwxrwxrwx  1 root root      12288 2008-02-01 19:16 .
drwxr-xr-x 11 root root       4096 2008-02-01 19:25 ..
drwxrwxrwx  1 root root          0 2008-01-16 23:24 Balls of Fury[2007]DvDrip[Eng]-FXG
drwxrwxrwx  1 root root       4096 2008-01-21 04:35 leopard
-rwxrwxrwx  1 root root  367128576 2008-01-26 17:55 Lipstick.Jungle.S01E01.PREAIR.DVDRip.XviD-CRX.avi
-rwxrwxrwx  1 root root 4698669056 2008-01-21 23:57 Mac OS X 10.4.8 [JaS AMD-Intel-SSE2-SSE3 with PPF1 & PPF2].iso
drwxrwxrwx  1 root root      12288 2008-02-01 19:16 Persepolis.2007.DVDRip.XviD-VoMiT
drwxrwxrwx  1 root root       8192 2008-02-01 19:04 .Trash-phoenixor
drwxrwxrwx  1 root root       4096 2008-02-01 19:07 UP THE CREEK-1984
phoenixor@Phoenixor:/media/New Volume$

---

### Post by jan quark on 2008-02-01
perhaps the swap file

pls post the result of 
```

sudo fdisk -l
```

---

### Post by hyper_ch on 2008-02-01
```

cd '/media/New Volume/.Trash-phoenixor'
ls -al

```

---

### Post by SIlvio77 on 2008-02-01
phoenixor@Phoenixor:~$ sudo fdisk -l

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x044cf332

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       19457   156288321    7  HPFS/NTFS
phoenixor@Phoenixor:~$ 


It seems i'm having a problem with my net connection due to the fact that i'm in india and that one of the underwater internet connection cables as been shutdown, so my replies might be a bit slow

---

### Post by jan quark on 2008-02-01
beat me
where is the linux partition ?
am I missing something or did you missed something

I get something like this when I run fdisk

```
Disk /dev/hda: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca98ca98

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3596    28884838+  83  Linux
/dev/hda2            3597        3736     1124550    5  Extended
/dev/hda5            3597        3736     1124518+  82  Linux swap / Solaris
jan@jan-desktop:~$ 
```

---

### Post by SIlvio77 on 2008-02-01
Ok just did that and it seems there is a all bunch of stuff in there (which i can't post cause if i do it's doesn't work).
How can i get rid of the items in there?

---

### Post by hyper_ch on 2008-02-01
it should be like that:
```

sudo rm -Rf /media/New\ Volume/.Trash-phoenixor/*

```

but safer is that:

```

cd '/media/New Volume/.Trash-phoenixor'
pwd

```
**check that the path is alright!!!**

```

sudo rm -Rf *

```

OR

to be 100% sure run this:
```

gksu nautilus

```
That will start nautilus with root privileges and then you navigate to that folder. Remember, folder starting with a dot "." are hidden. So you have to set nautilius to show them.

---

### Post by polmir on 2008-02-01
type in teminal
```
sudo apt-get clean
```

---

### Post by SIlvio77 on 2008-02-01
I can't post the complete result fdisk, cause otherwise i have a problem with post, i only posted the hard drive that it is related to

---

### Post by SIlvio77 on 2008-02-01
Ok it did the trick thanks a lot hyper_ch and all of you for the help.

---

### Post by hyper_ch on 2008-02-01
which way did you choose?

---

### Post by SIlvio77 on 2008-02-01
I went for the 

cd '/media/New Volume/.Trash-phoenixor'
sudo rm -Rf *

And it seems that all my drives have the same issue so doing the same to all of them, but it tells me that there is an input/output error and if i run Nautilus it tells me

Initializing gnome-mount extension

** (nautilus:7255): WARNING **: Hit unhandled case 6 (I/O error) in fm_report_error_loading_directory

---

### Post by hyper_ch on 2008-02-01
hmmm, if you empty the trash it should also be emptied... no clue about that...

but then I normally don't delete to trash... I just delete that stuff...

---

### Post by SIlvio77 on 2008-02-01
Ok. Cool and thanks again for the help.

---

### Post by hyper_ch on 2008-02-01
In Konqueror you can right-click the file(s), then press shift and then select delete... that will delete the files and not move them to the trash bin... in nautilus you should be able to do the same thing...

I do this because I do make auto-backups every 6h anway so there's not really anything that I could lose.

---

