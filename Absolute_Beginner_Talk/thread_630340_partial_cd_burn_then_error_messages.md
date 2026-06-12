---
title: "partial cd burn then error messages"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by md11driver on 2007-12-03
noobie here.  please forgive my ignorance.

using 7.10 gutsy.  equipped with panasonic dvr-105.  using k3b and brasero.  

when trying to burn data files, everything seems to start swimmingly.  shortly after starting the burning process, no matter what program i'm using, error messages appear.

k3b- concerning permissions to open the device

brasero-error message about wrong type of .iso file

no matter what the program, data IS written to the cd during the writing attempt, as evidenced by the change in reflective appearance of the cd.  the cd then becomes a coaster and is not recognized by any program as being a recordable medium.

my searches seem to lead nowhere.  sure could use some competent help.

thanks

---

### Post by gupta_sumesh63 on 2007-12-03
Try the command line option :
Open a terminal

code:
> cdrecord dev=/dev/cdrom driveropts=burnfree -v -data path_to_image_file


here /dev/cdrom is your cdrom device. Could be /dev/hda or /dev/scd0 etc.
path_to_image_file could be /home/yourname/cd_image.iso  or the complete path to the image file.

Secondly please choose a good quality media (disk) like MAXELL. Certain disks have write problems in Ubuntu.
Use a lens cleaning CD/DVD and clean your ROM lens also.
It should write I hope.
Try it.

---

### Post by md11driver on 2007-12-03
thank you gupta

entered into terminal as you suggested and the following was returned.

terry@terry-desktop:~$ cdrecord dev=/dev/cdrom driveropts=burnfree -v -data path_to_image_file
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-105 '
Revision       : '1.10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: none
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R 
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: No such file or directory. Cannot open 'path_to_image_file'.
terry@terry-desktop:~$ 

i will certainly clean the equipment and get different cd-rs.  

looking forward to help from any and all.

thanks

---

### Post by disturbed1 on 2007-12-03
** cdrecord: No such file or directory. Cannot open 'path_to_image_file'.**

Usually in help forums (like this one) we use a generic place holder for files. Such as *path/to/your/image/file.iso*

This isn't a direct link to your file. We can't see your computer, hence we flat out don't know where it is ;).

Let's say the *.iso file is on your Desktop, and it is called data.iso, the correct line would be -

cdrecord dev=/dev/cdrom driveropts=burnfree -v -data /home/terry/Desktop/data.iso

If the file is in your home directory, and named blah blah.iso (notice the space ;) ) Then you would type
cdrecord dev=/dev/cdrom driveropts=burnfree -v -data "/home/terry/blah blah.iso"

So replace path_to_image_file to the **REAL** path and file name.

---

### Post by gupta_sumesh63 on 2007-12-04
Hi,
I think my reply was not understood and the same command was used.
As I mentioned above /dev/cdrom is a generic term. Your CDROM device could be /dev/scd1 or /dev/hda2.
You have to check your pc for the device name of your cdrom device.
> cd /dev
ls -l
the above commands(individually of course) will list out the devices on your system.
The one which corresponds to your CDROM device should be entered i.e dev=/dev/your_cdrom_device_name.
The path to your .iso is the path to your actuual .iso file like clarified above.
please try again.

---

