---
title: "How-To install and run Ubuntu from external USB hard drive"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by stmiller on 2010-05-02
How to install Ubuntu to external USB hard disk and leave your existing Intel Apple machine and internal hard drive untouched.

There seems to be a lot of confusion over this topic. Here is a method that works if you don't want to/are unable to alter your existing OS X install or hard disk.

Before beginning, back everything up from your internal OS X hard drive install! Instructions are at your own risk. 

You will need the following before starting:

- USB hard drive
- Ubuntu install CD
- rEFIt bootable CD ([http://refit.sourceforge.net/doc/c1s5_burning.html](http://refit.sourceforge.net/doc/c1s5_burning.html))
- Coffee


1. Connect your USB hard drive, and reboot with the Ubuntu install CD in the drive. Hold down 'c', and when the disc boots, hit enter to begin the Ubuntu install as normal.

2. (Important!) During the install at 'Prepare Disk Space', choose your USB hard drive as the location to install Ubuntu. It will default to the internal hard drive - change this or else you will accidentally install on the internal drive!

3. (Also important!) At the last point of the install where it says Ready To Install and you are given a summary screen, CLICK Advanced...

Here CHANGE the hard drive location for the boot loader. It will default to the internal drive location first. Change it to the /dev/sdb or other location of the external USB hard drive.

4. Sit back and let Ubuntu install. At the end of the install, click to reboot and wait for Ubuntu to eject the CD. Now insert your rEFIt bootable CD. 

5. Reboot with the rEFIt CD in the drive. Hold down 'c' as the machine turns on, and there you will enter the rEFIt boot menu. Select Linux Hard Drive and press enter.

:)

**You will need to boot from this rEFIt CD to enter Ubuntu.**

----

This leaves the existing OS X install and such untouched. 

Edit: This is for intel macs!

Cheers,

---

