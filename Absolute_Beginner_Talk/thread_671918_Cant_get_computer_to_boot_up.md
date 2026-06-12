---
title: "Cant get computer to boot up"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by dc2610 on 2008-01-19
I accidently erased ubuntu from my hard drive. I have an Acer laptop that I had ubuntu and vista running on it. I was trying to repartition two partitions I made when I was following the directions to install ubuntu but I ended up deleting ubuntu from the hard drive instead.  

Now when I try to boot up my laptop I get this message: 
GRUB loading, please wait...
Error 17
And my computer just hangs there. 

How can I get ubuntu off my computer and log into windows vista?

---

### Post by Bigbluecat on 2008-01-19
You will need to restore Vista's MBR (Master Boot Record). 

The MBR resides right at the start of the boot HDD. In essence it points to the location of the rest of the boot files.

When you installed Ubuntu it instaleld the GRUB boot loader to the MBR and pointed to a file on your Ubunutu partition to manage the rest of the boot process. Now that you have removed Ubuntu you need to reverse the changes to the MBR.

I have only done this with XP and believe there are a few differences with Vista. Found the following ink which may help:

> [http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

---

