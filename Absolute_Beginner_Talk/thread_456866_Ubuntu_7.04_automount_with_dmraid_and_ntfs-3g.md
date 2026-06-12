---
title: "Ubuntu 7.04 automount with dmraid and ntfs-3g"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Haderen on 2007-05-28
I have a Asus K8N-VM (nForce 410). I can get both dmraid and ntfs-3g to work (which is a must, since all my music is located on a winXP partition).

However I can't get the winXP partition to automount via the /etc/fstab.

dmraid should be enabled from boot.local before mounting, but it doesn't do the trick. 

Does boot.local work on 7.04 or is there another way to enable dmraid before fstab is run?

---

### Post by cferthorney on 2007-05-28
> **Haderen said:**
> I have a Asus K8N-VM (nForce 410). I can get both dmraid and ntfs-3g to work (which is a must, since all my music is located on a winXP partition).

However I can't get the winXP partition to automount via the /etc/fstab.

dmraid should be enabled from boot.local before mounting, but it doesn't do the trick. 

Does boot.local work on 7.04 or is there another way to enable dmraid before fstab is run?

To my knowledge dmraid is a kernel mode so almost certainly will be booted prior to fstab (At least in my experience.  I haven't yet had enough experience with Fiesty's new system startup to be sure)  Could you post the contents of your /etc/fstab ?  One thing I discovered the first time I used ntfs-3G was you needed to use mount -t ntfs-3g (So in fstab /NTFS   /dev/hda1   ntfs3g   <opts> )

I hope this helps.  If not hopefully someone with more Fiesty experience can help you :-)

---

### Post by Haderen on 2007-05-28
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=2c4235ec-010f-45ad-b733-f5b92eeba455 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=f9aba496-ec2d-47cd-b60e-101ced4e3761 none            swap    sw              0       0
/dev/hdb		/media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        	/media/floppy0  auto    rw,user,noauto  0       0
/dev/nvidia_caghehfh5	/home/mads/Desktop/Musik ntfs-3g locale=da_DK.utf8, 0	0

```

dmraid is running at startup, but mounting isn't

---

### Post by igloocentral on 2007-05-29
...at the risk of saying something you already know...

should the comma be there in the fstab after "locale=da_DK.utf8**,**" ?

did you configure initramfs for dmraid? (in feisty this normally happens when you install the dmraid package)

---

### Post by kevpatts on 2007-05-31
I'm looking to do the same thing (including VMware usage). I've installed dmraid and dmraid -ay gives me:```
RAID set "nvidia_ebgeeceg" already active
RAID set "lsi_bhheafbjeae" already active
RAID set "nvidia_ebgeeceg1" already active
RAID set "lsi_bhheafbjeae1" already active
RAID set "lsi_bhheafbjeae5" already active
RAID set "lsi_bhheafbjeae6" already active

```

I have one IDE drive that I boot from (Ubuntu Feisty) and two RAID 0 (nForce 570) SATA drives with XP on them.

Can you tell me how you configure dmraid? I'm finding info to be sparse.

Kevpatts

---

### Post by kevpatts on 2007-05-31
Okay, I have the drive mounted but I have the same problem. It won't mount as /media/cdir at boot.

My fstab looks like:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb6
UUID=fe1c10e5-7327-4757-9b36-8f7d09a0e119 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=E220779B2077757F /media/oldcdir  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=28e965b5-fefc-4cf5-b777-044811ebd736 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/mapper/nvidia_ebgeeceg1	/media/cdir	ntfs-3g	rw,noauto	0	0
```

mount -a doesn't mount it either, I have to run: ```
mount -t ntfs-3g /dev/mapper/nvidia_ebgeeceg1 /media/cdir
```to get it to mount. dmesg doesn't give me many clues either.

Kevpatts

---

### Post by kevpatts on 2007-06-03
Removing the 'noauto' helped. I can be such an idiot sometimes!

---

### Post by alienexplorers on 2007-06-03
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

