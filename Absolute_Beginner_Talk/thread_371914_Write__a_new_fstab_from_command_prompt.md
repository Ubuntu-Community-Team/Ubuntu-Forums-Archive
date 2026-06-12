---
title: "Write  a new fstab from command prompt"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Foudre on 2007-02-27
I'm having an annoying yet interesting problem here,  [http://ubuntuforums.org/showthread.php?t=371789]("http://ubuntuforums.org/showthread.php?t=371789") I had a thread before on a problem with mounting an external hard drive, but fstab after saving it, ending up saving something else over it for some reason, refer to link to get a better understanding

Main issue fstab gone, basicly, need to fix it from command prompt, the back up file for fstab is blank for some reason, and i can't remember the options for all the drives, so if there is some way to auto make a new fstab, strickly from comand prompt

---

### Post by TonKi on 2007-02-27
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

Just some links, I think you have to write it by hand.

Here is mine (feisty - with uuid)```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb8 :
UUID=151608b0-1425-4d6d-b497-456f066855bc / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb7 :
UUID=97ee722e-ac02-4c69-be19-16e7edd5007d /boot ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=719730f4-ff5e-4de1-babb-bd7df98c1da2 /home ext3 defaults 0 2
# Entry for /dev/sdb6 :
UUID=4477-41E0 /media/games vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdc1 :
UUID=d7310673-9620-426d-afe7-d50e39f07841 /media/store ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=FEFCD443FCD3F3BD /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sdb5 :
UUID=f0d829a1-32d6-458b-8c70-7679ce9b19bb none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by confused57 on 2007-02-27
Here's my Dapper fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /media/data     ext3    rw,user         0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

You could make a new fstab from the command prompt like this:

```
cat > /etc/fstab << "EOF"

<insert fstab entries>

# End /etc/fstab
EOF
```

---

### Post by punx45 on 2007-02-27
probably better off using a command line editor like vi or nano.

heres my fstab which includes an NTFS drive

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hdc1       /media/mediaserver      ext3    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by confused57 on 2007-02-27
punx45 is right, nano would be easier:

cd /etc
sudo nano fstab

---

