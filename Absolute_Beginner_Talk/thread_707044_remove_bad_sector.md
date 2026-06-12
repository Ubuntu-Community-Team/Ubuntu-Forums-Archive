---
title: "remove bad sector"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by sijukk on 2008-02-25
hi....

i am having a 40GB IDE HDD.Now it is having bad sector in the MBR, so i'm unable to partition it .Can any body tell is there any tool to  repair it .Thanks in advance.....

---

### Post by Mr. C. on 2008-02-25
At the factory, hard drives are sector scanned using drive-specific formatting software and/or firmware.  This creates a slip-sector table, which allows the drive to keep track of bad sectors, and remap a bad sector to a good one.  If the drive is very old, it may have too many bad sectors, and should be considered junk at that point.

The drive mfgs. website may have diagnostic and/or low level formatting software.  It may be wise to see what you can find for that drive, and run some diagnostics.  Do you know if the drive has SMART capabilities?

Don't confuse the misnomer "low level format" in Windows or fdisk with the same formatting as the drive mfg would perform.

MrC

---

### Post by sijukk on 2008-02-25
thanks for the post.....
i forgot to specify the manufacturer it is a [COLOR="Blue"]Segate[/COLOR] HDD
but i had tried to remove the bad sectors using [COLOR="Blue"]HDD Regen[/COLOR].i always struct at a perticular [COLOR="Red"]sector#913[/COLOR] ,i think it comes under MBR so i am not able to proceed.I had tried [COLOR="Blue"]Zeerofill[/COLOR] also but its not working since i cannot partition the disk..is there any other methods .........thanks in advance

---

### Post by stoodleysnow on 2008-02-25
Unless you want to spend ages, no. Spend £40 instead on a hard disk of double the capacity.

---

### Post by Mr. C. on 2008-02-25
You cannot "remove" bad sectors on a disk.  They are permanent.  It is time to get a new disk.

---

### Post by Flyingjester on 2008-02-25
> **Mr. C. said:**
> You cannot "remove" bad sectors on a disk.  They are permanent.  It is time to get a new disk.

+1

---

### Post by MrKlean on 2008-02-25
I would try a program called dban.  It will write zero's to all yer sectors.  That MIGHT help you... but if too many sectors are bad,,, the drive is scrap ; ((

---

### Post by Mr. C. on 2008-02-25
No software program will override the disk's internal slip sectoring.  This happens at the disk firmware/built in controller level; which software doesn't bypass.

New disk time. Game Over.

MrC

---

### Post by Duck2006 on 2008-02-25
> **Mr. C. said:**
> No software program will override the disk's internal slip sectoring.  This happens at the disk firmware/built in controller level; which software doesn't bypass.

New disk time. Game Over.

MrC

+1 on this one, new drive time.

---

### Post by vaalbygaardsvej on 2008-02-25
why would anyone try to save a 40 gig drive. the are useless at this size, and new ones at 250 gig are cheap as poop:)

---

### Post by Duck2006 on 2008-02-25
> **vaalbygaardsvej said:**
> why would anyone try to save a 40 gig drive. the are useless at this size, and new ones at 250 gig are cheap as poop:)

Not real ubuntu will run well on that size. I run ubuntu on a 30Gb drive.

---

