---
title: "Share FAT32 Drive"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by DavidRussellCA on 2006-09-14
I have a dual boot set up and working fine.  I have another partition (20GB) formatted in FAT32 at the moment that I'd like to share between Windows and Ubuntu.  How do I set it up so that it's mounted everytime I start Ubuntu and so that both OSes can read/write to it?

Thanks

---

### Post by bodhi.zazen on 2006-09-14
[list=number][*]create a mount point.
[*]edit fstab.[/list]

```
sudo mkdir /mnt/FAT32
sudo chmod 777 /mnt/FAT32
```
Call "FAT32" anything you like.

in fstab add a line:```
/dev/sdc1 /mnt/FAT32 vfat user,auto,rw 0 0
```
Assuming the drive is /dev/hdc1 and mount point is /mnt/FAT32.

EDIT: Sorry. To edit fstab:
```
sudo nano /etc/fstab
```
Add the above line You can cut and paste, select text in you browse, move cursor to new line in nano, push middle mouse button).

Ctrl-X to exit, "Y" to save

---

### Post by DavidRussellCA on 2006-09-14
Perfect, works!  Thank you :)

---

### Post by coffeecat on 2006-09-14
If you make your mount point /media/FAT32 instead of /mnt/FAT32 you get a drive icon appear automatically on your desktop - which is handy. :) Don't forget to:

sudo mkdir /media/FAT32

first.

---

### Post by DavidRussellCA on 2006-09-16
Hmm... the files I put on in Ubuntu don't seem to appear in Windows and vice versa.  What am I doing wrong?

---

### Post by xmastree on 2006-09-16
That sounds like there are two different locations, and you only *think* you're writing to the windows disk from ubuntu.

More instructions here:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

which might help.

---

### Post by Najand on 2006-09-16
You can format the drive from Windows with the filesystem FAT32 and then mount it in linux as described above... And  I think 
> More instructions here:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)
is just about ntfs which you cannot write to it from Linux.

---

### Post by xmastree on 2006-09-16
> **Najand said:**
> is just about ntfs which you cannot write to it from Linux.Nope, it covers both. The second and fourth subsections are about FAT.

---

### Post by DavidRussellCA on 2006-09-16
Thanks for the tip - turns out I was putting files in the wrong spot - oops.

Got that sorted now.

I'm still getting a permission denied error whenever I try to put files on the drive through Ubuntu - though I chmodded it 777.  Any ideas?  It works fine if I do a sudo cp or sudo gedit or whatever - but not through the GUI file browsers.

---

### Post by bodhi.zazen on 2006-09-16
Did you modify fstab? Post fstab.

---

