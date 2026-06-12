---
title: "Grub editing with windows allready installed on 2nd drive"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-14
Hi all
I have installed Ubuntu edgy on to an empty SATA HD which i want to keep as my main OS.

I still have my old windows OS on another SATA HD and have installed this as SDB or HD1 I dont yet understand that bit. 
Any way its there and i can read it ok and have tranferred a lot of my old data over to my obuntu system.
Now i would like the option of sometimes booting into my old XP system which i assume is still functional.
Now i get to the point :) 
how do i edit grub? is there a GUI or will i have to edit it manually? if i do can you give me some pointers please?
I have googled a bit but not found anything other than people doing a fresh install of windows which i dont need or want.
Also i've had difficulty in following some of it as i'm an absolute newbie:( 

Thanks for your help

Mike

---

### Post by apjone on 2007-03-14
1) open a terminal
2) become root 'sudo -s'
3) move to grub folder 'cd /boot/grub'
4) make a back up of menu.lst 'cp menu.lst menu.lst.bk'
5) edit menu.lst 'gedit menu.lst'
5) Add the following to the end of the file. note hd0 is the disk, and 1 is the partion number.  You will need to change it for yours. From your post i guess you should try and change it to (sd1,0) .

```

# Windows XP
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by mahiyar on 2007-03-14
You certainly would not need to reinstall windows, before you go and change grub, can you please clarify a few things? You said you copied files from your old drive to Ubuntu drive, how did you manage to do it, you must have mounted the windows drive. In that case can you please give the output of this command >> sudo fdisk -l.

---

### Post by confused57 on 2007-03-14
See this guide for how to edit menu.lst & a possible entry to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by mpooley on 2007-03-14
> **mahiyar said:**
> You certainly would not need to reinstall windows, before you go and change grub, can you please clarify a few things? You said you copied files from your old drive to Ubuntu drive, how did you manage to do it, you must have mounted the windows drive. In that case can you please give the output of this command >> sudo fdisk -l.

Thanks all - wont have time to try anything for a couple of hours at least but here is the output
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24415   196113456   83  Linux
/dev/sda2           24416       24792     3028252+   5  Extended
/dev/sda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5656    45431788+   7  HPFS/NTFS
/dev/sdb2            5657       14946    74621925    f  W95 Ext'd (LBA)
/dev/sdb5            5657       10553    39335121    7  HPFS/NTFS
/dev/sdb6           10554       14946    35286741    7  HPFS/NTFS

thanks again
Mike

---

### Post by mpooley on 2007-03-14
Ok This is what i  have done 
I have added this to the file

# Windows XP
title           Microsoft Windows XP Professional
root            (sdb1,1)
savedefault
makeactive
chainloader     +1


Now i dont understand the disk numbering cos i always thought it was hda1 etc not sdb1 but thats what fdisk reports.
Now I havn't saved this yet and i wont until someone tells me this is ok :KS 
but once i have changed it and reboot i assume i'll be offered my choice of OS's
what if it doesnt work? will i still be able to boot into ubuntu?

thanks all of you who replied 

Mike

---

### Post by mpooley on 2007-03-14
Its me again!!
I noticed in the How to that confused57 gave a link to, there were two map commands
map                (hd0) (hd1)
map                (hd1) (hd0)

but as i'm still confused about the disk naming i didn't know what to do here :confused: 

Mike

---

### Post by jhenager on 2007-03-14
I wonder if you could just use GrubEd to do this?
[http://www.arsgeek.com/?p=455](http://www.arsgeek.com/?p=455)

---

### Post by confused57 on 2007-03-14
Grub recognizes hard drives as hd0, hd1, etc, regardless of whether they're SATA or IDE.


title  Microsoft Windows XP Professional
root  (hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader +1

---

### Post by mahiyar on 2007-03-14
Sorry, but can you give the output of two more files. The first one is /boot/grub/device.map and the second a longer one is /boot/grub/menu.lst (thats a small L in "lst")

---

### Post by mpooley on 2007-03-14
thanks all --- its done:KS 

used the map commands as per confused57 :KS   and it worked fine

thanks a lot to all of you:popcorn: 

mike

---

