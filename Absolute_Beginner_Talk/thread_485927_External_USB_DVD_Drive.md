---
title: "External USB DVD Drive"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-06-27
I have an external usb drive that I want too boot DVD's from. However, it does noot boot from it and I don't know why. Can someone help me out? I really want to try some distro's that are available only in DVD's.

---

### Post by speaker219 on 2007-06-27
I don't think a computer will boot from an *external* drive connected via USB. Check the settings in your BIOS, but I doubt it will boot from an external DVD drive.

---

### Post by Inxsible on 2007-06-27
Your BIOS should be able to support booting from external devices if you want to do that.

You can try downloading some updated bios for your hardware...but be careful doing that.

---

### Post by logos34 on 2007-06-27
> **izizzle said:**
> I have an external usb drive that I want too boot DVD's from. However, it does noot boot from it and I don't know why. Can someone help me out? I really want to try some distro's that are available only in DVD's.

Even if your BIOS does not support USB boot and there's no update that will add this feature, there is a workaround to get that optical drive to boot using a floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by izizzle on 2007-06-27
Oh well...I guess I can try the DVD's when I get an internal DVD drive......sometime in my life..... and it'll have lightscribe :D LOL

BTW, the link u gave me was too confusing.....so I gave up on it :(

---

### Post by logos34 on 2007-06-27
> **izizzle said:**
> Oh well...I guess I can try the DVD's when I get an internal DVD drive......sometime in my life..... and it'll have lightscribe :D LOL

BTW, the link u gave me was too confusing.....so I gave up on it :(

Are you kidding?  That's one of the more succinct Ubuntu howtos!  But here, since you're on linux (Feisty), try these notes I made to myself to make sbm floppy:

> Used sbm.bin (~1.4MB) file/image.  Wrote it to floppy on linux:

Copy 'sbm.bin' (~1.4MB) file from /install directory on ubuntu CD to /home/user directory
[B]sudo umount /media/floppy0
sudo mkfs.msdos /dev/fd0
cd /home/<user>/sbm.bin
sudo dd if=sbm.bin of=/dev/fd0
[/B]

Just substitute your user name in above. 

It works.

---

### Post by izizzle on 2007-06-27
How will this help me boot from an external USB drive?

---

### Post by logos34 on 2007-06-27
> **izizzle said:**
> How will this help me boot from an external USB drive?

If your bios does not support booting from usb devices you use this to add that capability...its a roundabout way of doing it...so you will boot to  your floppy drive (I forgot to ask does your lappy or desktop have one?) and you will be presented with a menu and the option to boot usb cdrom/dvd

---

### Post by izizzle on 2007-06-27
Oh ok, thanks for that info on how it works. I'll follow the steps you posted. Actually, i'm not at MY computer right now, so i'll try it later.
BTW, my desktop DOES have a floppy drive.

---

### Post by TorontoFish on 2007-08-30
> 
Quote:
[QUOTE]Used sbm.bin (~1.4MB) file/image. Wrote it to floppy on linux:

Copy 'sbm.bin' (~1.4MB) file from /install directory on ubuntu CD to /home/user directory
sudo umount /media/floppy0
sudo mkfs.msdos /dev/fd0
cd /home/<user>/sbm.bin
sudo dd if=sbm.bin of=/dev/fd0
Just substitute your user name in above.

It works. [/QUOTE]
I tried this, it didn't work. And I don't see how making a msdos filesystem will add USB drive support to SBM.

---

