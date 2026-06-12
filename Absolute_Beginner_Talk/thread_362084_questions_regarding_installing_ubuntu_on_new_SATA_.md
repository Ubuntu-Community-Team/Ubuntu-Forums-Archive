---
title: "questions regarding installing ubuntu on new SATA drive"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by polarpanda on 2007-02-15
Hi I am planning to install ubuntu on a brand new sata drive, i have a few concerns though, 

1.this system already have windows installed on a regular pata drive, so installing ubuntu on the sata drive should not affect windows boot up? 

2.can ubuntu's installer detect and format the SATA drive i plan to use? 

3.i want to partition the sata drive to two partitions one for ubuntu, and another one shared with windows, NTFS format works right? (using the program here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access files with windows, and i assume linux can access windows files?)

:)  thanks if anyone can answer those questions.

---

### Post by kanha on 2007-02-15
> **polarpanda said:**
> Hi I am planning to install ubuntu on a brand new sata drive, i have a few concerns though, 


1.this system already have windows installed on a regular pata drive, so installing ubuntu on the sata drive should not affect windows boot up? 

your windows will boot normally,but there will be a grub bootloader screen first,where you can select between windows or ubuntu

2.can ubuntu's installer detect and format the SATA drive i plan to use? 

yes coolly

3.i want to partition the sata drive to two partitions one for ubuntu, and another one shared with windows, NTFS format works right? (using the program here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access files with windows, and i assume linux can access windows files?)

it will be ok
but it will be better if you try FAT32 as shared partition filesystem.it will be a lot easier and you have to face no problems.With NTFS there may be issues.

:)  thanks if anyone can answer those questions.

:)

---

### Post by logos34 on 2007-02-15
> 1.this system already have windows installed on a regular pata drive, so installing ubuntu on the sata drive should not affect windows boot up?

If you wish to leave the windows completely undisturbed--including the bootloader--then you will want to make sure during ubuntu install that grub goes to the sata master boot record (MBR) or linux root partition and not the ide windows disk (as it usually does by default).  What happens is that grub chooses the first detected hard disk, and even if you set the sata to be first in the BIOS hard disk boot priority and thus expect it to show up as '(hd0)', grub will often instead designate your drives in order starting with the ide primary master and THEN sata, in which case it will be '(hd1)'.  If you are not sure, one way to avoid this is to unplug the windows drive before install.  

> 3.i want to partition the sata drive to two partitions one for ubuntu, and another one shared with windows, NTFS format works right? (using the program here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access files with windows, and i assume linux can access windows files?)

If you make an NTFS shared data partition, there isn't any need for fs-driver (unless you want to access your linux root system files.  Linux can read NTFS but needs NTFS-3G driver to write to it.

---

### Post by polarpanda on 2007-02-15
thank you, sounds good, i will try it out hopefully tommorow when my antec true power trio psu arrives, as of now my psu is having problems booting up with 3 harddrives haha

---

### Post by logos34 on 2007-02-15
> as of now my psu is having problems booting up with 3 harddrives haha

you too?  I had a antec psu in a Sonata case go out last august (same symtoms too, wouldn't boot two hard drives)--it was only a year old at the time and ran a light load.  But the warranty replacement they sent was 50 watts bigger, so that was some consolation.

---

