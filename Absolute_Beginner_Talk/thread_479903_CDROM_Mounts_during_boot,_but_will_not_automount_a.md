---
title: "CDROM Mounts during boot, but will not automount after?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bderr on 2007-06-20
New Ubuntu/Linux user, so bear with me.

I've read various posts about patches, fstab, etc about getting CDROMs to mount, but my problem is probably more related to automount.  I can boot Ubuntu Fiesty with a CD, and it mounts correctly.  If I eject it, and close it again, it fails to detect the CD.  I ran list_cddrives, and get this:


Drive:
  name:                 DVD+RW ND-5100A
  device:               /dev/scd0
  door:                 open
  type:                 CD-R, CD-RW, DVD+R, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       4234 KiB/s (CD 28.2x, DVD 3.1x)
  max write speed:      2822 KiB/s (CD 18.8x, DVD 2.0x)
  write speeds:         2822 KiB/s (CD 18.8x, DVD 2.0x)
                        1411 KiB/s (CD 9.4x, DVD 1.0x)
                        706 KiB/s (CD 4.7x, DVD 0.5x)

Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined


It appears that it thinks that the CDROM door is open; but it isn't.  When I reboot, the CD then mounts correctly.  I'm mostly sure that the hardware is good, but Dell will only support WinXP.  I'm running Ubuntu Fiesty on a Dell Inspiron 5150 laptop, with a NEC CD ROM

---

### Post by Jimmyfj on 2007-06-20
If I have understood you corrctly you have run the live cd and then removed it from the Cd once Ubuntu is up and running on the disk? 

If not - And you have Feisty installed on your hard drive then you could try this:

In a command you write:

sudo apt-get install autofs

Then you try 

automount /dev/cdrom

3'rd option is to right-click on the cd-icon in Nautilus and select Unmont

---

