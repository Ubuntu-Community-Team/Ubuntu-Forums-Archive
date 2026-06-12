---
title: "Encrypted Ubuntu"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by offthewall on 2007-09-06
Hi All,

I work as a consultant handling medical and insurance data and need to protect the files on my computer using whole disk encryption. The limited encryption offered by OS X (File vault, encrypted disk images) is not enough: I would prefer the entire operating system: boot partition, swap partition, user partition etc to be encrypted)

This link: [http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)  shows how to install an encrypted version of Ubuntu 7.04, but it is not specific to Intel Macs.

Does anyone have experience with installing and booting an encrypted Ubuntu operating system on an Intel Mac? 

Any suggestions or advice would be appreciated.

Thank you.

-offthewall

---

### Post by kidders on 2007-09-08
Hi there,

I know this doesn't directly answer your question ... sorry for that ... but you've gone a whole day without a response, so I thought I'd at least *try* to help out.

Having never done this on a Mac, I can't be sure, but I imagine the only Mac-specific encryption-related problem (if any) you might encounter would be *booting* off an encrypted filesystem. On any box, overdoing your filesystem encryption has a number of disadvantages...[LIST]
[*]The greater the number of filesystems you encrypt, the greater the probability that at least one of them will be damaged at some point, in the course of normal usage. Encrypted filesystems are unusually vulnerable to corruption, and can be extremely difficult to recover.
[*]Arranging to boot from an encrypted filesystem is awkward, and where there is no advantage, it's just not worth it.
[*]Accessing encrypted data is (obviously, I suppose) significantly slower than accessing unencrypted data. Encrypting system files will slow down everything you do on your box.[/LIST]Anyhow, there are many situations in which encrypting an *entire* Linux system is essential ... eg commercially sensitive servers, and so on. In your case, however, a convincing argument could be made in favour of encrypting /home and your swap space only, by tempting you with easier long-term management, better performance, lower susceptibility to disasterous corruption, and a less convoluted initial setup.

In your situation, I would give serious consideration to something like this...[LIST]
[*]Encrypting /home.
[*]Configuring your box to look for its decryption key on a USB flash disk at boot time, so you can use very complex keyphrases.
[*]Setting up on-the-fly swap encryption using random keyphrases.
[*]Considering purchasing extra RAM, and mounting certain parts of your system (eg /tmp) into it, for security purposes.
[*]Offset corruption risks by periodically dumping your encrypted /home onto DVD, or some similar approach.[/LIST]Basically, only the things your box *doesn't* have in common with every other Linux box on the planet (ie your personal files & any temporary data created by your applications that may be security-sensitive) would be protected. One major advantage of this sort of approach is that both Linux and OSX will happily let you do this, and in much the same way ... so you get your choice of OS back.

Anyhow, if you'd prefer to go the whole hog, and encrypt your entire system, it would surprise me if the simple fact of having a Mac made too much difference to how it's done. I'll happily do a little poking around, just to be sure though.

---

### Post by sunbird on 2008-03-27
I'm bumping this thread. I'm downloading 7.10 alternate in the hopes that the partitioner allows encrypted setup in manual partitioning mode. I want to keep a small OS X partition for firmware upgrades. I'm not sure that the manual partitioner will allow me to do so if I want encryption.  Does anyone know?

---

### Post by mrsteveman1 on 2008-03-27
You want the alternate installer CD, and yes it will work fine on a Mac.

The only part of the system that the Mac firmware needs to care about is the boot partition that Ubuntu will create when you setup the encryption during the install. After that boot partition is loaded things work just like any other computer.

Are you going to leave OS X on the machine? If so be careful not to let the ubuntu installer use the whole disk, because it will wipe os x off the machine. You can do the partitioning manually and still get the encryption setup.

If you are just going to wipe OS X off the machine it shouldn't be a problem, just let the ubuntu installer do whatever it wants.

---

### Post by sunbird on 2008-03-27
Thanks. I've been DL'ing the alternate CD via BT for over a day now (really slow connection) and it's almost done! I'm going to keep the OS X partition for firmware upgrades.

---

### Post by sunbird on 2008-03-27
Hmmm.... I can't seem to get this to work.

I'm on the partitioner in the alternate 7.10 x64. here's my partition map:

SCSI 3 (0,0,0) (sda) - 120.0 GB ATA FUJITSU

   3.1 kb       FREE SPACE
   209.7 MB  fat 32              EFI System P /media/EFI
   11.8 GB    hfs+                Apple_HFS
   134.2 MB  FREE SPACE
   107.9 GB  UNTITLED 2
   3.6 kB       FREE SPACE

I deleted the last partition, and tried to set it up like this:

  3.1 kb       FREE SPACE
   209.7 MB  fat 32              EFI System P /media/EFI
   11.8 GB    hfs+                Apple_HFS
   103.6 GB  crypto             not active
   4.4 GB      swap

But it says that I don't have a mount point for /.

I don't know how to create a mount point without creating an unencypted partition.

Can anyone help?

**Edit:** Never mind! I found [this post]("http://ubuntuforums.org/showthread.php?t=582406"), which has a handy step-by-step. I'll post my pics of the setup for Mac OS dual-boot here once it's done.

---

### Post by cyberdork33 on 2008-03-27
Also, don't mount the EFI partition.

---

### Post by sunbird on 2008-03-27
I got it all working. I've taken some photos and will do a how-to for other noobs soon.

**EDIT:** Done! The how-to is [here]("http://ubuntuforums.org/showthread.php?t=737964") in case anyone else wants to go this route.

---

