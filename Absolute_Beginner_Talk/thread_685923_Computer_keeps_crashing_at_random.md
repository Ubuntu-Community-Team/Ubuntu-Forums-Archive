---
title: "Computer keeps crashing at random"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jeeperscreepers on 2008-02-02
Hey, I've got his problem with Ubuntu randomly crashing. I generally just thought this was an issue with over heating. I don't know why this would be happening, Im usually only running ktorrent and vlc when i notice the crash. . im running ubuntu 7.10 and this is the only release i've been having this issue with. Recently it just doesn't shut down right away, one window will close unexpectedly and then i will hear the fan kick in and boom restart. I had "top"  open on the most recent crash and noticed that apport was running at 94% cpu. Which i think is kinda crazy for a bug report program especially when it didn't even open a bug report window. That was the only thing i noticed in top before the computer crashed. If you guys could drop me any hints or help that would be great. Just a Note Im running Ubnuntu on a 10gb partition with 3gb free.

---

### Post by metol on 2008-02-02
I had a very similar problem with spontaneous reboots.  After much troubleshooting my, problem turned out to be a bad motherboard.  Once I replaced the MB, everything was fine. But your problem could also be from overheating, a bad or poorly seated memory chip or CPU, etc.   Before spending money on new hardware, I would re-seat the memory and make sure the system is not overheating because of a faulty fan or something obvious.  You could also check power connectors, etc. 

Good luck... these types of problems are a real pain.

---

### Post by jeeperscreepers on 2008-02-03
they definately are. I origionally thought heat was the issue so i added a zalman fan. I am now lead to believe that it is either the harddrive or the motherboard. The macine is about 4 years old. Sad news is it was a gift from my grandfather who has since passed. So i ddn't want to part it. Well it only hiccups every so often so im probably just going to tough it out. Thanks for all the help.

---

### Post by bumanie on 2008-02-03
Could possibly be ram also. Do a memtest+86 with the live cd or from grub listat boot and see what it comes up with. It takes ages, but if ram has errors, it should show up after a while.

---

### Post by kellemes on 2008-02-03
Could be /var/log/messages gives hints on this issue..

---

### Post by forestpixie on 2008-02-03
I've just had the same thing here - turned out to be the power supply, I installed xsensors - checked the reported voltages - one seemed to be way off and a bit wobbly :) - been fine since

---

### Post by jeeperscreepers on 2008-02-10
That could be it. It is only a cheap power supply. So did you have to replace the powersupply or did xsensors solve your problem? 

** I now have xsensors installed and im getting:**

**Vcore:**1.36, 
**+12v: **: 12.83(which worries me), 
**+3.3: **: 3.14, 
**+5.0v: **: 5.01V,
** -12v: **: -11.94/-11.74, 
** V5SB: **: 5.08v,
** VBat **: 3.25V. 

So is the HDD shot, i've already had like 3 crashes today. My cpu is hanging out around 60.5 even with the fan turned down. Most of the time it seems that the comp crashes when thee dvd player is going but recently it crashed when i was watching media off my external hardrive. If it is the power supply what do i have to take into consideration when i buy a new one.

**In terms of /var/log/messages Right before the crash i got these messages:**

Feb 10 20:04:53 media kernel: [ 3215.043068] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 10 20:04:53 media kernel: [ 3215.043085] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'THE_OFFICE__CHRISTMAS_SPECIAL', timestamp 2004/08/25 09:43 (1f2e)
Feb 10 20:20:40 media kernel: [ 4162.509144] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 19 (level, low) -> IRQ 18
Feb 10 20:21:01 media kernel: [ 4183.224832] i2c /dev entries driver
Feb 10 20:32:41 media -- MARK --
Feb 10 20:52:41 media -- MARK --
Feb 10 21:12:39 media -- MARK --
Feb 10 21:32:39 media -- MARK --
Feb 10 21:52:39 media -- MARK --
Feb 10 22:12:39 media -- MARK --
Feb 10 22:17:15 media syslogd 1.4.1#21ubuntu3: restart.

Not sure if these are correct.

---

