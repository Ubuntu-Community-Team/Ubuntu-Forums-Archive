---
title: "Changing partition???"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by siongz on 2007-11-28
Hi im new to linux... and ive realised that ive installed in the wrong partition... izzit possible to change partition or shrink one to increase my ubuntu's??

the result of "sudo fdisk -l" is as follow

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe233bc5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4534    36419323+   7  HPFS/NTFS
/dev/sda2            4535        9729    41728837+   5  Extended
/dev/sda5            9356        9417      498015   82  Linux swap / Solaris
/dev/sda6            4535        9354    38716587   83  Linux
/dev/sda7            9418        9729     2506108+  83  Linux

and for df -h is as follow:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.4G  2.2G   42M  99% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   80K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  468M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6              37G  194M   35G   1% /boot
/dev/sda1              35G  2.5G   33G   8% /media/sda1
overflow              1.0M   48K  976K   5% /tmp


I believe ive installed ubuntu in sda7, will actually should be in sda6, any idea how to change partition or shrink the sda6??? thx in advance

---

### Post by forestpixie on 2007-11-28
you can use gparted - download the iso from [here]("http://download.tuxfamily.org/gpartedlive/") rather than use the one on the gutsy disc.

I'd be interested to know why, if you're new to linux you used a boot partition

---

### Post by master_kernel on 2007-11-28
You can use any partition program -- I prefer Partition Magic until gParted is stabilized. But gParted is definitely the open source choice.

---

### Post by forestpixie on 2007-11-28
has there been problems with gparted then - I'd like to know and I'll not send people that way!!

---

### Post by siongz on 2007-11-28
> **forestpixie said:**
> you can use gparted - download the iso from [here]("http://download.tuxfamily.org/gpartedlive/") rather than use the one on the gutsy disc.

I'd be interested to know why, if you're new to linux you used a boot partition

um.. what do u mean using a boot partition?? aniway... im not sure which sda my ubuntu is in... anione can help me??? and what does "/boot? means??? sorry for asking such a stupid question...

---

### Post by forestpixie on 2007-11-29
no stupid questions :)

looks like you've got ubunut installed to sda7, it looks to me like you/ve made sda6 a /boot partition - when you installed how did you do the partitioning?

/boot would be a partition that holds the files and directories that boot the pc, contain the kernel and the like I think - but I've not been here long. You appear to have a 37Gb partition for it.

---

