---
title: "Ubuntu-Macbook switch"
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by erictm on 2009-03-13
I recently downloaded and installed Ubuntu to my macbook version 3,1 and I'm having an issue. I've read through the forums but couldn't find an my particular issue albeit is most likely an easy one to fix.

I burned Ubuntu to a cd and after partitioning my macbook. I installed Ubuntu on my local disk and then repartitioned it all so that macosx is no longer on my macbook. 

The problem I'm running into is that in order to boot into Ubuntu I have to have my ubuntu disk in and boot from the cd and then using the boot menu boot from local disk one. If I start up my macbook without the cd in it takes me to a grey screen with just a flashing folder icon with a ! in it. Anyways, I was wondering what I needed to do in order to get my macbook to boot directly into Ubuntu instead of trying to boot up a non-existent macosx or if it is even possible. 

Thanks for your help.

---

### Post by cyberdork33 on 2009-03-13
> **erictm said:**
> I recently downloaded and installed Ubuntu to my macbook version 3,1 and I'm having an issue. I've read through the forums but couldn't find an my particular issue albeit is most likely an easy one to fix.

I burned Ubuntu to a cd and after partitioning my macbook. I installed Ubuntu on my local disk and then repartitioned it all so that macosx is no longer on my macbook. 

The problem I'm running into is that in order to boot into Ubuntu I have to have my ubuntu disk in and boot from the cd and then using the boot menu boot from local disk one. If I start up my macbook without the cd in it takes me to a grey screen with just a flashing folder icon with a ! in it. Anyways, I was wondering what I needed to do in order to get my macbook to boot directly into Ubuntu instead of trying to boot up a non-existent macosx or if it is even possible. 

Thanks for your help.

Create a refit CD:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

boot from it and make sure the partition tables are in sync with the partition tool.

You then may need to reinstall grub to the MBR, or use Grub-EFI to boot Ubuntu.

---

### Post by erictm on 2009-03-13
Done. Held the option button to boot in the rEFIt menu but I only got a mouse cursor and nothing has loaded as of yet.

---

### Post by cyberdork33 on 2009-03-13
> **erictm said:**
> Done. Held the option button to boot in the rEFIt menu but I only got a mouse cursor and nothing has loaded as of yet.

unplug uneeded USB devices.

---

### Post by erictm on 2009-03-13
I don't have any plugged in.

---

### Post by cyberdork33 on 2009-03-13
> **erictm said:**
> I don't have any plugged in.
Did you let it sit there for awhile?

The EFI firmware is searching for an efi executable. Since there is not one when you are single-booting, it creates a long delay. This can be shortened by blessing the Linux partition (See Stickied FAQ).

I'd try to fix the partition tables first though. Maybe the disc is not reading well?

---

### Post by erictm on 2009-03-13
I let it sit while I took a shower and it still hasn't loaded anything yet.

---

### Post by cyberdork33 on 2009-03-13
> **erictm said:**
> I let it sit while I took a shower and it still hasn't loaded anything yet.
OK other method:

boot into Ubuntu and install 'refit' this will allow you to use the gptsync command.

---

