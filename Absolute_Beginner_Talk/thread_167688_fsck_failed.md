---
title: "fsck failed"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-04-28
fsck.ext3: no such file or directory while trying to open /dev/sda4 /dev/sda4

fsck failed
-----------------------------------------------------------------------------
gnome failed too now and i'm resided back to root@(none)$ which i have no clue about. beyond my bash skills. 
-----------------------------------------------------------------------------
anyhelp would be much appreciated on how to fix this and get back to gnome and especially fix my network problems as well as fsck.ext3. yikes.

---

### Post by user1397 on 2006-04-28
I think i've had a similar problem...try typing in fsck, and press enter. post what you see.

---

### Post by N3wtR0ckn13 on 2006-04-28
[QUOTE=erik1397]I think i've had a similar problem...try typing in fsck, and press enter. post what you see.[/QUOTE]
-----------------------------------------------------------------------------
$fsck

$/dev/sda3 is mounted

WARNING!!! running e2fsck on a mounted file system may cause severe filesystem damage.

Do you really want to continue?(Y/N): Yes

fsck.ext3: No such file directory exists while trying to open /dev/sda3fs
-----------------------------------------------------------------------------
this the second time i've done this and i think it has to do with /etc/fstab which i'll provide below. 
--------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#                
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda4       /var            ext3    defaults,usrquota,grpquota        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by user1397 on 2006-04-28
okay your problem is definitely different than mine.  i don't know anymore so srry i can't help you any longer!

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=erik1397]okay your problem is definitely different than mine.  i don't know anymore so srry i can't help you any longer![/QUOTE]

i don't think the partition was set correctly if anyone else has a similar problem. i'll post back my results in a few.

---

### Post by N3wtR0ckn13 on 2006-05-05
[QUOTE=N3wtR0ckn13]i don't think the partition was set correctly if anyone else has a similar problem. i'll post back my results in a few.[/QUOTE]

Okay, b/c the partition was not set correctly i had major errors across the board despite installing everything initially. only upon restart did everything go horribly wrong. 

the ext3 partitions for /boot swap / and /var did not set correctly. not only that, ext3 /boot was not set to initialize on startup setting no current directory for the correct installation of my server.

hopefully i got this down right. correct what errors you see, but i hope this helps. see my other posts too as i'll add final summaries too.

---

