---
title: "New NTFS partition setup for sharing"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by jarhead14 on 2008-08-01
A quick summary of what I did:

-wiped hard drive
-used mac disk utility to create ~68gb partition for 10.4 and 25 for 8.04
-decided it was too much space and used gparted on live cd to shrink mac partition to 25gb and ubuntu partition to 10gb and created a large sharing partition using NTFS

ubuntu will not boot now! just says GRUB... did I screw up bad? can this be fixed without me wiping everything?

---

### Post by flaggh on 2008-08-01
Probably no big deal.  You just need to fix grub.  

First reboot the computer into rEFIt and go to the partition tool.  It will ask you to resync the partitions and you will accept.  Next pop in the live cd and boot into the live environment.  open a terminal window and type:
```
sudo grub
```
the grub utility should begin.  Next type:
```
find /boot/grub/stage1
```
it should return something like:
```
(hd0,3)
```
next type:
```
root (hd0,3)
setup (hd0,3)
quit
```
replacing (hd0,3) with whatever it told you before.
Reboot your computer and everything should work again.

---

### Post by jarhead142 on 2008-08-01
hmm.. now I have two linux icons at boot and neither one works - still just "GRUB"

---

### Post by cyberdork33 on 2008-08-01
Try holding the Option key at startup to see if you can boot Ubuntu that way.

---

### Post by flaggh on 2008-08-01
I forgot that you'll probably have fix your fstab as well.  The UUID of the drive has no doubt change so you'll have to fix it to say /dev/sda3 or whatever your drive is.  Once again, boot the live cd and open a command prompt.
```
sudo fdisk -l
```
This should give you a list of partitions.  Locate your linux root partition, for example /dev/sda3

```
sudo mount /dev/sda3 /media/disk
sudo gedit /media/disk/etc/fstab
```
locate the line that looks like:
```
UUID=12345678-9abc-def0-1234-56789abcdef0 /               ext3    relatime,errors=remount-ro 0       1
```
and replace it to say:
```
/dev/sda3 /               ext3    relatime,errors=remount-ro 0       1
```
that should do the trick.

---

### Post by jarhead142 on 2008-08-02
```
 mount: mount point /media/disk does not exist
```

not looking good...

---

### Post by flaggh on 2008-08-02
```
sudo mkdir /media/disk
```

---

