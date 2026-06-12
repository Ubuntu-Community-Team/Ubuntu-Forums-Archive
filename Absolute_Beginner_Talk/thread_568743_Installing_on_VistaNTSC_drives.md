---
title: "Installing on Vista/NTSC drives"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Lee7 on 2007-10-06
Hi all,

I want to install Ubuntu 7.04 on a seperate hard drive to Windows Vista. I would need to partition my second drive so Ubuntu can utilise some of it, but not all - my films and music are on there, too. I've heard  I should use grub for boot managing, but I'd prefer to partition my second hard drive in Vista and then install Ubuntu there. 

If I install Ubuntu on the partition, will my computer recognise both OS versions and ask me which to boot to? I want to keep Vista as my primary boot drive and have the option to boot to Ubuntu. Because I have data on my second hard drive, I won't lose this data if I partition the free space in Vista for Ubuntu? The data is backed up on a third hard drive just in case, however.

Both hard drives are SATA2 + NTSC, will this be a problem?

Thanks for any help.


_System Specs_

Intel Core Duo E6600 (2.4GHZ x2)
2GB DDR2 RAM
x1950 PRO 512MB
Asus PK5 motherboard
Logitech G15 keyboard and Revolution MX mouse

---

### Post by CAD-MAN on 2007-10-06
> **Lee7 said:**
> Hi all,

I want to install Ubuntu 7.04 on a seperate hard drive to Windows Vista. I would need to partition my second drive so Ubuntu can utilise some of it, but not all - my films and music are on there, too. I've heard  I should use grub for boot managing, but I'd prefer to partition my second hard drive in Vista and then install Ubuntu there. 

Partitioning the drive should be no problem. The Live CD comes with its own partitioning tool that will allow you to arrange both of your hard drives during the installation process. It is recommended that you defrag any Windows partitions if you want to resize them though.

> **Lee7 said:**
> 
If I install Ubuntu on the partition, will my computer recognise both OS versions and ask me which to boot to? I want to keep Vista as my primary boot drive and have the option to boot to Ubuntu. Because I have data on my second hard drive, I won't lose this data if I partition the free space in Vista for Ubuntu? The data is backed up on a third hard drive just in case, however.

Both hard drives are SATA2 + NTSC, will this be a problem?

Thanks for any help.


_System Specs_

Intel Core Duo E6600 (2.4GHZ x2)
2GB DDR2 RAM
x1950 PRO 512MB
Asus PK5 motherboard
Logitech G15 keyboard and Revolution MX mouse

Installing Ubuntu will also install a boot manager, called  GRUB which will allow you to choose which OS you want to boot into from a list. I don't know how it reacts to more than one physical hard drive, however. I shouldn't think it would have any problems, but it would be better to wait and see if someone who has experience with GRUB and more than one HD to answer though ;)


P.S. I don't know what SATA2 is like on Ubuntu, Im on SATA, and it is no problem for me.

---

### Post by luisromangz on 2007-10-06
You seem a bit confused. Grub will not make the partitions, Grub is the boot manager, so it will handle the selection between OSes at boot-time.

You can partition your drive with the program you choose. I recommend you not creating a partition for Ubuntu, but just to leave some free space avalaible in the hard drive, so you can tell Ubuntu's installer to use that free space, and it will create the needed partitions (yeah, at least too, one for swap and a regular one, that's why you shouldn't create one partition for Linux).

About if the kind of drives might be a problem, I don't know.

---

### Post by 505 on 2007-10-06
To make a new partition you need a partition manager. If you want to do that from within Windows you need an extra program. I believe you can also do that from the Ubuntu live CD without installing an extra program. Making another partition should leave your data intact, but a backup is always wise. With such partition managers, do not make a new partition, just make free space. Ubuntu will split the free space in a normal partition and a swap partition. It's better to let the installer do that, than do it yourself.

Just install Ubuntu on the free space and you should be fine. It will install Grub to manage booting, and it will recognise Vista. It might set Vista as the second choice to boot, but that can be changes very easily.

---

### Post by por100pre1 on 2007-10-06
Try [this]("http://ubuntuforums.org/showpost.php?p=3412810&postcount=3"). This method will keep Windows Bootloader.

---

