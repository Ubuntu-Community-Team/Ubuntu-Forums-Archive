---
title: "Can't run Ubuntu, please help!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-04-19
Hi, I've been trying to dual boot linux on my computer for a while.  First I tried Mandriva, but after installing it, Mandriva would run properly maybe 5% of the time, the rest of the time it would just freeze in the boot screen.  So I tried installing Ubuntu 6.10 and that installed fine as well, but when I tried running it I would get this error saying something about the x graphical interface being wrong/missing (or something like that).  I recently downloaded the newest version of Kubuntu hoping it might have fixed whatever problem I have, and while the Grub screen came up and seemed to work fine (the grub screen is the linux equivalent of microsoft's command screen, right?), when I tried to start a proper image-based desktop (by typing in xstart or startx) it would run for a bit and then say that the x graphical interface is missing (again, it was something like 'x graphical interface', I didn't write down the exact error message when it came up)
:confused: 
Is it some incompatibility with my hardware?  This is the information I thought would be relevant from my device manager.   Any help in joining the linux community would be appreciated.

Computer
.....ACPI Mulitprocessor PC
Display adapters
.....Raedon X600 Series
.....Radeon X600 Series Secondary
IDE ATA/ATAPI contrillers
.....Intel(R) 82801 GB Serial ATA Storage Controllers - 27C0
.....Intel(R) 82801 GB Ultra ATA Storage Controllers - 27DF
.....Primary IDE Channel
.....Primary IDE Channel
Modems
.....Intel(R) 537EP V9x DF PCI Modem
Monitors
.....Dell E173FP
Network adapters
.....Intel(R) PRO/100 VE Network Connection
Processors
.....Intel(R) Pentium(R) 4 CPU 2.80 GHz
.....Intel(R) Pentium(R) 4 CPU 2.80 GHz
SCSI and RAID controllers
.....D347PRT SCSI Controller
Sound, video and game controllers
.....Audio Codecs
.....AVerMedia AVerTV Video Capture (M113, Phillips FM1236MK5 Tuner)
.....Legacy Audio Drivers
.....Legacy Video Capture Devices
.....Media Control Devices
.....SigmaTel High Definition Audio CODEC
.....Unimodem Half-Duplex Audio Drive
.....Video Codecs

---

### Post by Sef on 2007-04-19
The problem is with you graphics card in Ubuntu.  You need to [reconfigure X.org]("https://help.ubuntu.com/community/RadeonDriver").

---

### Post by kvonb on 2007-04-19
Unfortunately, ATI don't put much effort into their support for Linux, but if you wait (hopefully only a few more hours!) until Ubuntu 7.04 is released, that will have better support.

Check here:

[http://www.ubuntu.com](http://www.ubuntu.com)

Regards, KEv :)

---

### Post by zhinker on 2007-04-19
> **Sef said:**
> The problem is with you graphics card in Ubuntu.  You need to [reconfigure X.org]("https://help.ubuntu.com/community/RadeonDriver").

I assume I'm supposed to do all that in the Grub screen?  

I haven't quite figured out how to scroll up to look at the text when it shows more than one page at a time, could someone please tell me the command to use?

---

### Post by AzzozHSN on 2007-04-19
I have same problem I think, every time I start my computer, I get "Error 15: file not found" , I press 'C' then I enter this commands in grub screen:

root  (hd0,0)
setup  (hd0)
kernel  (hd0,0)/boot/vmlinuz-2.6.17-10-generic  root=/dev/hda1  ro
initrd  (hd0,0)/boot/initrd.img-2.6.17-10-generic
boot

replace (hd0,0) , (hd0) and /dev/hda1  to your system partition

I hope some one tell us how to fix this.

---

### Post by zhinker on 2007-04-19
How do I install the lastest version of x.org on windows (I can't seem to run Ubuntu without it because of my stupid Raedon X600 Series video card)?  I went to it's download page but I could only find the source code.  

Any help?

---

### Post by igknighted on 2007-04-19
> **zhinker said:**
> How do I install the lastest version of x.org on windows (I can't seem to run Ubuntu without it because of my stupid Raedon X600 Series video card)?  I went to it's download page but I could only find the source code.  

Any help?

Go to the top of this forum, there is a sticky for the workaround.  You need the alternate CD and to install the proper driver from the CLI after install.  Check it out for specific instructions.

I don't think X.org runs on windows.  It does on Mac OS X though.

---

