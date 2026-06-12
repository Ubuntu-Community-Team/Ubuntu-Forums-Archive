---
title: "wireless nightmare: wg111t  usb and linux"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by orpheusblotto on 2006-05-08
hi all. i am a beginner on linux. i appreciate the patience of all the helpful posters here. this is my dilemma:

i managed to install ubuntu (breezy badger 5.10)
i have been trying for 2 days to get my netgear wg111t usb adapter to work. i installed ndiswrapper and used it with windows drivers from netgear website.

here is what i can get out of linux:
-inputing "lsusb -v" shows my adapter @ bus004 Device 2 and gives usbid as 1385:4251 and identifies an atheros chip in the adapter

-inputing "ndiswrapper -l" shows athfmwdl.sys as "driver present hardware present" and netwg11t.inf as "driver present". now here's the weird bit: there are several driver files included with the netgear propietary software. only these two will read as valid drivers by ndiswrapper, even though one is different from what i use in windows.
further, for some reason inputing "ndiswrapper -e" to disable one of these shows that it is not present although the -l switch shows it as present !!!???

-inputing "iwconfig" shows lo eth0 and sit0 as having no wireless extensions

-inputing ifconfig only shows lo

now get this, i managed to get the drivers loaded by the boot script and using dmesg shows 2 lines that say high speed usb detected in two spots, yet the adapter never blinks the active light. also if i do ifconfig the number of tx/rx bits keeps going higher each time i do it ???!!!

some of this may be inconsequential nonsense but i am just grasping at straws here. after searching all over the net i have come up with several conflicting verdicts on this device. many sites list it with different chip # but all agree it has an atheros chip as does linux.

i feel like either a: i am doing something very basic wrong
or b: this adapter is just not yet supported by linux

please help with any info you have
thanks so much

---

### Post by rubrboots on 2006-05-08
Hey  I dont have a solution for you but I had the same problem. I spent days trying to get my netgear usb wifi working. I ended up going hardwired. As you already know there is known problems with some of the netgear wifi adapters. I would suggest trying a wifi adapter that is known to work well with linux or using good ol network cable. Good Luck!

---

### Post by orpheusblotto on 2006-05-09
thanks for responding rubroots. what wireless options would you suggest as being "well supported"?

---

### Post by ORF1000 on 2006-07-27
I got my WG111T to work in Dapper by downloading and compiling a later version of ndiswrapper.  The 1.8 just doesn't work, at least not with my chipset.  [I followed the instructions in this wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  It wasn't hard to do, just more work than I felt like doing.  It was worth it in the end because the WG111T a pretty good device.

Dave

---

### Post by ORF1000 on 2006-07-29
One more thing about the WG111T -- you need to install both Windows drivers -- athfmwdl.inf and netwg11t.inf.

---

