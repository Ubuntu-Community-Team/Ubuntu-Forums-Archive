---
title: "SATA and HDD - BAD?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by nosto53 on 2008-03-25
My first post.
Me - I an a old geek (55 ago) and I got a stroke in 2005.  
I email is not too good, but working.

I need help to my HDD.  I am using my cdrom to boot for Ubuntu.
I use "install" in the Desktop.  It work, but went the HDD stops
and the Desktop stops.

My BIOS have first boot on cdrom, second on HDD and third is dis.
My IDE channel 0 master - none     0 slave - Lite On cdrom
                         2  master - none     2 slave - none
                         3  master - none     3 slave - WD 36G (old)

In 'Integreted peripherals" -     OnChip IDE0               (ena)
                                                  OnChip SATA Control (ena)
                                                  OnChip SATA Type     (Native IDE)
My new Seagate 250G is not seen!
Could my BIOS is right or wrong?

Rick, in the FAA (Yes - I like the airplanes!)

---

### Post by nosto53 on 2008-03-25
Me!

This is my new PC:

AMD 6000+ 3.0Ghz
Mushkin DDR2-800  1G x 2 (5-4-4-12)
Gigabyte GA-MA690G-S3H
Seagate 250G 16 cache SATA2
Zalman 9500 copper fan (cool!)
NO WINDOWS!!!!!
Getting  Ubuntu or Debian 4.0 (64)

Rick at FAA......

---

### Post by c-ron on 2008-03-25
Hi Rick,
You may want to check this link:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/21186](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/21186)

The things that I can think of to try would be to post your dmesg log here. Boot from the LiveCD, Hit ALT+F2 to run a program, type or paste in 'dmesg >> ~/Desktop/dmesg.txt' 

Also post your /boot/grub/menu.list file here.
'cat /boot/grub/menu.list >> ~/grubsettings.txt'

---

### Post by Shazaam on 2008-03-25
AFAIK most motherboards use SCSI to denote SATA drives. Maybe look in the bios for a SCSI setting. My Soyo board requires having RAID enabled but no array defined (SATA listed as SCSI) to be able to access it as SATA. You also might want to find a manual for the board from the manufacturers website. The one that came with my board wasn't very helpful.

I found this.....
[http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2554](http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2554)

You also might want to try the "Alternate Install" cd.

---

### Post by tgalati4 on 2008-03-25
Sometimes you have to go into BIOS and set IDE to "Enhanced" to allow 6 hard drives to be detected (2 drives for 3 channels).  Sometimes this mode allows both regular IDE drives and newer SATA drives to be detected. 

If you don't see your drive during the initial bootup--right after the BIOS message, then Ubuntu will never see it.

---

