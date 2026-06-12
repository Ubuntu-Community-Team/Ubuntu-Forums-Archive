---
title: "Ubuntu doesn't recognize Windows 8 partition while installing - Asus S56"
date: 2013-08-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by magneto538 on 2013-08-29
Hi you all,
I understand that this kind of issue has been discussed here a lot of times, but I am still not able to figure it out just by following the guides I've found.

I own an **Asus S56CM **and I need to set it up with two OSs, Windows 8 and Ubuntu. I am not able to do so because **Ubuntu doesn't recognize any Windows partition while installing**. On my old PC it was so damn easy, I just had to plug in my bootable USB key and click on "Install Ubuntu alongside Windows 8", but now this doesn't even show up. I even tried to create Ubuntu partitions manually, but I got a bit confused as I couldn't create any extended partition (I think this is due to the fact that my motherboard is UEFI), as I used to do before. 

The fact is that I see no way to install both the OSs on my machine, nothing I've tried worked, including all the guides I've found here on the forums and on Ubuntu official websites (and most of the times they blew everything up and I had to reinstall everything).

If you need any further information, I can say that my BIOS (if needed...) is an American Megatrends, version 205.

Hope someone can help, I really need this to get this fixed soon.

Thank you all.
D

---

### Post by oldfred on 2013-08-29
Is this an Ultrabook? Then it has Intel SRT which uses RAID and the desktop installer does not have RAID drivers.
Best just to turn off Intel SRT, and remove RAID meta-data from drives. You can re-implement the Intel SRT and it will work if you are primarily a Windows user. Some install Ubuntu to SSD and not use SRT.

For more details on Ultrabook issue see link in my signature.

Other Asus, may be similar?
       Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

---

### Post by magneto538 on 2013-08-29
Sorry, I didn't understand what I have to do. How do I turn off Intel SRT? And what should I do with RAID? I wouldn't like to install anything on the SSD, as it seems to be full of other things that, I guess, may be very important for the system. I don't know however.

---

### Post by oldfred on 2013-08-29
I have lots of details which I would rather not just repeat in link in my signature.

With an Ultraboot you have three main issues that are not directly related. UEFI which is new and has secure boot, Intel SRT which uses RAID and must be removed, but can be reimplemented and dual video with nVidia usually the default so you need nomodeset.

the Intel SRT should be similar but may not be identical for your system.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

    




And it is best to understand a little about each issue, although we can just give commands to make all the changes. But it seems each vendor implements UEFI and other features slightly different so exact process cannot be posted unless someone has your vendor & model system.

---

