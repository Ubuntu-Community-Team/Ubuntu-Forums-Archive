---
title: "help..got error &quot;caught signal 11, exiting x-server&quot;"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-02-11
hi.

Well I reinstalled the 64 bit version, after a slightly different error, but now the X-Serv will not boot. I get a feeling its my video. Everything starts OK, initializations go ok within the Ubuntu splash screen, but then it seems to try 3 times to boot the GUI (I notice my monitor trying to connect to the GUI). The I get get an error message and "exiting x-server, an error has occurec, woulkd you like to view the log?"

In the log, the only thing I caan find noteworthy is " Caught Signal 11,exting X=Server".

Any ideas?

---

### Post by d1337 on 2006-02-11
You'll likely need to perform a "dpkg-reconfigure xserver-xorg" from the command line, but first you'll need to know more about your machine.  I reverted from 64 back to 32 as I'm about 32 bits short on time, so I may not be able to help you with specifics.  Is your video on-board, pci or agp?  What does lspci report as your video?

The forums have great howtos for nvidia support as well as ATI. mlomker has written howto for at least the ATI drivers that include 64bit instructions.  Once you know what your video chipset is, a forum search should help tremendously.

d1337

---

### Post by bartbes on 2006-02-11
I thought signal 11 was no screens found..

---

### Post by d1337 on 2006-02-11
[QUOTE=bartbes]I thought signal 11 was no screens found..[/QUOTE]
Likely right...been awhile since I've had x issues that I wasn't expecting (therefore not bothering to read the output).  But, reconfiguring or hand editing xorg.conf should still resolve the issue if I'm not mistaken.

d1337

---

### Post by gordong11 on 2006-02-11
[QUOTE=d1337]Likely right...been awhile since I've had x issues that I wasn't expecting (therefore not bothering to read the output).  But, reconfiguring or hand editing xorg.conf should still resolve the issue if I'm not mistaken.

d1337[/QUOTE]

Sorry... I had to run..so i can dedicate the day to this.

OK...This error was happening yesterday, so I re-installed. After re-install however I'm getting error on the second wave of install, after ejecting the CD. After running Sudo dpkg-reconfigure xserver-xorg. I get an error" must manually run dpkg --configure -a"

I'm running:
AMD Sempron 2800
MSI RS482M-IL(M-ATX) with ATI grpahics
512 mb ram
WD 80 gig caviar SATA

Thats all..in a small case
Starting anew thread..this one no longer is applicable

---

