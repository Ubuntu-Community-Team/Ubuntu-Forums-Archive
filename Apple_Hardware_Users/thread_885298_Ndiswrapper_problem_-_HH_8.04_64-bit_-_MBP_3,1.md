---
title: "Ndiswrapper problem - HH 8.04 64-bit - MBP 3,1"
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by ZCos on 2008-08-09
First,  a big thank you to all of you who have unwittingly answered a lot of my questions. Also, apologies for my complete ignorance of Linux.  I've been learning at the school of hard-knocks...

I'm triple-booting a MBP 3,1 with Vista 64-bit and HH 8.04 64-bit. 

ms@mbp:~/madwifi$ uname -a
Linux mbp 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

Initially, I was using the Madwifi pre-release drivers for my Atheros card and they worked fine. While trying unsuccessfully to get the coretemp sensor to work, I somehow disabled the Atheros.  So I uninstalled Madwifi, including undoing the edits to /etc/rc.local and /etc/default/acpi-support. 

I followed the MacBook [[https://help.ubuntu.com/community/MacBook#Wireless]](https://help.ubuntu.com/community/MacBook#Wireless]) installation instructions along with the readme for v. 1.53.  The first issue I ran into was that my output from 

ls /lib/modules/'uname -r' /build

did have an "include" directory but did not have a ".config" file. After googling, I was left with impression that I might need to create a symbolic link of some kind but went ahead with the install.  (This sounds even lamer as I write it but I thought it might be fixable after the fact.)  FWIW, this is what the output looks like now:

ms@mbp:~$  ls /lib/modules/`uname -r`/build

arch    Documentation  include  Kbuild  Makefile        net      security
block   drivers        init     kernel  mm              samples  sound
crypto  fs             ipc      lib     Module.symvers  scripts  usr

I seemed to be able to proceed with the installation:

ms@mbp:~/Installers/ndiswrapper-1.53$ mkdir ~/atheros
ms@mbp:~/Installers/ndiswrapper-1.53$ unrar x AtherosXPInstaller.exe ~/atheros/

UNRAR 3.71 beta 1 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from AtherosXPInstaller.exe

Setup=DPInst.exe
Silent=1
TempMode


Extracting  /home/ms/atheros/net5211.inf                              OK 
Extracting  /home/ms/atheros/net5416.inf                              OK 
Extracting  /home/ms/atheros/DPInst.exe                               OK 
Extracting  /home/ms/atheros/ar5211.sys                               OK 
Extracting  /home/ms/atheros/ar5416.sys                               OK 
Extracting  /home/ms/atheros/net5211.cat                              OK 
Extracting  /home/ms/atheros/net5416.cat                              OK 
Extracting  /home/ms/atheros/DPInst.xml                               OK 
All OK
ms@mbp:~/Installers/ndiswrapper-1.53$ sudo ndiswrapper -i "~/atheros/net5416.inf"
couldn't open ~/atheros/net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
ms@mbp:~/Installers/ndiswrapper-1.53$ 
ms@mbp:~/Installers/ndiswrapper-1.53$ sudo ndiswrapper -i '/home/ms/atheros/net5416.inf' 
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
ms@mbp:~/Installers/ndiswrapper-1.53$ ndiswrapper-l
bash: ndiswrapper-l: command not found
ms@mbp:~/Installers/ndiswrapper-1.53$ ndiswrapper -l
net5416 : driver installed
	device (168C:0024) present
netathrx : driver installed
	device (168C:0024) present

However, at the last step, it looks as if ndiswrapper.ko didn't make it into /lib/modules/2.6.24-20-generic/misc/ and no wireless networks are being recognized.

ms@mbp:~/Installers/ndiswrapper-1.53$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.24-20-generic/misc/ndiswrapper.ko': No such file or directory

I apologize if this unclear but I'm beginning to lose it.  Thanks again for your help.

---

### Post by cyberdork33 on 2008-08-10
First, you should probably use the page for MBP instead of the Macbook (not that it should actually matter in this instance...)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Second have you tried rebooting? Have you tried just reinstalling madwifi? have you tried [ath9k]("http://ubuntuforums.org/showpost.php?p=5545069&postcount=5")?

---

### Post by ZCos on 2008-08-10
> **cyberdork33 said:**
> First, you should probably use the page for MBP instead of the Macbook (not that it should actually matter in this instance...)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)


Second have you tried rebooting? Have you tried just reinstalling madwifi? have you tried [ath9k]("http://ubuntuforums.org/showpost.php?p=5545069&postcount=5")?


I think I used the Macbook page because the MBP page didn't have any step by step instructions on ndiswrapper but I could be wrong.  I did reboot w/o any success and will reinstall madwifi rather than put a lot of time into ndiswrapper.  I read about the ath9k driver right after I posted.  It sounds like an ideal solution but can install it using with my current kernel or do I need to downgrade first?

---

### Post by cyberdork33 on 2008-08-10
> **ZCos said:**
> I think I used the Macbook page because the MBP page didn't have any step by step instructions on ndiswrapper but I could be wrong.  I did reboot w/o any success and will reinstall madwifi rather than put a lot of time into ndiswrapper.  I read about the ath9k driver right after I posted.  It sounds like an ideal solution but can install it using with my current kernel or do I need to downgrade first?
I think you are right about the ndiswrapper instructions, but I did not understand that this is what you were seeking there...

you can try installing and see if you get an error, but 2.6.24-19 is the latest stable kernel so it would be best to stick with that anyway. Is there a reason that you have installed the -20 kernel?

---

### Post by ZCos on 2008-08-10
> **cyberdork33 said:**
> I think you are right about the ndiswrapper instructions, but I did not understand that this is what you were seeking there...

you can try installing and see if you get an error, but 2.6.24-19 is the latest stable kernel so it would be best to stick with that anyway. Is there a reason that you have installed the -20 kernel?

I just booted into 2.6.24-19 and my wireless returned.  I'm guessing that the original problem with Madwifi may also have been related to using the 2.6.24-20 kernel. Lesson learned and thanks!!!

---

### Post by cyberdork33 on 2008-08-10
> **ZCos said:**
> I just booted into 2.6.24-19 and my wireless returned.  I'm guessing that the original problem with Madwifi may also have been related to using the 2.6.24-20 kernel. Lesson learned and thanks!!!
ah yes, in that case, pretty much anything that you compile against a kernel version will break when you upgrade the kernel and they will need to be compiled again (against your new kernel). Just FYI!

---

