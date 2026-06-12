---
title: "I can't read a cd of ubuntu"
date: 2007-11-20
forum: Apple Intel Users
---

### Post by jber on 2007-11-20
Hello!
My macbook Intel core duo no read any cd of ubuntu, and I can't install ubuntu on my macbook!!!!I have particionated my hd!
How I can repare it?
Help!thank you

---

### Post by volanin on 2007-11-20
Probably you got a BAD CD IMAGE or a BAD CD MEDIA.

First, check if the image that you downloaded is good.
Open a terminal and type:
```
$ md5sum ubuntu-7.10-desktop-i386.iso
```
and compare the value to the number below:
**d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso**

If it does not match, you have to download again.

Second, it you got a good CD image, you should burn it to a different CD MEDIA.
Get another Blank CD, and burn to it.

Third, even if it BOOTS OK, always check the integrity of the CD before installing.
Choose **CHECK THIS CD FOR DEFECTS** in the boot menu!
:)


[i]Also: it might sound silly, but don't forget to hold down the OPTION key while booting.
Then choose to boot from the CD in the menu that appears.[/i]

---

### Post by jber on 2007-11-20
The cds are Ok because in the macbook of my brother runs Ok, and my macbook reads a cds of music and games but no read the cds of ubuntu!And a year ago I haven installed ubuntu on this macbook that now don't run the ubuntu cds!!!
help!

---

