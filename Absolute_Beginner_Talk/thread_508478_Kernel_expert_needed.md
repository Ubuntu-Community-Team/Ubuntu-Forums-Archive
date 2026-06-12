---
title: "Kernel expert needed"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jnorthr on 2007-07-24
The ppa module appears to need scsi support in order to recognise any devices on a parallel port like a zip100 device. I put ppa in /etc/modules and put 'sg' (the scsi generic code) before ppa then rebooted.

As i do NOT have a printer, ppa shows up in syslog but never displays any configuration messages to indicate it's become attached to the base scsi code in the kernal or to the 'sg' module. Does the 'ppa' module have any -v for verbose setting to yield further diagnostics ? I'm just getting the feeling that ppa is not finding scsi to drive the zip100 thru the parallel port.

I won't let this beat me...:roll:    come on guys - a bit of help pls.

many thanx

---

### Post by pebo on 2007-07-24
Back in those far off days of SuSE 6 I seem to remember zip drives had to be mounted as /dev/sda4...so you could try```
sudo mkdir /media/zip
sudo modprobe ppa
sudo mount -t vfat /dev/sda4 /media/zip
```Good luck!

---

### Post by jnorthr on 2007-07-24
Yes, thx for that suggestion. I've tried it several days ago. Now i'm to the point of using mknod to create a connection to a block-type driver as i need a block driver in order to 'mount' the zip drive. I've done a 'cat /proc/devices' to find the major/minor codes. But the only block devices are ide0 and ide1, ram and floppy - no scsi. My 'sg' generic scsi module shows as a character device, so i cannot mknod to point to that as 'mount' does not then work. I believe you are correct in that code should describe /dev/sda4 as the node. I have also inserted an entry in 20-names.rules (or similar) to include BUS="scsi" ... and a bunch of parms. I just feel that the scsi code is not active before the 'ppa' module needs it thus does not 'see' it and does not make a scsi connection. :confused:

links i've used: [http://ubuntuforums.org/archive/index.php/t-12074.html](http://ubuntuforums.org/archive/index.php/t-12074.html)  and this one is good but does not seem applicable for 7.0.4 : [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive)

---

### Post by jnorthr on 2007-07-25
Hi again -
can you pls review the following issues we have with the ppa module and scsi support code in the kernel ?
ta

---

