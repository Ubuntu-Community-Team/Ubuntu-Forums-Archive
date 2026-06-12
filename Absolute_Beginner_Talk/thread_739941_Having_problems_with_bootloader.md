---
title: "Having problems with bootloader"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by j0natz on 2008-03-30
Hi there, 

I tried to search but I could not find any good help. 

I'm having a problem whith booting of Ubuntu.

Mainly I'm running Vista SP1 on a RAID 0 (Sata II Raid)

I'm having some old 300 GB Pata Drive which has 30 GB free. Booting Ubuntu with the on the CD included Wubi stuff works perfekt. When I install it permanently on my Harddrive I tried both:

Install GRUB --> Won't work and will kill my Vista Bootloader. 

Or I choose to don't install anything and hope Wubi will work. Actually it did work once but I've tried to much stuff and thought I'll reinstall Ubuntu once more to have a clean one. Since that I can't boot it anymore. 

When I try to boot Ubuntu without the USB stick plugged in there's something showing up which is calles "Busy Box". I have no clue what I should do with it...

Can somebody help me how to fix this? I'm having those problems for a pretty long time now... I really  would like to use some Linux again but since I'm running RAID's I'm not getting it to work anymore :/

Hope sombody can help me...

Thanks in advance...

Best regards

Jonas

---

### Post by nonewmsgs on 2008-03-30
there have always been issues with pata and sata.

for some reason BIOS, GRUB, and linux all put your drives in another order.  you have to put GRUB on the first booting drive (instead of letting it automatically put it on the PATA).

then you're going to have to manually edit the GRUB tables for the order of the drives.  It's a bit of a pain but it works.

---

### Post by j0natz on 2008-03-30
W> **nonewmsgs said:**
> there have always been issues with pata and sata.

for some reason BIOS, GRUB, and linux all put your drives in another order.  you have to put GRUB on the first booting drive (instead of letting it automatically put it on the PATA).

then you're going to have to manually edit the GRUB tables for the order of the drives.  It's a bit of a pain but it works.

Will the first drive (Which is in Windows my Raid) be hd0?

Because if so, my Vista bootloader won't work anymore and Grub will tell me it has error 22.
I also get error 22 on some other distro's. (i.e. SUSE)

Could you help me setup Grub so it will work :)?

Br

Jonas

---

### Post by nonewmsgs on 2008-03-30
actually i belive it is hd(1)

i will help do my best to help you with this :)

---

### Post by j0natz on 2008-03-30
Allright, thanks for your help so far. I really appreciate this :)

Maybe this helps to show how my drives are recognized by windows?

I can also show a screenshot from gparted if this helps? I'm sorry but its in german but I guess you'll understand it somehow?!


link to picture (windows partition tool): [http://img528.imageshack.us/my.php?image=driveswindowspd1.jpg](http://img528.imageshack.us/my.php?image=driveswindowspd1.jpg) 
link to picture (gparted screenshot) [http://img144.imageshack.us/my.php?image=screenshotdevsdagparteduz9.png](http://img144.imageshack.us/my.php?image=screenshotdevsdagparteduz9.png)
On "Datenträger 0" which seems to be my first drive is the 18 GB partition which is ext3. The smaller one on "Datenträger 0" is the swap. 

So I should be able to install GRUB to hd0?!? If I do so, do I have to check the boot order in BIOS, right?
Edit: Didnt work

Will now try to install gparted do sda1 instead of hd0?

Best regards

Jonas

edit.: picture doesnt show?!

---

### Post by nonewmsgs on 2008-03-30
the picture shows fine.

ok: 
have you tried to install grub to hd(1)
sda1 is not what grub is looking for.  it seems to use a strictly numerical format.

---

### Post by Duck2006 on 2008-03-30
You can always try EasyBCD If grub don't work for you.

[http://www.freewarefiles.com/EasyBCD_program_21892.html](http://www.freewarefiles.com/EasyBCD_program_21892.html)

---

### Post by nonewmsgs on 2008-03-31
i am here along with the others.  whatever method you choose, we'll just be happy to get things straightened out again.

---