### Post by Duck2006 on 2007-10-06
[http://www.freewarefiles.com/program_2_219_21892.html](http://www.freewarefiles.com/program_2_219_21892.html)

---

### Post by Lee7 on 2007-10-06
Thanks for the replies.

If I happen to dislike Ubuntu and wish to uninstall, will Grub automatically be removed and use Vista's boot manager again? Meaning that Vista will always boot up. If so, I'll go ahead and install Ubuntu today. :)

---

### Post by Duck2006 on 2007-10-06
> **Lee7 said:**
> Thanks for the replies.

If I happen to dislike Ubuntu and wish to uninstall, will Grub automatically be removed and use Vista's boot manager again? Meaning that Vista will always boot up. If so, I'll go ahead and install Ubuntu today. :)

If you install grub to the MBR you will have to remove grub.
if you use BCDEasy, and remove ubuntu you will be able to remove BCDEasy from vista

---

### Post by Lee7 on 2007-10-06
Okay, I have the live CD loaded.I was installing it, and it failed on installing GRUB. It said "A fatal error occurred", and canceled the installation. It said something about (hd0) I believe. The whole partition area is a little confusing - I was only able to select a root partition, and couldn't then place another partition on that hard drive for swap. Am I doing something wrong?

---

### Post by por100pre1 on 2007-10-06
> **Lee7 said:**
> Thanks for the replies.

If I happen to dislike Ubuntu and wish to uninstall, will Grub automatically be removed and use Vista's boot manager again? Meaning that Vista will always boot up. If so, I'll go ahead and install Ubuntu today. :)

No. Do as I posted, install GRUB in Ubuntu partition just before installing Ubuntu. When finished login to Vista and add Ubuntu to Windows Boot loader with Easy BCD.

---

### Post by Lee7 on 2007-10-06
> **por100pre1 said:**
> No. Do as I posted, install GRUB in Ubuntu partition just before installing Ubuntu. When finished login to Vista and add Ubuntu to Windows Boot loader with Easy BCD.

I've read your post, but how do I specify to install GRUB in root partition during Ubuntu installation?

---

### Post by Lee7 on 2007-10-06
I had another go at the installation, and successfully installed it.

However, when I boot up the computer GRUB returns "error 22" when trying to load... which means I cannot boot up Vista or Ubuntu.

Any help would be greatly appreciated.

---

### Post by por100pre1 on 2007-10-06
Check if [this]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html") helps. Sorry for my delay. :(

---

### Post by Lee7 on 2007-10-06
> **por100pre1 said:**
> Check if [this]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html") helps. Sorry for my delay. :(
Ok, but: A) How will I make sure I do not receive this message next time I install Ubuntu? and B) That site says he was deleting the lInux partition, but I haven't. So is this the only way to fix the boot issue - what about removing GRUB?

---

### Post by por100pre1 on 2007-10-06
Go ahead and install Windows MBR, at this time your files are more important than the unused Ubuntu installation. Use the Live CD to delete the Ubuntu partition and swap. Install Ubuntu again but at the last step, just before install click **Advanced** and then select to install GRUB in the Ubuntu installation (in your case it should be **hd(1,1)** meaning second disk, second partition; number 0 is first one). After installing login to Vista and install EasyBCD to add Ubuntu to Vistas MBR.

---

### Post by Lee7 on 2007-10-06
> **por100pre1 said:**
> Go ahead and install Windows MBR, at this time your files are more important than the unused Ubuntu installation. Use the Live CD to delete the Ubuntu partition and swap. Install Ubuntu again but at the last step, just before install click **Advanced** and then select to install GRUB in the Ubuntu installation (in your case it should be **hd(1,1)** meaning second disk, second partition; number 0 is first one). After installing login to Vista and install EasyBCD to add Ubuntu to Vistas MBR.

Thank you, por100pre1. I'll give a lowdown of my hard drives just so I know hd(1,1) is correct.

C:/ (Windows)
L:/ (Linux partition - 50GB, swap has roughly 1-3GB)
M:/ (Files - films, music, etc)

I assume it is still hd(1,1)? Is the swap partition large enough?

---

### Post by por100pre1 on 2007-10-06
Do you want to install Ubuntu in your second hard disk? I want to be sure.
When I mean hd(1,1) it actaually means disk two, partition two** of that disk**. I think you posted that you have a partition with files in the second disk already, that should be hd(1,0)

