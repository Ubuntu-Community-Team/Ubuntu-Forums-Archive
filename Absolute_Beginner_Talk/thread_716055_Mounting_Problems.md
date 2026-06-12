---
title: "Mounting Problems"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-05
I get the following error when running :mount /mnt/auto/cdrom


wrong fs type, bad option, bad superblock on /dev/scd0,
or too many mounted file systems

my /etc/fstab is this

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0  /mnt/auto/cdrom udf,iso9660 ro,owner,noexec,noauto  0  0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0


and I'm running DSL

---

### Post by tech9 on 2008-03-05
> **the beak said:**
> I get the following error when running :mount /mnt/auto/cdrom


wrong fs type, bad option, bad superblock on /dev/scd0,
or too many mounted file systems

my /etc/fstab is this

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0  /mnt/auto/cdrom udf,iso9660 ro,owner,noexec,noauto  0  0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0


and I'm running DSL

try 

```
sudo mount /media/cdrom0
```

make sure you have media in you cdrom drive - also you can right-click the device  and select mount

---

### Post by the beak on 2008-03-05
I get the error: cant  find /MEDIA/CDROM0 in /etc/fstab or /etc/mtab

??

---

### Post by the beak on 2008-03-05
Do I neeed a line for /dev/cdrom in my etc/fstab

---

### Post by the beak on 2008-03-05
any clues, please?

---

### Post by the beak on 2008-03-05
I'm not that impressed with Linux if it's this much bother to access a CD drive!

---

### Post by Oldsoldier2003 on 2008-03-05
> **the beak said:**
> I get the following error when running :mount /mnt/auto/cdrom


wrong fs type, bad option, bad superblock on /dev/scd0,
or too many mounted file systems

my /etc/fstab is this

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0  /mnt/auto/cdrom udf,iso9660 ro,owner,noexec,noauto  0  0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0


and I'm running DSL


make sure you have the directory /mnt/auto/cdrom on your computer. If not, do this in a terminal:

```
sudo mkdir -p /mnt/auto/cdrom
```

then edit your fstab to modify your line to look like this (you can paste it):


```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by the beak on 2008-03-05
thanks I'll try that

---

### Post by the beak on 2008-03-05
It's still not working heres my etc/fstab

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0

I'm I typing in the correct command?

---

### Post by dstew on 2008-03-05
What mount command are you using? If your fstab says "noauto", maybe you cannot mount it with mount -a, you have to issue an explicit mount command like```
sudo mount -t iso9660 /dev/scd0 /media/cdrom0
```

---

### Post by spiderbatdad on 2008-03-05
You seem to have two threads running on this question.  Your entry in /etc/fstab looks flawed change to ,exec  also you should have a UUID=. hopefully that is present

---

