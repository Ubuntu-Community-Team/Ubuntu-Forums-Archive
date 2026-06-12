---
title: "Got ubuntu running but can't dual boot Windows 7"
date: 2013-09-03
forum: Any Other OS
---

### Post by weegeekus on 2013-09-03
First up, I will admit I have made a bit of a mess of things..

I have a Samsung NP900X3D ulrabook, it was running Windows 8 which I detested and had numerous problems with. I decided to try a dual boot of Windows 7 and Ubuntu (I have been an Ubuntu user in the past) but I seem to have made a mess of the partitions. I tried installing Windows 7 from a memory card but once I was asked what partition to install it on I was told "Windows cannot be installed on this disk, the selected disk is of the GPT partition style." At this point I tried reformatting the disk but obviously deleted my recovery partition and couldn't boot Windows 8 at all. I then thought best course would be to install ubuntu allowing it to install over Windows 8 and try to amend the problem from there. Ubuntu installed perfectly and is working better than Windows 8 did before. The trouble is that I now can't install Windows 7 (needed for course work) at all. If I change the boot order to boot from memory card or USB stick I just get the error "Bootmgr is missing, press ctrl+alt=delete to restart". I have run Boot Repair and have been given this URL [http://paste.ubuntu.com/6059601/](http://paste.ubuntu.com/6059601/)

Apologies for the mess I've made and much appreciation to anyone kind enough to try to help =)

---

### Post by rai_shu2 on 2013-09-03
So, you really need [Windows support]("http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx"). I'm not sure Boot Repair can help you, considering you already have Ubuntu installed.

Note that booting Windows in UEFI is only supported for 64-bit versions of Windows.

---

### Post by weegeekus on 2013-09-03
You guys are so much nicer though ;-)

Yep, I got that. 

Thank you for your reply.

---

### Post by oldfred on 2013-09-03
Do you want BIOS boot with MBR(msdos) partitions or UEFI boot with gpt partitions. 
Windows only boots from gpt partitions with UEFI.
Ubuntu will boot from gpt partitioned drives with UEFI (efi partition needed) or with BIOS (bios_grub partition needed)
Both Ubuntu & Windows only boot from MBR drives with BIOS.

 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

      
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

And Windows does not properly remove gpt partition table backup when installed in BIOS/MBR mode. You would have to use fixparts if that is what you want.

How is Ubuntu installed? UEFI or BIOS?

More info on UEFI in link in my signature.

---

### Post by techie-smarts on 2013-09-04
Just a random thought, if you have Ubuntu up and running, why not just load Windows 7 as a VM through VirtualBox?  Windows without the mess, and you don't have to muck around with setting up dual boot and UEFI and all of that mess.

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Other OS/Distro Support**.*

Not really a Ubuntu support question. Good luck though. ;)

---

### Post by weegeekus on 2013-09-05
Thank you for your response. I will work through all the information and the links and get back to you (hopefully tomorrow). =)

---

### Post by weegeekus on 2013-09-05
I had that thought too.. Might give it a shot, even just as a temporary measure =)

---

