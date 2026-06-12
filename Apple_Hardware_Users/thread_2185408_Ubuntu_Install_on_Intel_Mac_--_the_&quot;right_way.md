---
title: "Ubuntu Install on Intel Mac -- the &quot;right way&quot;"
date: 2013-11-02
forum: Apple Hardware Users
---

### Post by xmbwd on 2013-11-02
Hi all.  So I have tried to install Ubuntu on my iMac as a dual-boot system (though I may be soon moving to a VM setup, if this post yields no results).  I got Ubuntu to work, but I can't get it to load through rEFInd (I will put my entire setup at the bottom of this post, but I'm on 2011 iMac).  My problem, and my questions are: 


[LIST=1]
[*]**what to do if the Super Grub 2 Disk does not find an Ubuntu installation -- so the rEFInd boot loader does not show one either? ** 
[*]i**s there an actual "right way" to install Ubuntu (13.10) on a Mac?** 
[/LIST]

I ask the second question because there are a number of guides, and they all differ slightly.  Here are a few (the first two appear to be the best):[INDENT]
[http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)
[https://help.ubuntu.com/community/ubuntuprecisequantalon2011imac](https://help.ubuntu.com/community/ubuntuprecisequantalon2011imac)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
[http://tech-devnet.blogspot.de/2012/05/running-ubuntu-1204-on-mac.html](http://tech-devnet.blogspot.de/2012/05/running-ubuntu-1204-on-mac.html)
[http://www.thatsthewayyoudoit.me/2013/04/how-to-install-ubuntu-1304-on-macbook.html#!/2013/04/how-to-install-ubuntu-1304-on-macbook.html]("http://www.thatsthewayyoudoit.me/2013/04/how-to-install-ubuntu-1304-on-macbook.html#%21/2013/04/how-to-install-ubuntu-1304-on-macbook.html")
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
[http://www.noah.org/wiki/Ubuntu_install_on_Apple_Mac_Intel_hardware](http://www.noah.org/wiki/Ubuntu_install_on_Apple_Mac_Intel_hardware)
[/INDENT]

The primary difference between these directions appears to be:  1) whether to create just a "/" root partition and a swap partition -- versus -- creating a "/" root partition, a "/home" partition, a "boot" bios partition, and a swap partition; and 2) where to "Set the device for bootloader installation" on the Ubuntu install disk -- at the /dev/sda (i.e., the root of the entire hard drive that includes all partitions, including Mac OSX) or at the "/" root partition.  

I have tried as many combinations of this as I care to for now.  At the end of the day, I was able to get Ubuntu installed and rEFInd working, but the Super Grub 2 disk could not find any Grub installations when I selected "GRUB 2 installation (even if MBR is overwritten)."  As a result, the rEFInd bootloader does not "see" Ubuntu, and the only way for me to boot into Ubuntu is to load the Grub disk and select "show all available os," as which point it shows a Linux OS, and I can boot into Ubuntu (which works great once I'm in).

[COLOR=#b22222]**Does anyone know how to fix this problem?**[/COLOR]  [COLOR=#b22222]**Please . . . . **[/COLOR] I *think* it must be something to do with where my Ubuntu configuration has Grub.  Accordingly, at the bottom is a pic of my Grub folder in Ubuntu.  

Thank you for any help!!  

Here is my current setup (though please note I also tried the way with a "/boot" partition and a "/home" partition -- they did not work at all (i.e., I could not boot into Ubuntu even from the find any os menu of the Super Grub 2 Disk).  I believe, though I am not sure, that when I used that approach, I set the bootloader installation at the /dev/sda level instead of "/" root AND, in a separate install, I set it at the "/boot" partition.  Neither worked.   The below DID WORK for Ubuntu and for getting into rEFInd, but not for Super Disk 2 recognizing the Ubuntu Grub installation:

   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                               *1.0 TB     disk0
   1:                        EFI EFI                                   209.7 MB   disk0s1
   2:                  Apple_HFS Cypress iMac                907.3 GB   disk0s2
   3:                 Apple_Boot Recovery HD                650.0 MB   disk0s3
   4: 0FC63DDF-8483-4772-8F89-3D69D8477FE4     63.5 GB    disk0s4
   5:                 Linux Swap                                       6.6 GB     disk0s5
   6:                  Apple_HFS Lion                               21.7 GB    disk0s7

*There are two Mac partitions (Cypress iMac and Lion).  Ubuntu is at the /dev/sda4, and I have no idea why that long code is there for the TYPE NAME.

**Mac:**

iMac 27-inch mid-2011
Processor:  2.7 GHz Intel Core i5
4 GB DDR3
AMD Radeon HD6770M
Running 10.9 (Mavericks)

**Grub folder on Ubuntu install:**

[IMG]https://dl.dropboxusercontent.com/u/13392425/Screenshot%20of%20boot_Grub.png[/IMG]

---

### Post by pacome.heuze on 2013-11-04
Yes it could be nice to make a one thread for imac installation.
 i've got a mac 7.1 and i've got ubuntu and what i did is that i installed mac osx and then ubuntu studio 13.10.
for now i have to presse the alt button at the start of mac and i'm stuck there.
I don't use mac osx for now ...

I've first installed ubuntu 12.10 and then i just upgrade to 13.10. i did it twice and twice it worked.

---

