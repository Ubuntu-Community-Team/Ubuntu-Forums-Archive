---
title: "[SOLVED] Restore so I can see the windows harddrive again"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-12-29
I reinstalled Windows and did then overwrite mbr so I used this guide to restore grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

```

linux@linux-laptop:~$ sudo fdisk -l
[sudo] password for linux:

Disk /dev/sda: 120,0 GB, 120034123776 byte
129 huvuden, 4 sektorer/spår, 454344 cylindrar
Enheter = cylindrar av 516 · 512 = 264192 byte
Diskidentifierare: 0xf1b06308

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               4       27787     7168000   1c  Dold W95 FAT32 (LBA)
/dev/sda2   *       27788      367390    87617574    7  HPFS/NTFS
/dev/sda3          367391      446770    20480040   83  Linux
/dev/sda4          446771      454340     1953060   82  Linux växling / Solaris

```

Problem is after I got access to ubuntu again was I unable to see sda2, the sda1 was still possible to see since it have not been changed.

How do I get back the access to sda2? Think it have something to do with it not being mounted.

---

### Post by philinux on 2007-12-29
Have a look at 

```
cat /etc/fstab
```

---

### Post by SpinningAround on 2007-12-30
Here is the output

```

linux@linux-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9139b048-b2be-417e-b0da-32057be9e5ee /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=80E9-C15B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4630A25130A247AF /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=08247ddd-777d-4ca8-9fdf-0ffb95dec598 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

Quite a newbie so where do I go from here? :)

---

### Post by meindian523 on 2007-12-30
Try installing the NTFS-3G drivers,search Synaptic for ntfs-3g

---

### Post by PriceChild on 2007-12-30
You've changed your ntfs partition a little too much and the "UUID" has changed.
To find the new one, type the following into a terminal```
sudo blkid | grep sda2
```You can then paste the new UUID into your /etc/fstab file replacing "UUID=4630A25130A247AF" on line 10

EDIT - and forgot you'll need to ```
sudo mount -a
``` afterwards to let the changes take effect :)

---

### Post by PriceChild on 2007-12-30
> **meindian523 said:**
> Try installing the NTFS-3G drivers,search Synaptic for ntfs-3gThey are installed by default in Gutsy. Notice that the partition used to work before windows was reinstalled (partition messed with) This would imply that whatever is trying to mount the drive, can't mount it in the same way as before. You could further discover it was the UUID changed, by replacing it with "/dev/sda2" in the fstab before.

---

### Post by meindian523 on 2007-12-30
@PriceChild

Could you please explain that fourth sentence again?that is this one

"You could further discover it was the UUID changed, by replacing it with "/dev/sda2" in the fstab before."

---

### Post by vanadium on 2007-12-30
The best thing you do is just update the UUID in your /etc/fstab like PriceChild explained in his first post.

1) make a backu copy of /etc/fstab in case you screw up

sudo cp /etc/fstab /etc/fstab.backup

2) Load fstab in your editor, as root

sudo gedit /etc/fstab

Either put the command in the background (Ctrl+z then "bg") or open a new terminal now.

3) look up the current UUID of your partition

blkid

Find the line starting with /dev/sda2, highlight and copy the part UUID="48C8D3333A74A592" to the clipboard (in the terminal, choose "Edit - Copy" or press Shift+Ctrl+C)


4) Paste the copied line over the corresponding part in your /etc/fstab, e.g. where it say something like 

```

# /dev/sda2
UUID=21e61b67-83f2-4c3e-8704-c7fc80a465f5 ....(remainder of the line)

```
replace UUID=... with the output you copied in step 3)

5) Save and exit. Now test weather it all works:

sudo mount -a

There should be no error message here. If there isn't, your partition will be mounted.

---

### Post by PriceChild on 2007-12-30
> **meindian523 said:**
> @PriceChild

Could you please explain that fourth sentence again?that is this one

"You could further discover it was the UUID changed, by replacing it with "/dev/sda2" in the fstab before."If you replaced the UUID with simply /dev/sda2, then sudo mount -a'd, it "should" just mount immediately, showing you that the UUID was different.

---

### Post by meindian523 on 2007-12-30
Thanks for the clarification,helped raise a small bit of knowledge :)

---

### Post by SpinningAround on 2007-12-30
Got it working!

Thanks everyone  \\:D/

---

