---
title: "Macbook pro lately 2013 - Triple Boot - Ubuntu 32 bits ?"
date: 2014-04-01
forum: Apple Hardware Users
---

### Post by souldream on 2014-04-01
Hello,

I just get a new macbook pro, and i try to do a triple boot for my work.

Actually, i have some prob to understand really how works the Hybrid partition schemes ( GPT , MBR ... ).

I try to do in this step :

1) Installaing MacOS fresh install
2 ) Installing bootcamp => half size of the SSD ( 128 gb )

As i can not resize the bootcamp, i need to resize the mac osx partition.

Problem is one partition is hidden ( recovery ).

So if someone have a working HowTO , step by step to make tri-boot with Linux 32 bits.

I try either to install 32 bits version but i get some problem with grub loading after installation.

regards

---

### Post by oldfred on 2014-04-01
I do not know Mac.

But 32 bit Ubuntu does not have any UEFI support, you need the 64 bit version which if a new computer you should be using anyway.

Because Windows has to boot from BIOS mode (why?), you have to use hybrid mode. That syncs the first 4 gpt partitions with 4 primary MBR partitions. You must be careful to maintain that sync
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Some links that may be helpful

 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
      
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)
Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)
New Haswell MacBook Air - several issues
[http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1)

---

### Post by Mk32 on 2014-04-02
I have tried to do this before on a Intel Mac mini. 

Windows XP (at the time), Ubuntu 10.04LTS and OS X. 

You'll want rEFIt. I couldn't get it all working. I found that Windows and Linux at the same time don't get along very well on a Mac. I also found the practical limit was 3 OSs because of the hybrid bootloader, the MBR has only four slots. One is taken up by default. (I wanted to run 10.4 Tiger, 10.5 Leopard, Windows XP and Ubuntu. Didn't work.) Avoid using BootCamp to resize the partitions: better is to sort that all before hand with Disk Utility booted off a CD drive -- if that is possible. If not then you'll have to use GParted. 

Install Mac OS X first, then Windows, then Linux. I also wouldn't do this on a 128GB SSD. Too small for that stuff. I will reckon you're using Windows 7, which is a gigantic OS. After a fresh install + updates to SP1 I saw 20GiB gone *just for the OS*. In my experience, OS X 10.5 Leopard wants about 10GiB just for itself, Debian Linux will eat up 8GiB easily, so you can see why I don't recommend it because then you'll be down to about 60-70GiB for your data.

You can run Linux off a USB thumbdrive. It'll be slower, but it depends on what you want to do. I suppose you could help that by going to Andantech or someplace like that and try and find the fastest USB 2.0 thumbdrive you can get. You'll still need rEFIt.

---

### Post by este.el.paz on 2014-04-04
Gents:

I'll keep this to a minimum, since the conversation here is like that.  I have a triple boot set up on my '10 MBPro; the data from rodbooks is helpful, but what you need for anything after Mountain Lion is "rEFInd" . . . rEFIt only works up to Sno Leopard.  I don't know if you need "gdisk" for rEFInd . . . I installed it for rEFIt when I was using the rodbooks suggestion to use Boot camp, and when I changed to rEFInd I didn't re-install it.  But like you seem to have found BC seems to lock the HD and doesn't let any further partitions go on.  I had to wipe the HD and start fresh using DU to set up the partitions--I now can boot 10.6.8., 10.8.x, and LM 16 . . . each in their own partition.

A buddy of mine recently started using linux in a chromebook and found that using "wine" lets him run specific windows apps . . . w/o installing Windows; which as the other poster mentioned, would use up a lot of space.

e.e.p.

---