---

### Post by Lee7 on 2007-10-06
> **por100pre1 said:**
> Do you want to install Ubuntu in your second hard disk? I want to be sure.
When I mean hd(1,1) it actaually means disk two, partition two** of that disk**. I think you posted that you have a partition with files in the second disk already, that should be hd(1,0)
Yes, I want to install Ubuntu on my second hard drive. I've set a partition (50GB) for Ubuntu, which is called U:/ for Ubuntu. So the rest of the space on that drive is left over for L:/ - technically just one partition is on the drive?

I hope I haven't confused you. :(

---

### Post by por100pre1 on 2007-10-06
> **Lee7 said:**
> Yes, I want to install Ubuntu on my second hard drive. I've set a partition (50GB) for Ubuntu, which is called U:/ for Ubuntu. So the rest of the space on that drive is left over for L:/.

I hope I haven't confused you. :(

I'm leaving so I just want to make sure everything is ok. Keep in mind that the first partition you set up in the second hard drive is hd(1,0); if it is Ubuntu then GRUB should be installed to hd(1,0). Now it is up to you. :)

---

### Post by Lee7 on 2007-10-07
> **por100pre1 said:**
> I'm leaving so I just want to make sure everything is ok. Keep in mind that the first partition you set up in the second hard drive is hd(1,0); if it is Ubuntu then GRUB should be installed to hd(1,0). Now it is up to you. :)

Well, I tried to install to "hd(1,1)" and it failed. I'll go ahead and restore Windows boot manager and then try installing GRUB again, but I really need to know where to install GRUB.

I install it to the root partition, not swap or boot? My second hard drive has three sections, but I specify two partitions.

Storage (450GB)
Root partition (45GB)
Swap partition (5GB)

So "hd(1,1)" should work? This hard drive is in SATA port 2 slot, so I'm guessing it is the second hard drive. ;)

Cheers for the help, hopefully I'll be on it tonight (getting my Vista installation disk sent up).

---

### Post by por100pre1 on 2007-10-07
> **Lee7 said:**
> Well, I tried to install to "hd(1,1)" and it failed. I'll go ahead and restore Windows boot manager and then try installing GRUB again, but I really need to know where to install GRUB.

I install it to the root partition, not swap or boot? My second hard drive has three sections, but I specify two partitions.

Storage (450GB)
Root partition (45GB)
Swap partition (5GB)

So "hd(1,1)" should work? This hard drive is in SATA port 2 slot, so I'm guessing it is the second hard drive. ;)

Cheers for the help, hopefully I'll be on it tonight (getting my Vista installation disk sent up).

Did you use [EasyBCD]("http://neosmart.net/dl.php?id=1") in Vista to add Ubuntu to Vista's boot loader? That should be done after Boot should be installed in the Root partition. If the root partition is the first one that you setup then it should be hd(1,0). :-k

---

### Post by Lee7 on 2007-10-07
Okay, I have 50GB of unallocated space in Vista. I'll let Ubuntu installation partition the stuff.

45GB of it will be /, 5GB will be /swap. Is that sufficient or do I need to add a /boot partition?  I'll make sure GRUB installs to the 45GB root partition, which is partition #2 - hd(1,1).

The confusing part for both of us is that I have 450GB worth of space ready for storage on the same drive that Vista/Ubuntu can use, that is classed as primary partition in Vista, so partition #1.

---

### Post by Lee7 on 2007-10-07
Hmm, GRUB fails when installing to hd(1,1). I'm kinda unsure as to what to try next.

---

### Post by Lee7 on 2007-10-08
I've managed to get GRUB installed in the root partition under boot. I select the root partition in EasyBCD and restart... once choosing to boot to Ubuntu it keeps "loading new partition" over and over. What's going wrong?

---

### Post by Lee7 on 2007-10-08
> **Lee7 said:**
> I've managed to get GRUB installed in the root partition under boot. I select the root partition in EasyBCD and restart... once choosing to boot to Ubuntu it keeps "loading new partition" over and over. What's going wrong?
I've fixed that issue, but it now says it cannot load the partition on the hard drive. :(

I've even started on a fresh hard drive and I still can't resolve this problem. I used guided mode to install on a hard drive, and it created a root partition, swap and extended. I tell EasyBCD to boot the root partition but it doesnt work.

---

