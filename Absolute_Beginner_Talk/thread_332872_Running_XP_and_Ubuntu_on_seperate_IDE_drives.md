---
title: "Running XP and Ubuntu on seperate IDE drives"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mit on 2007-01-06
I have searched the forum and google.  I also made a thread [here]("http://ubuntuforums.org/showthread.php?t=250824"), but this is now slighty different - I am trying to not have to re-install anything if possible! 
I have a desktop machine with 2 seperate IDE drives.  One has XP installed on it, and the other has 6.10

I don't need to share any files betweeen them, so planned to diable the less used drive in the BIOS and swop the boot order.  Seems a bit backwards, but I use XP more than Ubuntu due to work, but still like to be able to boot in to Ubuntu as and when I have a spare hour to learn.

The problem is, my BIOS won't disable and IDE drive - it keeps it on Auto, and the drive Ubuntu resides on isn't supported by service pack 2 and even though I have disabled it in device manager, it keeps trying to install everytime I restart the system.  I was thinking of creating a hardware profile and disabling the Ubuntu drive, so when it boots I can select that profile.

Am I going about this the completely wrong way - both OS are installed on the drives and work.  I would rather re-install 6.10 if needbe - we all know how long it takes to get an XP machine back up and running without imaging software! :-k 

Thanks for reading

Mit

---

### Post by bernied on 2007-01-06
Most people let the boot loader that's installed with ubuntu (called GRUB - GRand Unified Bootloader), do all this for them, and would think that you are doing this the hard way. This involves installing the grub MBR (master boot record - the first 512 bytes of a disk), also known as grub stage 1,  on the primary hard disk and the rest of grub (stage 2) somewhere else. This of course overwrites the Windows MBR, but that is pretty easy to fix especially if you took a copy of it before you did the grub install. This is by far the easiest thing to do.

However, some prefer to leave their precious/sensitive/distateful Windows install untouched so there are other ways you can do this, like:
- change the disk boot order in the bios (doesn't seem to work for you)
- create a boot floppy/cd/usb-flash-drive, which, when inserted before booting, brings up a boot menu, including your linux install (or you could make it so that it just started linux).

What do you think you'd like to do?

---

### Post by mit on 2007-01-06
Hi Bernie,

Thanks for your reply.

In all honesty, I do use the Windows platform more than Ubuntu.  :???:   

I agree that I have done this the hard way, and, ideally would like two seperate machines; one for Work and one for Ubuntu.

The reason this happend is because we have loads of machines where I work that are of identical hardware and when they are replaced/de-commisioned, the IT people get first refusal. :) 

Simply, I had two seperate operating systems running perfectly well on two seperate machines and then wanted to use them both from the same tower.  I did search the forum and googled it, but, perhaps missed what I was looking for. :-? 

Perhaps I need to look at imaging the both of them for data purposes and doing it the preferred way, i.e using GRUB to choose the desired OS.

Thanks for reading

mit

---

### Post by quartzy on 2007-01-06
I don't really get what you are trying to achieve but you do understand that you can write the MBR on one HDD, have that HDD load then then get the bootmanager to boot the OS on the other HDD?

You can do what [this]("http://ubuntuforums.org/showthread.php?t=332677") guy wanted so you don't even see grub.

---

### Post by mit on 2007-01-06
Hey, thanks! 

Regards

Mit

---

### Post by gn2 on 2007-01-06
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

