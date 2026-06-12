---
title: "Triple boot Ubuntu (latest version)"
date: 2014-07-01
forum: Apple Hardware Users
---

### Post by carlito3 on 2014-07-01
HI sorry to bother you guys

I know there are many posts already on this topic but just wanted to ask before doing anything stupid
I'd like to triple boot my MBP (version 10.7.3) with ubuntu (one of the latest version).

i've had bootcamp already installed on my mac for a few years
so i just need to install ubuntu now. i've been reading this tutorial  but i'm not sure whether it is still applicable to the recent versions of  ubuntu [http://lifehacker.com/5531037/how-to...p-required/all]("http://lifehacker.com/5531037/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/all")

Should i still go ahead with this method or are there better ways of doing it nowadays? 


thank you in advance

---

### Post by oldfred on 2014-07-01
I do not know Mac, but that discusses 10.04 which was before UEFI.
You can boot Ubuntu with UEFI.

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
Boot Windows from Mac with UEFI. Long thread 2009 thru 2014 
[URL="http://forums.macrumors.com/showthread.php?t=696523"]http://forums.macrumors.com/showthread.php?t=696523

      [/URL]
 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

    [URL="http://forums.macrumors.com/showthread.php?t=696523"]
[/URL]

---

### Post by carlito3 on 2014-07-02
Thank you Oldfred i'm going to read about it and try and i'll get back to you if i need.

---

### Post by carlito3 on 2014-07-02
Hi again, i really need help because obviously something went wrong in the installation process.

After creating partitions on my Hard drive i downloaded rEFIt and manage to get it working. ( the rEFIt menu showed up as described in the tutorial)

I decided to reboot it again but this time the rEFIt menu had disappeared, and could only see the "macintosh hd" icon which i clicked on and the gray Apple logo appeared for a few minutes



I can only see now a 'no entry sign' progress indicator (spinning gear) 

I tried to reboot in safe mode and did not work. And cmd key+ S gave me the error message "still waiting for root device" ...

I just don't know what to do, can please someone help?

---

### Post by sudodus on 2014-07-02
Maybe these links can add some tips you need

[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Mac_OSX](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Mac_OSX)
and
[How to install Ubuntu on MacBook using USB flash drive]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")

---

### Post by carlito3 on 2014-07-02
Thanks for your help but i think that my laptop is just gone, all i can see no is the no entry sign with the spinning gear..

---

### Post by carlito3 on 2014-07-02
I managed to boot mac os again, but it seems that my mac os partition that i had created (now called 'disk0s2' ) needs to be repaired. 

The 3 other partitions are still there though ( linux, linux swap, bootcamp)

Wouldn't mind if someone could advise me on what is going on

---

