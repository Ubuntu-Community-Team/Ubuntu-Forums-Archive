---
title: "Hard drives rescanned everytime I boot the computer"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2008-04-08
HI,

My USB hard drive and internal hard drives must be rescanned by either ubuntu or Gnome. This takes several minutes. The problem started when I reinstalled ubuntu from scratch after messing up my previous system.

Any advise please?

Thanks,

---

### Post by tamoneya on 2008-04-08
it probably says in your fstab that they should be scanned automatically.  Post the contents of /etc/fstab and we can see if this is the problem.

---

### Post by Mega_Fauna on 2008-04-08
Hi,

Here it is, thanks for the swift response, I'll be back tomorrow evening (I did not expect to hear back so soon).


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=12451009-ce4f-4769-b444-f8a596d92862 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8a95cd58-8978-4af0-b4bd-bed3fd3be4c2 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=d31078af-f69c-441a-87bf-fbb0706b884e /media/sda4     ext3    defaults        0       2
# /dev/sdb1
UUID=47BB-8118  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9d284007-0606-4dc7-a954-edc3aceaa4a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1 /media/Ford_Prefect vfat umask=000 0 0

---

### Post by Soundman2 on 2008-04-08
That fstab does not cause them to rescan.  Could it be that the machine is not shutting down cleanly?  How are you restarting or shutting it down?

---

### Post by Mega_Fauna on 2008-04-09
Hi,

I shut down the machine with the proper button Log off / Reboot screen button. No doing anything wrong there.

fsck says that there is a difference between the boot sector and it's backup when I start the computer (IIRC).  I can post the bootup log if it helps, not sure where it is though so I'd need to know.

Thanks again,

---

### Post by pwn32 on 2008-04-09
Of course I don't know much, but could it just be your motherboard or something? 
Do you know its scanning your hard drive?

---

### Post by spiderbatdad on 2008-04-09
try booting with option 'profile' added to the kernel line from the grub menu, by pressing e to edit the kernel line. It will make that boot take several minutes while creating the profile, but should make subsequent boots considerably faster and eliminate the need to scan the whole drive...looking for jdong's how-to...

---

### Post by Mega_Fauna on 2008-04-09
pwn32

Not sure, how would I check that (sorry, I'm a ubuntunewb).

---

