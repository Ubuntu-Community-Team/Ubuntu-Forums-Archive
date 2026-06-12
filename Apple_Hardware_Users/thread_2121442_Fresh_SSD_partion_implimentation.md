---
title: "Fresh SSD partion implimentation"
date: 2013-03-01
forum: Apple Hardware Users
---

### Post by twinturbotom on 2013-03-01
Over the past few months I've learned enough to be dangerous with Ubuntu.  My 2008/2009 MacBook Air hard drive crashed, I installed a new SSD, and begun setting up this machine to support my personal data & various development efforts + testing out different OS's.
 
 I'm pretty sure I need to make changes and I'm researching + posting here to identify what they are.  The image below shows the existing setup.  Keys are, boot partition for chain loading / independant grub, potential for multiple OS's, personal files accessible by other OS's.  When setting this up I did recieve some errors about GPT and the ubuntu partioning tool kept creating 1mb unallocated regions at beginning and end of drive.

Proposed changes

[LIST=1]
[*]Change "bios_grub" partition to a primary ext4 and manually install grub2 
[*]Move FAT as primary partiion behind bios_grub 
[*] Swap after FAT (Signifying beginning of seconary logicals) 
[*] /boot after swap, this ensures all logical partitions are in consecutive order (I thought I set it up like that but was tired when I started). 
[*]Split up my / with a few partitions to support other Linux distros. 
[/LIST]

Summary of questions:

[LIST=1]
[*]Proposed changes make sense? 
[*]Proposed changes made without formating disk / loosing data? 
[*]How do I check if GPT is on the drive and should I be using that?
[LIST=1]
[*]Some handy terminal tools to trace booting and diagnose all may be helpful. 
[/LIST]
   
[/LIST]

 Image of existing Gparted below.  Any help or direction is appreciated; I want to be sure before moving forward and possibly boching things up worse! At a first glance GParted / partitioning tools don't appear to be flexible enough to allow me to make the changes I need without creating a new table from scratch an deleting everything :(  Thanks!
[ATTACH=CONFIG]239607[/ATTACH]

---

### Post by oldfred on 2013-03-02
Moved to Apple sub-forum.

I do not know Macs, but have some links. Macs use gpt and only have hybrid MBR/gpt to be able to boot Windows as a Mac does not use the newer version of UEFI that works with Windows or Ubuntu.

 Apple Macbook
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)

---

### Post by twinturbotom on 2013-03-02
Great info thanks.

---

