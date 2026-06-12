---
title: "unable to mount the selected volume"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by hughlle on 2006-09-29
ok, i just installed ubuntu onto my server and its all dandy apart from one issue.

i have 5 drives, 2 sata, 2 ide and a dvd-rw, 

all of the hard drives apart from the linux one are NFTS which i hope to change once i backup the data. back to the story, in places --> computer, i see all th drives. when i click on any one of these, including the dvd-rw i get an error message "unable to mount selected voluem"

the details given are: 

error: device /dev/hda1 is not removable

error: could not execute pmount

whats up, i just need to be able to acces my drives else whats the point in a "stable OS". i never had this issue before so why now?

any help is much appreciated

---

### Post by Bachstelze on 2006-09-29
That's because of a stupid idea of Ubuntu's developpers' to use pmount instead of mount. Use mount from the command line and you will be OK :)

---

### Post by hughlle on 2006-09-29
i'm afraid you'd have to give me a step by step guide on what you're atlking about :S

i've never actually done anything more than browse and feebly attempt to set up file sharing which i'll be pestering you chaps about later

bare in mind i'd like these drives to be mounted upon startup as i dont want to have to be typing in commands every single time

cheers

---

### Post by Bachstelze on 2006-09-29
Firstly, I need you to copy the output of

```
sudo fdisk -l
```

and then tell me where you want each partition mounted.

---

### Post by hughlle on 2006-09-29
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14218   114206053+   7  HPFS/NTFS
/dev/hda2           14219       14593     3012187+   f  W95 Ext'd (LBA)
/dev/hda5           14219       14593     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9354    75135973+  83  Linux
/dev/sda2            9355        9729     3012187+   5  Extended
/dev/sda5            9355        9729     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25841   195357928+   7  HPFS/NTFS

```

where i want them mounted? i don't know, i don't understand :(

i'd just like to be able to click on them in computer and have access

edit: the 80gb drive is my actual linux install

---

### Post by Bachstelze on 2006-09-29
All right, so here's what to do :

```

cd /media
sudo mkdir hda1 hdb1 sdb1
sudo mount -t ntfs /dev/hda1 /media/hda1
sudo mount -t ntfs /dev/hdb1 /media/hdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1

```

and see if it suits your needs. If so, I'll tell you how to mount them permanently so you don't have to type the commands ater every reboot.

---

### Post by hughlle on 2006-09-29
```
hughlle@piano:/media$ sudo mkdir hda1 hdb1 sdb1
mkdir: cannot create directory `hda1': File exists
mkdir: cannot create directory `hdb1': File exists
mkdir: cannot create directory `sdb1': File exists
hughlle@piano:/media$ sudo mount -t ntfs /dev/hda1 /media/hda1
hughlle@piano:/media$ sudo mount -t ntfs /dev/hdb1 /media/hdb1
hughlle@piano:/media$ sudo mount -t ntfs /dev/sdb1 /media/sdb1

```

no in computer i can see the file system drive and only one other hard drive (a 186gb one) and nothing else. and the 186gb drive is still not accessable :(

---

### Post by hughlle on 2006-09-29
ok, they are apparently mounted

```
mount: /dev/sdb already mounted or /media/windows/ busy

```

how do i access the drive now so that i can start to copy stuff to my other pc's drives?

---

### Post by hughlle on 2006-09-29
ok, used the disk tool thing under administrator and found them and their mount points all looked "normal" but when i clicked browse on any disc i got this

"You do not have the permissions necessary to view the contents of "hdb1"

---

### Post by Bachstelze on 2006-09-29
Open up Nautils or whatever file manager you like and go to /media/windows :)

**EDIT :** for your permissions problem, paste the output of

```
cat /etc/fstab
```

---

### Post by hughlle on 2006-09-29
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

nautilus eh? this sure is more fun to get working than microsoft :D

edit: hmmm, looks a bit funky compared to what the console shows :D

---

### Post by bodhi.zazen on 2006-09-29
Add this to fstab:

```
/dev/hda1 /media/hda1 ntfs auto,users 0 0
/dev/hdb1 /media/hdb1 ntfs auto,users 0 0
/dev/sdb1 /media/sdb1 ntfs auto,users 0 0
```

For other options see:

[Fstab options](http://www.tuxfiles.org/linuxhelp/fstab.html)

For ntfs write: [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by hughlle on 2006-09-30
when i change fstab i can get things working but theres just one issue which i'd like to be able to do without, after saving, the only way i can get it to  ctually implement the changes i've made is to restart the computer. is there a faster way? such a simple update via console?

---

### Post by hughlle on 2006-09-30
ok, i'm sort of beginning to get the hang of this allthough there is still much to be desired in the outcome.

i am currently formatting my drives using the system->admin->disks tool

i opted for reiserFS but i am lost as to what the access path should be for each of the discs (3 being formatted and mounted in total)

---

### Post by CatKiller on 2006-09-30
> **hughlle said:**
> when i change fstab i can get things working but theres just one issue which i'd like to be able to do without, after saving, the only way i can get it to  ctually implement the changes i've made is to restart the computer. is there a faster way? such a simple update via console?

```
sudo mount -a
```

---

### Post by CatKiller on 2006-09-30
> **hughlle said:**
> ok, i'm sort of beginning to get the hang of this allthough there is still much to be desired in the outcome.

There's a post that I made recently explaining some of what's going on with mounting and /etc/fstab. You might find it helpful with getting your head around it all.

[http://ubuntuforums.org/showpost.php?p=1557220&postcount=10](http://ubuntuforums.org/showpost.php?p=1557220&postcount=10)

---

