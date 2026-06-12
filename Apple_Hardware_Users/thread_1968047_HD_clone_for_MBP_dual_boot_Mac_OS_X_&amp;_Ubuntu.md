---
title: "HD clone for MBP dual boot Mac OS X &amp; Ubuntu?"
date: 2012-04-28
forum: Apple Hardware Users
---

### Post by bravegag on 2012-04-28
Hello,

After tons of work setting up the dual boot environment to my heart's content, is there an easy way to clone my full SSD disk as is including all configurations, partitions, Boot partitions etc into an image that can be brought back to any new free size disk I wish to buy in the future? 

What I have is Ubuntu and Mac OS X in dual boot, and of course I use still Time Machine but that only includes the Macintosh HD bit and not the rest of the disk or?

I have virtually all disk management software (Drive Genius, Disk Warrior, etc etc) for Mac but none seems to implement this simple task ...

TIA,
Best regards,
Giovanni

---

### Post by jimihendrixhewasgood on 2012-05-24
Hi Giovanni,

I am currently working on this same problem with Mac 10.6, Win7 and Ubuntu. I am working with clonezilla to save images of the partitions then re-loading them to a second machines with the same partition structure and using rEFIt to arrange the loading. So far I have managed to take images of the existing tri-boot machine and reload the images onto a second machine, but I have not successfully booted into Win7 or Ubuntu yet. I was hoping to simply clone the entire drive with clonezilla but it does not recognize the  GUID partition scheme. I'll keep working on it and keep you posted!

Regards,
James

---

### Post by oldtechmage on 2012-05-29
I would definitely be interested in your progress.  I'm trying to clone xserve 3,1 nodes in my cluster.  I can use a couple of utilities such as dd.  It appears to clone correctly, but is not bootable.  Unfortunately, I can't try clonezilla as I don't have graphical support.  CLI only. =(
:popcorn:

---

