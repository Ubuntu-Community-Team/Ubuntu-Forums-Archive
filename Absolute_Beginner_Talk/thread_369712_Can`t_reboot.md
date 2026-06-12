---
title: "Can`t reboot"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by nyonga on 2007-02-24
hi,
 I tried to change user permission in one of hd partition by editing /etc/fstab file. however, on booting all I see is:

/etc/rcS.d/S20 checkroot.sh : 407:readlink: permission denied
/etc/rcS.d/S20 checkroot.sh : 407: usplash_write: permission denied
*cannot initialize /etc/mtab
/etc/rcS.d/S20 checkroot.sh: 407: rm: permission denied
init: unable to execute "/bin/sh" for rc-default : permission denied
init: rc-default (3478) terminated with status 1

please someone help

---

### Post by taurus on 2007-02-24
Can you boot your machine into recovery mode?  If you can, post your /etc/fstab here then.

```
cat /etc/fstab
```

---

### Post by nyonga on 2007-02-24
Thanks. for quick reply. I tried booting in recovery mode but I still get the same message

---

### Post by taurus on 2007-02-24
Then you need to boot your machine with the LiveCD.  Do you know what partition is your / since you need to mount it and edit /etc/fstab on that partition?  If you don't know, post the output of this command from a terminal here.

Applications -> Accessories -> Terminal (from the LiveCD)
```
sudo fdisk -l
```

---

### Post by nyonga on 2007-02-24
sorry taurus, I had to type the whole output

The output is:

disk /dev/hda: 60.0GB, 60011642880 Bytes
255 heads, 63 sectors/tracks, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

device          Boot    Start       End         Blocks          Id           System
/dev/hda1                    1        608        4883728+      12          Compaq diagnotics
/dev/hda2       *         609     3995      27206077+        7          HPFS/NTFS
/dev/hda3                5408     7296      15173392+        f           w95 Ext`d (LBA)
/dev/hda4                3996     5407      11341890        83           Linux
/dev/hda5                5408     5472         522049+      82           Linux swap / solaris
/dev/hda6                5473     7296      14651248+      83           Linux
/dev/hda7                5473     5473                  0+      83           Linux

Partion table entries are not in disk order

---

### Post by nyonga on 2007-02-24
However usually I use /dev/hda3 for booting linux

---

### Post by taurus on 2007-02-24
Aren't you running it from a LiveCD with Gnome?

I now need to see your /etc/fstab to see what have you made changes to it that crashed your machine.

From a terminal, do

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda4 /mnt/ubuntu
cat /mnt/ubuntu/etc/fstab
```
Post the output of the last command here.

p.s.  Sorry but /dev/hda3 is an extended partition, not your /.

---

### Post by nyonga on 2007-02-24
here is the post of the command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
UUID=de507065-7635-4d16-bf8c-caf3a3e683a5 / ext3 rw,user 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=40C8440BC843FE22 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=4C54A5A254A58EF0 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=73d45f5f-e392-4bc7-8559-e969f139b009 /media/hda6 ext3 rw,user 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=fd4e7c29-2c39-46a2-b6f0-1ee3d4b36606 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-02-24
> **nyonga said:**
> here is the post of the command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
**UUID=de507065-7635-4d16-bf8c-caf3a3e683a5 / ext3 rw,user 0 1**
# /dev/hda1 -- converted during upgrade to edgy
UUID=40C8440BC843FE22 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=4C54A5A254A58EF0 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
**UUID=73d45f5f-e392-4bc7-8559-e969f139b009 /media/hda6 ext3 rw,user 0 2**
# /dev/hda5 -- converted during upgrade to edgy
UUID=fd4e7c29-2c39-46a2-b6f0-1ee3d4b36606 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

You are not supposed to modify your /etc/fstab if you don't know what you are doing.  The entry for your /, /dev/hda4, is wrong (and so is the one for /dev/hda6).

Therefore, you need to edit /mnt/ubuntu/etc/fstab 

```
gksudo gedit /mnt/ubuntu/etc/fstab
```
and replace these two lines 

```

UUID=de507065-7635-4d16-bf8c-caf3a3e683a5 / ext3 rw,user 0 1
UUID=73d45f5f-e392-4bc7-8559-e969f139b009 /media/hda6 ext3 rw,user 0 2

```
with these two new lines.

```

/dev/hda4   /   ext3   defaults,errors=remount-ro   0   1
/dev/hda6   /media/hda6   ext3   defaults   0   1

```
Save the changes and reboot, without the LiveCD.

---

### Post by nyonga on 2007-02-24
Thanks taurus, am able to boot perfectly. Thanks a million. However how can I mount /dev/hda6 and /dev/hda3 and have read/write peremission without messing /etc/fstab file. I will highly appreciate help on this

---

### Post by taurus on 2007-02-24
Since there is no /dev/hda3 (it's an extended partition), I will use /dev/hda6 then.

You can change the ownership of /media/hda6 to you so you can read and write to it anytime you want.  Assuming your login name is **nyonga**, run

```
sudo chown -R **nyonga**:**nyonga** /media/hda6
```

_WARNING_:  Do not run that command for your root partition, /, since doing so will trash your whole system.

---

