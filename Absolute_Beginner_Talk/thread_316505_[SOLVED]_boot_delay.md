---
title: "[SOLVED] boot delay"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by dkjedi on 2006-12-10
hi, i'm pretty new to linux and have used ubuntu 6.06 and 6.10 and on both my  system pauses for about 30 seconds at boot, if i hit alt + 1 it says 

"hdb: no response (status = 0xff), resetting drive"

 as far as i can tell it is looking for the 2nd ide channel, problems is my mother board (Intel® Desktop Board D945GNT) doesn't have one, it only has one ide channel. thanks in advance, if you need more info please let me know (and the location of the info please).

---

### Post by ciscosurfer on 2006-12-10
A 30 second boot time is roughly average for startup time. :-)

---

### Post by dkjedi on 2006-12-10
sorry should have been more specific in have to wait 30 - 45 seconds for the error to clear then another prolly 45 for the system to finish booting

---

### Post by igknighted on 2006-12-10
What is the slave on the primary IDE?  hdb is the slave on the primary IDE.

---

### Post by ciscosurfer on 2006-12-10
You might want to check your log files as well for more info on the errors: looking under /var/log for log files.

---

### Post by dkjedi on 2006-12-10
i have no slave just a master, my dvd drive, hard drive is sata. checking log but not sure what to look for. thanks

---

### Post by dkjedi on 2006-12-11
bump

---

### Post by mcglnx on 2006-12-11
What is the actual error message?

---

### Post by dkjedi on 2006-12-11
hdb: no response (status = 0xff), resetting drive

i also when in too my logs the only thing i can find related is from dmsg and is follows

[17179571.996000] ICH7: chipset revision 1
[17179571.996000] ICH7: not 100% native mode: will probe irqs later
[17179571.996000]     ide0: BM-DMA at 0x20b0-0x20b7, BIOS settings: hda:DMA, hdb:pio
[17179571.996000] Probing IDE interface ide0...
[17179572.744000] hda: DVDROM 8X, ATAPI CD/DVD-ROM drive
[17179583.220000] hdb: no response (status = 0xff), resetting drive
[17179618.444000] hdb: no response (status = 0xff)
[17179618.500000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

i don't know how to use the log files very well though.

---

### Post by mcglnx on 2006-12-12
Did you try to mount your hdb from the live CD?
Did you just plug a new Hard drive?

---

### Post by dkjedi on 2006-12-13
no, i haven't changed anything in the case, but it has done this from the time i installed linux. It has never worked properly. My drive config is 
ide0 (hda) - dvd rom
ide1 (hdb) - empty
sata1(sda) - 300gb harddrive.

thanks for your response

---

### Post by igknighted on 2006-12-13
What is the jumper on your DVD drive set at?  Try setting it as cable select, or making sure that it is on master and plugged in to the master plug on the IDE ribbon (the middle one i believe?)

---

### Post by dkjedi on 2006-12-13
thanks i will try that, currently it is set to master but on the end of the cable i thought that was the proper config. thanks.

---

### Post by igknighted on 2006-12-13
> **dkjedi said:**
> thanks i will try that, currently it is set to master but on the end of the cable i thought that was the proper config. thanks.

You could be right, I'm not certain on that one... but it can't hurt to try.  I gave up with master/slave configurations long ago in favor of CS, much simpler

---

### Post by dkjedi on 2006-12-13
Problem solved. Thanks to all that helps me. In the end i had to swap out the dvd drive for another, not sure but the controler card in the old dvd drive must be on its way out. Thanks again.

---

