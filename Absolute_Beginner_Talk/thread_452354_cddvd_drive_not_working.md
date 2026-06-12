---
title: "cd/dvd drive not working"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Balinsky on 2007-05-23
ok i have a brand new dell n series desktop. It came with no OS so the cd drive had to work for me to install ubuntu. 

but now when i insert a cd of any kind into the drive nothing happens. Oh and to make matters dandy i cant boot from the drive either it tells me the device is not available. Ubuntu recognizes the drive and so does the system bios.

is their any sort of diagnostic i could run or anything i am running out of ideas.

thanks
jebsky

---

### Post by klytu on 2007-05-24
> **Balinsky said:**
> ok i have a brand new dell n series desktop. It came with no OS so the cd drive had to work for me to install ubuntu. 

but now when i insert a cd of any kind into the drive nothing happens. Oh and to make matters dandy i cant boot from the drive either it tells me the device is not available. Ubuntu recognizes the drive and so does the system bios.

is their any sort of diagnostic i could run or anything i am running out of ideas.

thanks
jebsky

If I understand you correctly, you are saying that you installed Ubuntu using the same CD drive that doesn´t seem to work. But now after Ubuntu is running, when you insert a CD into the drive nothing happens. Please post the output of ```
dmesg
``` and ```
cat /etc/fstab
``` Also could you please explain this a little more: > i cant boot from the drive either it tells me the device is not available Exactly what tells you that the device is not available and when does this happen?

---

### Post by Balinsky on 2007-05-24
i attached the demsg output its more than 500 lines.

here is the fstab:
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b9ec1ceb-fd92-45b9-8a0f-6cdc5f2bb348 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3038eb0b-0989-45ab-9295-924ac52364bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and yes you understand correctly the problem.

and what i mean when i cant boot from the drive is i tried to boot a live cd from BIOS and that didnt work either.

its leading me to believe it might be the hardware. It is weird though because both ubuntu and the BIOS detect the drive. Its brand new and really hasnt been moved but im starting to think the lazer is broken or something.

thanks
jebsky

---

### Post by klytu on 2007-05-24
> **Balinsky said:**
> i attached the demsg output its more than 500 lines.

here is the fstab:
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b9ec1ceb-fd92-45b9-8a0f-6cdc5f2bb348 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3038eb0b-0989-45ab-9295-924ac52364bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and yes you understand correctly the problem.

and what i mean when i cant boot from the drive is i tried to boot a live cd from BIOS and that didnt work either.

its leading me to believe it might be the hardware. It is weird though because both ubuntu and the BIOS detect the drive. Its brand new and really hasnt been moved but im starting to think the lazer is broken or something.

thanks
jebsky

Try changing this line in your fstab: > /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0 to this:>  **/dev/sr0**       /media/cdrom0   udf,iso9660 user,noauto     0       0

Then try putting a CD into the drive when Ubuntu is running and see if that works. In the unlikely event that this works I am still  baffled as to why you can´t boot from the CD drive now if you could before...

---

### Post by Balinsky on 2007-05-24
> Try changing this line in your fstab:
Quote:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
to this:
Quote:
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto 0 0

no dice i think the drive is busted

---

