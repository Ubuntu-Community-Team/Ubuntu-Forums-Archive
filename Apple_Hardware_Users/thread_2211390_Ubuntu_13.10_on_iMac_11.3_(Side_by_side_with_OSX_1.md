---
title: "Ubuntu 13.10 on iMac 11.3 (Side by side with OSX 10.8.5)"
date: 2014-03-15
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2014-03-15
Hi all,

This is somewhat frustrating as I have been using Ubuntu since version 6.06 (Dapper Drake) on all the computers I have had.

Previously I had installed Ubuntu 12.04 LTS on my iMac 11.3 in a dual boot configuration together with OSX. This worked perfectly.

Recently, I deleted Ubuntu 12.04 and attempted to install Ubuntu 13.10.

My usual method is as follows:

1. Use free space to make a partition (FAT) for Ubuntu
2. Install rEFIT (now using reFIND)
3. Start computer from the Ubuntu CD/DVD
4. Format the FAT partition created earlier to Ext4
5. Install Ubuntu to that new partition
6. Restart
7. Select Ubuntu in the rEFIT (now reFIND) menu
8. Ubuntu starts normally

Not so however with Ubuntu 13.10. Everything up to point 7 above works.

After the installation I restarted and in the rEFIT (now actually using rEFIND) window I see an option for Linux.

But, when I try to boot from it, all I get is a black screen with a blinking cursor.

I just don't get it. Has anyone managed to install Ubuntu 13.10 on an iMac 11.3?

What has changed now with the installation procedure?

Any help appreciated.

Thank you.

---

### Post by PartisanEntity on 2014-03-16
I have given up with 13.10 and have gone back and installed 12.04.

---

### Post by wn1ytw on 2014-03-17
I'm getting similar on my Imac mid-2011 12,1 with AMD Radeon HD 6770M 512 MB on 13.10 and the Trusty daily of 3/16. The iMacs are a real pia.
scott

---

### Post by PartisanEntity on 2014-03-18
> **wn1ytw said:**
> I'm getting similar on my Imac mid-2011 12,1 with AMD Radeon HD 6770M 512 MB on 13.10 and the Trusty daily of 3/16. The iMacs are a real pia.
scott

I am a bit disappointed that Ubuntu 12.04 LTS installs just fine on the iMac side by side with OSX 10.8.5, but Ubuntu 13.10 does not.

Evidently something about the install process has changed with Ubuntu 13.10. Canonical needs to work on a more consistent installation process IMHO.

---

### Post by wn1ytw on 2014-03-18
I found some things to try and made headway. Refind -newer version [http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/](http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)
 
and this: [http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/](http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)
right  now I get menu and boot in 'blind mode' 'log graphics mode'

I will be trying this if the second  monitor thing works in the next few days: [http://ubuntuforums.org/showthread.php?t=2209040](http://ubuntuforums.org/showthread.php?t=2209040)

 too would at least like one thread with a good fix and searches on imac video to show how without all the false trails

---

### Post by wn1ytw on 2014-03-28
I found this thread to be VERy interesting and helps me understand some of this [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

