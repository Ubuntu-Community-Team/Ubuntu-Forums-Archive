---
title: "Can't Mount Burned DVDs"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ielliott on 2007-04-27
I had burned the WoW download (the free one from the site) onto a DVD when i still used Windows XP.

Now my DVD won't recognize, do DVDs burnt in Windows not get recognized by Linux?

Spits out the following error

CANNOT MOUNT VOLUME

Invalid Mount Option when attempting to mount the volume "WoW Installer".

Any tips hints ect would be helpful.

It doesn't matter if you just point me to a doc to read. :D

---

### Post by ielliott on 2007-04-27
More info
sudo mount /dev/dvd
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
--
 dmesg | tail
[   77.556247] Bluetooth: HCI device and connection manager initialized
[   77.556250] Bluetooth: HCI socket layer initialized
[   77.599803] Bluetooth: L2CAP ver 2.8
[   77.599808] Bluetooth: L2CAP socket layer initialized
[   77.613297] Bluetooth: RFCOMM socket layer initialized
[   77.613553] Bluetooth: RFCOMM TTY layer initialized
[   77.613556] Bluetooth: RFCOMM ver 1.8
[175389.580628] Unable to identify CD-ROM format.
[175504.823184] Unable to identify CD-ROM format.
[177308.957153] Unable to identify CD-ROM format.

---

### Post by ayllu on 2007-04-27
I have the same problem i got erros tring to muting some dvd burned in windows, i use a windows computer to copy my files and i got all mi files whit write protection and without permission to change it. So if anybody knows how to resolve this problem tell us.

---

### Post by Najand on 2007-04-27
Hmm, can you post your /etc/fstab file here?

---

### Post by ielliott on 2007-04-27
Well it looks like doing

sudo mount /dev/hdc -t udf /media/cdrom0

It mounted properly in read only

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=060911df-5d20-4974-b80e-cdb22547c013 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=9a60f82e-1f13-4581-a6c8-da50588aa58b none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Najand on 2007-04-27
First of all there should be a comma instead of space between iso9660 and user in the last line.
Secondly, try to add "rw" after noauto. Don't forget to separate it using a comma.

---

### Post by ielliott on 2007-04-30
Thanks, do i need to reboot for the fstab changes to take effect?

Or something along those lines?

---

### Post by lethu on 2007-05-01
It may seem stupid but the following worked for me.
try this : 
```
/dev/hdc /media/cdrom0 [COLOR="Red"]iso9660,udf[/COLOR] user,noauto 0 0
```
and no there shouldn't be a comma instead of space between iso9660 and user in the last line, you should also be able to try the above code without rebooting : ).

[COLOR="DarkGreen"]<edit>[/COLOR]If the above doesn't work try "auto" instead of "iso9660,udf"[COLOR="DarkGreen"]</edit>[/COLOR]

---

### Post by brundles on 2007-07-11
lethu - Thanks for that. Messed up as it is, that works when trying to automatically mount UDF only images.

Does anyone know why swapping the two around should have that effect? (I haven't tried it yet, but I'm assuming ISO images are still recognised?)

---

### Post by Ahslan on 2007-12-24
How do I get permission to change the fstab file??? I am the only user on my laptop...

---

### Post by Fatjoint on 2007-12-24
> **Ahslan said:**
> How do I get permission to change the fstab file??? I am the only user on my laptop...

```

sudo vim /etc/fstab

```

the command "sudo" says that you want to execute the command immediately after as the root user.

---

