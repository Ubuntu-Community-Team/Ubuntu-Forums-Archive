---
title: "Ubuntu installed but wont boot from HD"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Trajan47 on 2007-06-17
Im using an old computer to play around with Ubuntu but have had problems with the install.  I'm using an edgyeft live disc and the initial instalation process goes fine.  The problem starts when it instructs me to remove the disc so the comp' can reboot and install the remaining packages.  The computer restarts but does not boot from the hard drive (or any other drive for that matter).  I used a clean install of Ubuntu onto the master hard drive (with plenty of memory) so its shouldnt be a partitioning issues (no more XP on the machine).
I'd appreciate any input or ideas.  I'm excited about getting my feet wet in Ubuntu but only being able to run through the installation process is getting old.

Thanks!
-Patrick

---

### Post by Rocket2DMn on 2007-06-17
There are a few possibilities/options:
The first is that you're having BIOS problems - try setting the HD as the primary boot device instead of the cd drive.
Another possibility is that GRUB (the boot manager) is not installing correctly.  I'm not clear on how to troubleshoot this, but a lot of people do have problems with GRUB, searching the forums may help.
Finally,  try using the alternate cd instead of the live one.  Also, make sure you have enough RAM, I'm not sure about the minimum for Edgy, I think 256 is recommended min. for Feisty though.

---

### Post by Trajan47 on 2007-06-17
Thanks for the input.

1. How should i go about setting the HD as my primary boot device?  
2. I'll try the alternate cd however i've used two different installation cds of ubuntu (one came with a guide book i bought, the other is from a friend) and still no luck.
3.  I do have 256mb of RAM so i think i should be good on that aspect.

Thanks again!

---

### Post by Bostonian on 2007-06-17
I'm new to linux, but I can answer question 1:
Its a little different on every computer, but right when you turn on your computer you should see an option on the screen to go to settings/setup/ect. (usually its something like "hit f12 now to enter setup"), the menus should be pretty clear from there.

---

### Post by w4ett on 2007-06-17
Does it boot into the Grub Bootloader, and then fail to boot into  Ubuntu,  or does the computer display a message such as : No System Disk Found, or Press any key to boot from CD or other messages?

As far as entering Setup (BIOS) all machines are different.....F1, F2, F12, and ESC or DEL have been used as keys to enter Bios....Usually the M/B post screen will give you the key to press to do this.

---

### Post by Rocket2DMn on 2007-06-17
> **Trajan47 said:**
> Thanks for the input.
1. How should i go about setting the HD as my primary boot device?  
As mentioned above, it depends on your computer - you may only have a split second to see they proper key, so it may take more than 1 reboot attempt to get to BIOS.  Once in the BIOS you need to change the Boot Order (or Sequence).  It should explain how to do it.
> 2. I'll try the alternate cd however i've used two different installation cds of ubuntu (one came with a guide book i bought, the other is from a friend) and still no luck.
CDs can be corrupt, so if you re-download, check the md5sum on the .iso file, then  burn at a slow speed (this seems to alleviate a lot of problems).  With 256MB RAM you might as well get the Ubuntu 7.04 Feisty Fawn alternate cd so you can stay up to date - this also makes it easier for us to assist you in the future.
> 3.  I do have 256mb of RAM so i think i should be good on that aspect.
You should be fine as long as you don't overdo it with lots of multitasking and eye candy (like Beryl window manager)

Good luck!

---

### Post by Trajan47 on 2007-06-18
Upon a restart the computer gives a "Boot Failure" message.  It shows the record of searching for a Boot Record from "Floppy" then "CDROM" then "SCSI".  
No key i press has any tangible effect other than bringing up the same error message.  
I am currently downloading the image file for the Alternate Installation CD and will try that out ASAP.
Any comments or ideas are welcome.

Thanks!

---

### Post by Rocket2DMn on 2007-06-18
Yeah, it sounds like your boot order is messed up.  Did you check your BIOS's boot order?  You should be able to access it before those failures, but you only have a split second to do it.  If you don't see HDD as an option, is it possible the HD is not longer connected properly, perhaps the power cable or IDE/SATA cable is loose?

---

### Post by Trajan47 on 2007-06-18
As of right now I think it's working thanks to the advice.  It took 2 or 3 tries but i finally was able to bring up the BIOS setup menu and put my IDE-0 and IDE-1 HDs in the boot order.  I'm not sure which one it was on, but Ubuntu booted regardless and is now installing the remaining packages.  Thanks again.  I'm thrilled to be able to start playing around with it.

Thanks!

---

