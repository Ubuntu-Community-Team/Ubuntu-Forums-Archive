---
title: "Problem with DVD Drive"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by rahulsitaraman on 2008-03-23
Ive bin tryin to burn dvd's for the past few days, but nothin happens.. all i get at the end is 'FAILED'

Im attaching a copy of the debugging report tht ws generated.. pls help.. Is it a HW problem or SW???

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.7 "release 72.6"
QT Version:  3.3.8
Kernel:      2.6.22.17-0.1-default
Devices
-----------------------
SONY DVD RW AW-G170A 1.71 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: engaging DVD-R DAO upon user request...
Embarrassed PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2252064 -use-the-force-luke=dao:2252064 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m

---

### Post by mc4man on 2008-03-23
while I've never used k3b what you may want to look at is > Embarrassed PERFORM OPC failed
OPC probably means optimum power calibration - usually fails due to poor quality media. (or somehow incompatible)
Again I don't use k3b so you may want to do a search on that.  (opc)

---

### Post by rahulsitaraman on 2008-03-23
THanx a lot mc4.. But i guess, its got something to do with getting the drivers right.. i googled 'bout optimum/optical power calib.. but no avail.. luks like a lot of ppl r stuck up with this prob.. as i write this, im burning a dvd at 1.1x.. i guess if i use lower speeds ill be able to burn... shall post after my success

---

### Post by mc4man on 2008-03-23
here's a short info - was for cd's though applies to dvd's as well
I>  get a 'Power calibration error' or 'Calibration area (almost) full' error message. Why?

Power Calibration is controlled by the recorder.

Before any write operation, all recorders must do a 15 step power test to determine the optimum power for writing to the CD; this is called "Optimum Power Calibration"(OPC). During the write, it continues to do this test to get the best write throughout the whole CD; this is called "Running Optimum Power Calibration" (ROPC).

This whole process is controlled by the recorder, though initiated by programs such as Nero. There is an area on the inner part of the CD for the test and test data info to be stored. You can use this area up to 999 times.

If you receive the "Power calibration error" or "Power calibration area is (almost) full" error message, the cause will be either poor media, poor power, or a defective recorder.

Please try the following solutions:

1. Update the firmware of your recorder. Please check the manufacturer's website for the latest version.

2. Try another brand of media.

3. Try different power connectors, and for recorders, do not share power with other devices. It needs its own power connector. If the error occurs with an external recorder, the power source in the chassis could be the cause. As a test, try to take the recorder out of the external chassis and connect it internal.

4. Try different configurations, such as taking the CD-ROM to the primary IDE bus as slave and have only the recorder connected to the secondary IDE bus as master.

5. Send the recorder in for service.

---

