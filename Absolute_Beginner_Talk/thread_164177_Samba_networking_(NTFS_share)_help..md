---
title: "Samba networking (NTFS share) help."
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by gamerteck on 2006-04-22
Hi everyone.  I am very new to the linux community and even newer to Ubuntu, so far love it.

I have samba setup on my network and I can view/access it from my XP box.
--------------------------------------------------------------------------
My linux box is setup like this (In regards to partitioning):

1x40GB HDD - This drive has XP and Ubuntu.
[INDENT]'/dev/hda1' - XP[/INDENT] 
[INDENT]'/dev/hda3' - Ubuntu[/INDENT]
[INDENT]'/dev/hda5' - NTFS Partition[/INDENT]

I also have a seprate 80GB HD that is full NTFS parttions
---------------------------------------------------------------------------

**My question is:**
How to I configure my samba .conf file to share out my NTFS partition on my 40GB drive?
(I have searched all morning without any luck)
Thanks in advance.

---

### Post by prezbedard on 2006-04-22
I have fiddled around with samba in the past on other distros and I believe you won't be able to do this with NTFS. but not 100% sure

---

### Post by gamerteck on 2006-04-22
So you're saying I might not be able to view NTFS parttions on my linux box from my networked XP box?

---

### Post by prezbedard on 2006-04-22
I'm pretty sure.

I did find this

[http://www.linuxforums.org/forum/servers/8368-samba-winxp-sharing.html](http://www.linuxforums.org/forum/servers/8368-samba-winxp-sharing.html)


This person is trying to do something similar.

---

### Post by gamerteck on 2006-04-22
Yeah, he is doing something similar but I don't want my linux to be able to use the NTFS partition.

I want my XP networked box to be able to connect to the NTFS partition that is on my Ubuntu/XP dual boot box.

I think that in the smb.conf I would write something like this:
[INDENT][B][share2]
path = /my_shared_folder
comment = Some random files[/B][/INDENT]

I am unsure how to point the share path to my NTFS partition.

Thanks for the help so far prezbedard :D

---

### Post by prezbedard on 2006-04-22
Have you been able to mount the NTFS partition?

---

### Post by gamerteck on 2006-04-22
Yes it's mounted, I mean I can access it but I can't access it in linux of course.

Not really sure what mounted means in linux terms though; so I would have to mount it in samba? Or from within Ubuntu?

---

### Post by gamerteck on 2006-04-22
I guess it's not mounted her is what my fstab looks like.
**----------------------------------------------------------------------------------------------**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
**----------------------------------------------------------------------------------------------**

So would I enter something like?:
[indent]dev/hda1     auto    rw,user,noauto  0       0[/indent]

---

### Post by gamerteck on 2006-04-22
I found the answer.  The link is below.
[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

Again, thanks **prezbedard** you pointed me in the right direction!!

---

### Post by prezbedard on 2006-04-22
no problem

glad to see you were able to find some helpful info.

---

