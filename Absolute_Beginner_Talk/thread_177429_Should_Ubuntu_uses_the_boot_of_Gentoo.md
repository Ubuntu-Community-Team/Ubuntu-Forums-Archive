---
title: "Should Ubuntu uses the /boot of Gentoo?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by MichaelZ on 2006-05-16
Hello,

I would like to install Ubuntu 5.10 along with Gentoo (already installed).

A friend has told me that I do not have to define a /boot partition, but I can use the one of Gentoo. This way there will be no problem with GRUB.

Actually I have a:

For Gentoo:
/boot (primary, 255MB)
/swap (logical, 1GB)
/ (logical 6GB)

Moreover, I have around 6GB of unallocated space on my hard-disk. I would like to install Ubuntu in this unallocated space.

Do I simply have to define this unallocated space as / partition and let Ubuntu uses the /boot and /swap of Gentoo? Will Ubuntu overwrite the /boot of Gentoo and makes it unusable?

Thank you very much.

Best wishes,
Michael

---

### Post by Sef on 2006-05-16
> Will Ubuntu overwrite the /boot of Gentoo and makes it unusable?

What should happen is that Ubuntu will install GRUB and it will be the default option.  Gentoo will be an option to boot into.  It is possible to make Gentoo the default option, if you so desire.

---

### Post by syg00 on 2006-05-16
Mmmm - I'd be willing to bet the Ubuntu installer won't recognise another Linux install (I'd be happy to be proved wrong).

In such situations I prefer not to install a bootloader at all for the second (and subsequent) installs. Not sure if ubuntu allows this as an option - I installed on a laptop, and let it install grub to the MBR; can't remember what choices I had.
If Ubuntu does take over, shouldn't be too hard to get the menu.lst back in some semblance of usablility.

---

### Post by syg00 on 2006-05-16
Duplicate post - deleted.

---

### Post by towsonu2003 on 2006-05-16
[QUOTE=Sef]What should happen is that Ubuntu will install GRUB and it will be the default option.  Gentoo will be an option to boot into.  It is possible to make Gentoo the default option, if you so desire.[/QUOTE]
Ubuntu is unfortunately very much like Windows. it will most probably not recognize your Gentoo, but it will recognize Windows. so you will have to find a way (I believe there was an option) to tell Ubuntu to install the bootloader to the boot (root?) partition instead of the mbr. **Dapper LiveCD does not give you that option**... Than when everything is done, boot to your Gentoo and add the following to the end[1] of your /boot/grub/menu.list (.lst?) [in Gentoo]:
```

title      Ubuntu Bootloader
root      (hdx,y)
savedefault
chainloader   +1

```
you will have to figure out the (hdx,y) part. To give an example, /dev/hda1 is (hd0,0) and /dev/hdaT is (hd0,T-1) where T is a number...

[1]Gentoo may provide another way to edit grub's menu.lst though...

---

### Post by MichaelZ on 2006-05-16
Hello,

Thank you very much for your help :).

I have also asked more info to my friend and he told me to use the unallocate space for / and to addind /boot and /swap of Gentoo to Ubuntu without formatting them. And it should work.

I am not sure if Ubuntu does allow to not install the booloader. In Gentoo there was such option, but in Ubuntu I do not remember (but I think not).

Anyway, to know what it works I will have to try. If I mess up, I will re-begin. 

Best wishes,
Michael

---

### Post by MichaelZ on 2006-05-16
[quote=MichaelZ]
I have also asked more info to my friend and he told me to use the unallocate space for / and to addind /boot and /swap of Gentoo to Ubuntu without formatting them. And it should work.
[/quote] 
I have tried and it worked only partially. At the end Ubuntu wanted that I set the GRUB (anywhere). So, I decided in /dev/hda. Ubuntu finished the installation, but Gentoo was not more available. Well, the funny is that the GRUB used the splash of Gentoo.

To solve this, I have copied the GRUB info of Gentoo in the grub.conf file, into the menu.lst of Ubuntu. So, I could re-use Gentoo.

Anyway, I have lost all the  configurations (e.g., keyboard layout) that I have previously done, before installing Ubuntu.

I just hope that the Gentoo and Ubuntu will not conflict, because of the same /boot partition.

Best wishes,
Michael

---

### Post by towsonu2003 on 2006-05-16
> **MichaelZ]I decided in /dev/hda.[/QUOTE]
that's the mbr. if you gave it the name of where the boot partition is (/dev/hdaX) -if you can? don't remember- than my post might have been helpful  said:**
> 
Anyway, I have lost all the configurations (e.g., keyboard layout) that I have previously done, before installing Ubuntu.
gentoo lost its configurations? that shouldn't happen. each distro uses its own partition of / to keep the configuration files :confused: 
[QUOTE=MichaelZ]
I just hope that the Gentoo and Ubuntu will not conflict, because of the same /boot partition.[/quote]
I don't think so. My understanding from various partition howtos is that yours is a common practice among non-newbies...

---

### Post by MichaelZ on 2006-05-16
> **towsonu2003]that's the mbr. if you gave it the name of where the boot partition is (/dev/hdaX) -if you can? don't remember- than my post might have been helpful  said:**
>  

Yes, I have installed it in the mbr. It seemed the best option.

[quote=towsonu2003]
gentoo lost its configurations? that shouldn't happen. each distro uses its own partition of / to keep the configuration files :confused: 
 
Yes. I have lost the background, keyboard layout, font and so on. I will see if I still have this problem in the future.

[quote=towsonu2003]
I don't think so. My understanding from various partition howtos is that yours is a common practice among non-newbies...[/quote] 
I hope. Anyway, I get help about this from a non-newbie. I am still quite newbie :).

Best wishes,
Michael

---

