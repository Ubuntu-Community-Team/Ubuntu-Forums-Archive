---
title: "Installed..but Ubuntu does not see windows and reboot boots into windows..help"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-02
Hi,

Well I added a new SATA hard drive to my 2xSATA raid/windows configuration.

I then installed 5.10 to the new hard drive. Chose eresase entire disk and format.

Then it installed, without error asked me to remove the install disk and reboot. I did.

BUT then it just re-booted into windows, no grub OS choice.

I do not need to the installs to communicate, Im using Windows XP SP2, on 2x WD raptors set to raid 0.

Any ideas what could have went wrong?

---

### Post by Sutekh on 2006-04-02
At the GRUB installation step, what did you choose to do?  Where did you choose to install GRUB?  On the MBR of the Windows disc or the Ubuntu disc?

---

### Post by gordong11 on 2006-04-02
Hmm.

OK. IT said :loading paritioner...then it gave me 3 disk options, I chose the new one. IT then asked to erase entire disk or erase entire disk with LVM. I chose the standard, pressed enter. It then gave me the warning, and pressed wrtite to disk. Thats all, pretty much the same as if I was installing it on a brand new PC build.

Should I have manually set patrition table? Im not partitioing though...just installing on new disk.

---

### Post by Sutekh on 2006-04-02
No I don't mean the partitioning, sounds like you did that fine.  

I mean later on the installer asks where GRUB should be installed.  It says if it has detected other OS (ie Windows XP) and asks if it can install to the MBR.  You have the option of answering Yes or No.  If you answer No, you are then asked where you want GRUB to be installed.

So what I want to know is if you said Yes/No and if No where did you install GRUB?

---

### Post by Sutekh on 2006-04-02
Also can you tell me what the device names of the discs are?  

By this I mean what discs containg Windows?  /dev/sda1 and /dev/sdb1?

What disc is Ubuntu on? /dev/sdc1, /dev/hda1?

These names would have been specified during the partitioning process.


This link has some pictures which might help

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Step 8 for the partitioning and device names and Step 34 for the GRUB installation

---

### Post by gordong11 on 2006-04-02
I think it was SCSI1, SCSI2, SCSI 3 and I chose SCSI3 for the new one. Otherwise I dont't remember anything else..Id have to reinstall.

---

### Post by Sutekh on 2006-04-02
What about the installation of GRUB (Step 34 in that link), can you remember if you said Yes or No?

---

### Post by LycoLoco on 2006-10-27
I'm actually having this exact same problem, both with installing Dapper and Edgy. I have XP installed on a SATA drive, and Ubuntu installed on an IDE drive, so obviously they are not on the same drive or drive architecture. I never had an option to choose where to install grub to, so that could be a problem. Anyone have any ideas?

---

### Post by bulldog on 2006-10-27
> **LycoLoco said:**
> I'm actually having this exact same problem, both with installing Dapper and Edgy. I have XP installed on a SATA drive, and Ubuntu installed on an IDE drive, so obviously they are not on the same drive or drive architecture. I never had an option to choose where to install grub to, so that could be a problem. Anyone have any ideas?

It depends which hdd you use to boot.
Probably the Sata disk and GRUB is on your IDE disk.

Try to change the boot order to check things out.

If you used the live cd you're right,it doesn't ask you anything,but dicides for you.
But default it's installed on the first bootdevice and I think in your config it's the IDE drive.

---

### Post by Bigbluecat on 2006-10-27
I had problems like this. The installer did not ask me where I wanted to install grub on my multi disk system then when I tried to boot it just went to windows.

Best way I found to solve it was to download Super Grub Disk:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Then use Herman's guide (see the link above) to use grubs command line interface to manually boot the kernel. Through the command line you can interrogate the system and find where your kernel is and what grub calls all the other disks and partitions. Just follow the step by step instructions.

Once the kernel is booted you can use the knowlegde from the interrogation to edit your menu.lst file.

---

