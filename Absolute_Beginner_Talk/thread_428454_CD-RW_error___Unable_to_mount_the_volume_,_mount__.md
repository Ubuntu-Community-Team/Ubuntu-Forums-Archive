---
title: "CD-RW error :  Unable to mount the volume , mount : no meduim found"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-30
hey  I have a DVD-ROM and a CD-RW , 

the DVD works fine with CDs, but the CD-RW doesnt read any CD ,
when I put the cd in it says 
```
Unable to mount the volume # [COLOR="DarkRed"](name of the CD)[/COLOR]
, mount : no meduim found
```
it is strange because it can tell me the name of the CD , but it cant read it .
anybody has an idea ? 
here is how the CD-ROM is loaded  in my fstab
[B]/dev/hdd       /media/cdrom1   udf,iso9660 user,noauto     0       0
[/B]


[by the way  I am one of those who had "[CAN ACCESS TTY]("http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html")" during installation of feisty , so I installed feisty using **modeprob piix**  may be it be related to this ]

---

### Post by medya on 2007-04-30
never mind i fixed it !

---

### Post by Drakkor on 2007-04-30
I have 2 writers, one CD,the other DVD........here's my fstab   doesn't Fiesty  do scd instead of hcd,hdd ??
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by medya on 2007-04-30
> **Drakkor said:**
> I have 2 writers, one CD,the other DVD........here's my fstab   doesn't Fiesty  do scd instead of hcd,hdd ??
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

it does but I had changed it , as it wasnt working...

---

