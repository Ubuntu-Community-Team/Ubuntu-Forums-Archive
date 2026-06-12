---
title: "Help Need to Uninstall Linux"
date: 2013-11-13
forum: Any Other OS
---

### Post by Captain_Black-Heart on 2013-11-13
Current OS: linux MINT 13 (Maya) only
Machine: Acer Aspire 5720z  

Cannot Install Win 7 from USB.

I need to either know how I can accomplish adding Win 7 to this OS     

---OR---

How to uninstall Mint so that I can reinstall after Win 7   ( after reading through various threads/posts ) 
I have gleaned :

Windows doesn't like to play second fiddle to another OS....
Linux will not properly run on the Acer Aspire 5720z  ( various power management issues....such as fan control, battery recognition( kubuntu ) and the like that I have experienced.

I am currently having to force the CPU fan on each time I start run the machine from the console. 

Any help would be greatly appreciated, as I know Jack and Crap about Linux, and Jack left town.

Thanks


PS      Linux will not recognize a Win 7 USB stick, even after changing Boot Order in Bios.......system thinks about it, then just boots to MINT.

PS...PS.....also currently unable to upgrade BIOS from USB and FreeDos  ( most likely my errors on setting it up, but when I get to the point of trying to run from the drive, it only states "cannot be run from DOS".   


The Capn

---

### Post by oldos2er on 2013-11-13
Moved to Other OS/Distro Support.

---

### Post by buzzingrobot on 2013-11-13
> **Captain_Black-Heart said:**
> 
PS      Linux will not recognize a Win 7 USB stick, even after changing Boot Order in Bios.......system thinks about it, then just boots to MINT.



Linux has no affect on the BIOS. If the boot order is set to look first to the USB drive and it does not boot, then the USB very likely does not have anything bootable on it. The BIOS will then look at the remaining boot candidates until something does boot. I'd double check the USB.

You don't particularly need to delete Linux before installing Windows.  You can remove the Linux partitions during the Windows install process.  If memory serves, you need to reboot then and restart the Windows installation so it correctly reads the new partition scheme.

---

### Post by hansdown on 2013-11-13
Welcome to the forum, Captain_Black-Heart.

You need to format your drive to fat32, or ntfs so windows will install to it.

Use a live linux usb, and open gparted. This will overwrite your linux install, so save any data you want to keep.

[http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/](http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/)

---

### Post by Captain_Black-Heart on 2013-11-14
Thank you for your response(s). 

I was finally able to burn a GParted disk, use it to reformat my partitions and install. I was planning on changing Linux distros anyway, and wanted a dual boot machine. 
In the end, I was able to figure it out on my own by reading the documentation on the gparted site.  ( that is, after a few unsuccessful attempts ).

System is fine now and in good order.

Again....thank you for your replies.

---

### Post by hansdown on 2013-11-14
Glad you fixed it,Captain_Black-Heart. 

Good work.

---

### Post by thiebaude on 2013-11-15
Captian, I don't know if you have tried this about power management,[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

---

