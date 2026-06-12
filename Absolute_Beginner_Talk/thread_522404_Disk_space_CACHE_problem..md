---
title: "Disk space CACHE problem."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-08-10
I'm moving data from an Old account to a New account.  So far I only managed to do so by duplicating the files while I'm moving.  But then I delete the files from the Old account so the transfer can go on.

But when checking "System monitor" the Used column stays at 88% even when I deleted the big original files.  I'm suspecting there's some CACHE that have stored some backups of my big files somewhere.
Where can I find this CACHED data and empty it?

---

### Post by plucky on 2007-08-10
Try emptying the trash can.:)

---

### Post by jingo811 on 2007-08-10
Trash can is already empty.  It's something else lurking under the hood which I can't find :confused:

---

### Post by asmoore82 on 2007-08-10
> **jingo811 said:**
> I'm moving data from an Old account to a New account.  So far I only managed to do so by duplicating the files while I'm moving.  But then I delete the files from the Old account so the transfer can go on.

But when checking "System monitor" the Used column stays at 88% even when I deleted the big original files.  I'm suspecting there's some CACHE that have stored some backups of my big files somewhere.
Where can I find this CACHED data and empty it?

:confused: is all of this taking place on the same partition or same hard drive or totally different drives?

---

### Post by jingo811 on 2007-08-10
My second Hard drive where my /home partition resides it is pushing 98% at this point even after having deleted all the duplicate big files I was transferring.
I have rebooted the PC a couple of times logged into both my New and Old account it says the same 98% Used. :confused:

Something is whack!

---

### Post by asmoore82 on 2007-08-10
did you just move files from on user's home to another's on the same /home partition ??

---

### Post by jingo811 on 2007-08-10
Yes I moved around 15 GB of data from OldUser/home to NewUser/home.  Then I deleted the duplicate files on OldUser/home to make room for my /home partition.

Judging from this fdisk-l can I be 100% certain that my SWAP partition is connected to my /(root) partition right?  Or has my /home partition taken over the SWAP role?
```

pingu@renaissance:~$** sudo fdisk -l**

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        3831    20506972+   c  W95 FAT32 (LBA)
/dev/hda3            3832        4998     9373927+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226    b  W95 FAT32
[B]/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux[/B]
pingu@renaissance:~$ 
```

---

### Post by annda on 2007-08-10
are you by any chance using sudo or gksudo nautilus to copy/delete the files between acccounts? if so, check root's trash: 

```
ls -a /root/.Trash
```

---

### Post by jingo811 on 2007-08-10
> are you by any chance using **gksudo nautilus** to copy/delete the files between acccounts? if so, check root's trash: 
Yes I was.

```
pingu@renaissance:~$** ls -a /root/.Trash**
ls: /root/.Trash: No such file or directory
pingu@renaissance:~$** ls /root/.Trash**
ls: /root/.Trash: No such file or directory

pingu@renaissance:/$** ls -a /root/.Trash**
ls: /root/.Trash: No such file or directory
```

```

pingu@renaissance:/root$** ls -la**
total 72
drwxr-xr-x 13 root root 4096 2007-08-10 22:59 .
drwxr-xr-x 21 root root 4096 2007-08-10 17:50 ..
-rw-r--r--  1 root root 2227 2006-12-20 16:50 .bashrc
drwxr-xr-x  2 root root 4096 2007-08-10 18:25 Desktop
-rw-------  1 root root   16 2007-08-10 17:06 .esd_auth
drwx------  3 root root 4096 2007-08-10 22:58 .gconf
drwx------  2 root root 4096 2007-08-10 23:00 .gconfd
drwxr-xr-x  3 root root 4096 2007-08-10 18:45 .gnome
drwx------  4 root root 4096 2007-08-10 18:25 .gnome2
drwx------  2 root root 4096 2007-08-10 17:06 .gnome2_private
drwxr-xr-x  2 root root 4096 2007-08-10 18:46 .gstreamer-0.10
drwxr-xr-x  3 root root 4096 2007-08-10 18:25 .nautilus
-rw-r--r--  1 root root  141 2006-12-20 16:50 .profile
-rw-------  1 root root  721 2007-08-10 22:59 .recently-used
-rw-r--r--  1 root root 2739 2007-08-10 22:59 .recently-used.xbel
drwx------  3 root root 4096 2007-08-10 19:46 .synaptic
drwx------  4 root root 4096 2007-08-10 18:46 .thumbnails
drwxr-xr-x  2 root root 4096 2007-04-15 13:59 .wapi
pingu@renaissance:/root$ 


```

It no work :(

---

### Post by jingo811 on 2007-08-10
Terminal was bad at finding /root/.Trash but somehow I stumbled on it with gksudo nautilus.
But it couldn't delete the triplicate files.  Nor can I do it in Terminal.
Which might be bad rm usage.  Teach me how to remove the files in .Trash-root?

```
pingu@renaissance:/home$ **ls -la**
total 52
drwxr-xr-x 10 root  root   4096 2007-08-10 18:09 .
drwxr-xr-x 21 root  root   4096 2007-08-10 17:50 ..
drwxr-xr-x  2 root  root   4096 2007-07-27 09:25 login
drwx------  2 root  root  16384 2006-11-29 21:43 lost+found
drwxr-xr-x 15  1002 pingu  4096 2007-03-03 21:39 michael
drwxr-xr-x 52 mikey mikey  4096 2007-07-18 23:52 mike
drwxr-xr-x 25 mikey mikey  4096 2007-08-10 22:31 mikey
drwxr-xr-x 22 pingu pingu  4096 2007-08-10 22:55 pingu
drwxr-xr-x  2 root  root   4096 2007-07-18 14:53 Recycled
drwx------  6 root  root   4096 2007-08-10 20:55 .Trash-root

```

```
pingu@renaissance:/home$** ls -a /root/.Trash**
ls: /root/.Trash: No such file or directory
pingu@renaissance:/home$ **rm .Trash-root**
rm: cannot remove directory `.Trash-root': Is a directory
pingu@renaissance:/home$ **sudo rm .Trash-root**
Password:
rm: cannot remove `.Trash-root': Is a directory
pingu@renaissance:/home$ 
```

---

### Post by jingo811 on 2007-08-10
```
 sudo rm -R .Trash-root
```
Disk usage dropped from 98% down to 57% again :lolflag: It was the most beutiful thing seeing the disk numbers drop 	\\:D/  PROBLEM SOLVED!

---

### Post by annda on 2007-08-10
> Teach me how to remove the files in .Trash-root?


```

sudo rm -Ri /home/.Trash-root/*
```


the R option is for 'recursive' in case you have any directories there and the i stands for 'interactive', so you don't delete any important files by mistake.

UPDATE: i was too slow again. and congratulations for solving the problem!

---

### Post by jingo811 on 2007-08-10
Whoops....... mistake already made.  I hope .Trash-root will be able to recreate itself in the future when I need it.

---

### Post by schorsch on 2007-08-10
It will ....

---

### Post by annda on 2007-08-10
don't worry. i'm trying to be over-cautious when giving advice. i have deleted trash on my external drive and mp3 player at least a dozen times and it always comes back

---

