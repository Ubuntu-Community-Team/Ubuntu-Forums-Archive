---
title: "Unable to boot 11.04 LiveCD on 2011 Mac Mini"
date: 2011-09-13
forum: Apple Hardware Users
---

### Post by Arin91 on 2011-09-13
I'm trying to boot an Ubuntu 11.04 x64 LiveCD using a Pioneer USB CD/DVD drive.

It works fine on a 2010 Mac Mini ( Macmini4,1 ).

The same drive and media will not boot on a 2011 Mac Mini ( Macmini5,1 ).

The error is:
No bootable device -- Insert boot disk and press any key

Trying the i386 flavor yields the same result.

Kind of stuck here.  Anybody else able to successfully boot on a 2011 Mac Mini?

---

### Post by Arin91 on 2011-09-13
I did verify I could boot a win7 usb install key and a win7 dvd from the same Pioneer drive.
 
I also tried rEFIt which could see the ubuntu cd but resulted in the same error.
 
Using another system to install to a usb drive, verifying it works, and then trying to boot that on the 2011 mini resulted in the same error.
 
It seems to be getting through grub. On the x64 cd there is a "EFI" cd shown as an option to boot which does bring up a grub menu. But again, selecting Try Ubunutu without installing results in the same error. Selecting the Install Ubuntu hangs with a blank screen.
 
I noticed after selecting the drive to boot there is some brief activity, halts for about 20 seconds and then the error is shown.
 
I also have tried the 32bit flavor of Ubuntu 11.04 with the same results.
 
So still stuck.
 
1. USB CD/DVD drive and Ubuntu 11.04 x64 boots on Mac Mini 2010
 
2. Same USB CD/DVD drive and same Ubuntu 11.04 x64 on Mac Mini 2011 fails with:
 
No bootable device -- Insert boot disk and press any key
 
3. Ubuntu 32bit 11.04 yeilds the same results.
 
4. Using another system to install Ubuntu to a USB Hard Disk results in the same error with/without rEFIt.
 
5. Win7 media does boot (either DVD or Win7 USB Installation key).

---

### Post by Arin91 on 2011-09-14
Apparently this is a known issue with Mac's that have multiple partitions on their boot drive.
This is standard with all new Mac's that now come with a Recovery HD partition for Lion.

Found this here:
[http://ubuntuforums.org/showthread.php?t=1842894](http://ubuntuforums.org/showthread.php?t=1842894)

Which points to this workaround:
[http://ubuntuforums.org/showpost.php?p=11093491&postcount=43](http://ubuntuforums.org/showpost.php?p=11093491&postcount=43)

And I can confirm it works.
Should get this sticky'd/wiki'd somewhere

---

