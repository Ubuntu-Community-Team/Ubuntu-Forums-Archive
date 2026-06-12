---
title: "[SOLVED] Cd-rom not working after installation of xubuntu 7.10"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by roems on 2008-04-14
Hi all,

Few days ago I installed xubuntu 7.10 in an old PC that does not have internet access, Today I tried to install some packages from the cd-rom and the drive is not working, because it is not being mounted.  It worked perfectly under xubuntu 6.10. 

**Here is the fstab list**

sudo mousepad /etc/fstab
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1c8ac4d8-da49-4564-ad7c-9aaa1fb508b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=afe69fc4-47b8-462d-936d-1048fd4e698e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

**When I try to mount the cd-rom manually:**

remigio@cirsium:~$ sudo mount /dev/hdc /media/cdrom0
mount: No medium found

**I cheked if the cd-rom appears in the list and it does as hdc so there is no error in the fstab name:**

remigio@cirsium:~$ ls -l /dev | grep hd
lrwxrwxrwx 1 root   root           3 2008-04-14 14:27 cdrom -> hdc
brw-rw---- 1 root   disk      3,   0 2008-04-14 14:27 hda
brw-rw---- 1 root   disk      3,   1 2008-04-14 14:27 hda1
brw-rw---- 1 root   disk      3,   2 2008-04-14 14:27 hda2
brw-rw---- 1 root   disk      3,   5 2008-04-14 14:27 hda5
brw-rw---- 1 root   disk      3,  64 2008-04-14 14:27 hdb
brw-rw---- 1 root   disk      3,  65 2008-04-14 14:27 hdb1
brw-rw---- 1 root   cdrom    22,   0 2008-04-14 14:27 hdc

Any suggestions? Thanks for your help.

Roberto

---

### Post by Inxsible on 2008-04-14
Could you comment out the line in fstab related to the cdrom. Cd drives are supposed to be auto detectable anyway.

Although it should also work with the line in there. But that's the only thing I can think of right now.

---

### Post by tcpip4lyfe on 2008-04-14
Are you positive it's hdc?  

Try:

 dmesg | less | grep ATAPI
or
 dmesg | less | grep CD/DVD
or
 dmesg | less | grep DVD

---

### Post by roems on 2008-04-14
Thanks for the replies:

I have checked the cd-rom name as tcpip4lyfe suggested and its indeed the hdc disk:

remigio@cirsium:~$ dmesg | less | grep ATAPI
# [   18.362851] hdc: ATAPI CDROM, ATAPI CD/DVD-ROM drive
#[   18.841048] hdc: ATAPI 44X CD-ROM drive, 128kB Cache, UDMA(33)

remigio@cirsium:~$ dmesg | less | grep CD/DVD
#[   18.362851] hdc: ATAPI CDROM, ATAPI CD/DVD-ROM drive

The pertinent line of the fstab regarding the cd-rom is:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

This is strange because as Inxsible points out the cd-rom should be mounted automatically. Any idea? 

Roberto

---

### Post by Inxsible on 2008-04-14
So commenting out that line and restarting X didnt work for you?

---

### Post by roems on 2008-04-14
> **Inxsible said:**
> So commenting out that line and restarting X didnt work for you?

Yes, indeed that solved the problem. Thanks for the help provided.

---

### Post by Inxsible on 2008-04-14
> **roems said:**
> Yes, indeed that solved the problem. Thanks for the help provided.
Cool. I have seent hat happen to a few people with IDE drives. I have /dev/sdc and it works with or without a line in fstab.

You can mark your thread solved by clicking Thread Tools>>Mark Thread as Solved.

---

