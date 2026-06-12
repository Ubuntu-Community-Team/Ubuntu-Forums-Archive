---
title: "problems with mounting disks"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by chrien on 2006-11-29
This might seem as an FAQ. I saw the guide that says: look at "System, Administration, Disks", but under "System, Administration", there's no such thing as "Disks"](*,). I tried to look up an old thread asking the same question, but to me there was too many strange terms.

I just installed Ubuntu from a downloaded iso image, into a new partition made manually using a live CD. It's version 6.10. The other partition runs on windows xp professional, and I can't se any of the two in "Places, Desktop".

Thanks for all help.




Christian

---

### Post by taurus on 2006-11-29
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by chrien on 2006-11-29
I get a weird answer :S:



sudo fdisk - 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by taurus on 2006-11-29
```
sudo fdisk -l
(That should be lower case letter l as in larry...)
```

---

### Post by chrien on 2006-11-29
hm... 

Now I'm trying to change the /etc/fstab.

this is what i get.

proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=9a29dfa4-b776-4794-81e3-76c237f4834f /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

My windows partition doesen't appear? (wich should be /dev/hda1)
can i just add it? what next?

Thanks so much for the patience :-D

---

### Post by taurus on 2006-11-29
Is /dev/hda1 a ntfs or a fat32 and where do you want to mount it!  I would add this line to the end of /etc/fstab to mount that partition...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line
```

/dev/hda1   /media/windows   ntfs   nls=utf8,umask=0222   0   0

```
Save it and from the terminal, create a mount point and mount it...

```
sudo mkdir /media/windows
sudo mount -a
df -f <-- you should see /dev/hda1 mounted on /media/windows!
```

p.s.  When it asks you for a password, use the same password that you use to log in...

---

### Post by chrien on 2006-11-29
it worked! thanks a million!

---

### Post by taurus on 2006-11-29
You're welcome.

---

