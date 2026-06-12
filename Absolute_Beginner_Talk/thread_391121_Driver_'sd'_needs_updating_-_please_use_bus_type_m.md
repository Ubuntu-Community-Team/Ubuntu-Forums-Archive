---
title: "Driver 'sd' needs updating - please use bus_type methods"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Twist on 2007-03-22
Hello Everyone,

I'm kinda new to Ubuntu, and Figured I'd give the LTS a shot, as it seemed suitable for my needs.
To explain my situation in short: I bought an old PC , installed a couple of flashdrives and a couple of harddrives. I'm booting from the flashdrives, and using the PATAs as backupmedia for my network.
HOWEVER. In order to install the PATAs I've had to remove my DVD-rom drive. "No problem" I figured. I have a nice little gadget that allows me to connect any IDE/IDE44/SATA device to a USB port. So I figured I'd just plug in the DVD-ROM when I need it. Well, now I needed it !

Unfortunately, in trying to mount the drive I've run into some problems. The only one I seem to be able to relate to is the one in my title.
After plugging in the USB device, this message appears in dmesg:

Driver 'sd' needs updating - please use bus_type methods

I looked at all the forums I could find, searched high and low, and the message appears to be somewhat ambigous, as it's directed at various pieces of hardware, not just DVD-drives. So presumably it's a hardware issue.
/me goes replace the DVD-drive
When I replace the DVD with a centuries old 44x CD-ROM drive... It works like a charm, I dont even have to replace the original mount point from the time of installation in the /etc/fstab.
BUUUUUT... I still want to be able to connect a DVD-drive, for capacity reasons. And apparently neither my faithful NEC 3500A is usuable (gives LOADS of read errors, presumably a hardware problem, I can't even install on this drive), nor is my Trusty Toshiba TS-H352 (gives the problem in the title).
So how do I go about getting the "SD" driver that needs updating ?

---

### Post by azimout on 2008-04-18
This was filed as a [bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167") on 26/01/2008, and was [discussed briefly on the kernel mailing]("http://lkml.org/lkml/2008/1/10/272") list on 10/01/2008. It seems to be harmless, I had it in 2.6.24 and still have it with 2.6.25, but my disk and cdrom work fine... Ignore it for now, I expect they will fix this at some point

---

