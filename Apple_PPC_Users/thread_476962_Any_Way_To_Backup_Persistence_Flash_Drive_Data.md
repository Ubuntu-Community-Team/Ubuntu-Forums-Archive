---
title: "Any Way To Backup Persistence Flash Drive Data?"
date: 2007-06-17
forum: Apple PPC Users
---

### Post by jimwg on 2007-06-17
Greetings!

I've been hunting high and low for an answer to backing up the data on a Persistence flash drive against the catastrophic loss of hours and hours of setting up various app prefs and settings and configurations and downloaded Linux programs but found nothing on this issue, which I find incredible since I suspect most newbies at Ubuntu will rather first test it out using persistence on flash drives and live-CDs than the hassle of reformatting a HD just to test a OS. Currently I partitioned my flash drive into Linux and DOS because DOS is visible to both Mac and Edgy Ept so can be used to shuffle docs and other data between the two systems, but there's no way to actually copy or backup your actual casper-rw persistence data to your iDisk or external drive to reinstall your flash drive after a crash or zap. I was willing to eat several crashes in trying out Ubuntu and take the time to recreate my configurations and re-download programs, but more than a few newbies might not be so patient or understanding and leave vexed muttering Ubuntu sucks under their breaths to their friends, so it behooves the community for a productive people-friendly solution.

Any ideas will be much appreciated!

James Greenidge

---

### Post by dannyboy79 on 2007-06-19
> **jimwg said:**
> Greetings!

I've been hunting high and low for an answer to backing up the data on a Persistence flash drive against the catastrophic loss of hours and hours of setting up various app prefs and settings and configurations and downloaded Linux programs but found nothing on this issue, which I find incredible since I suspect most newbies at Ubuntu will rather first test it out using persistence on flash drives and live-CDs than the hassle of reformatting a HD just to test a OS. Currently I partitioned my flash drive into Linux and DOS because DOS is visible to both Mac and Edgy Ept so can be used to shuffle docs and other data between the two systems, but there's no way to actually copy or backup your actual casper-rw persistence data to your iDisk or external drive to reinstall your flash drive after a crash or zap. I was willing to eat several crashes in trying out Ubuntu and take the time to recreate my configurations and re-download programs, but more than a few newbies might not be so patient or understanding and leave vexed muttering Ubuntu sucks under their breaths to their friends, so it behooves the community for a productive people-friendly solution.

Any ideas will be much appreciated!

James Greenidge
Please don't double post again, I believe it's in the rules. If someone doesn't answer you within a 8 hours or so, then simply bump your post, but please don't double post. The admins will most likely combine your threads now. 

i don't totally understand what you want to do here, if all you want to do is make sure that all your stuff is backed up in case of catastrophic failure, then make a copy of it. meaning, boot to a normal live cd, plop in your usb drive, it should auto-mount, then simply plop in another usb drive you want to back it up to, and merely copy and paste frmo Nautilus or use the command line 
sudo cp -R /media/ubuntustick/ /media/newlocation/

Also, you can mount windows drives within your usb stick install by doing something like this:
sudo sufdisk -lcd /mediamkdir windowsmount /dev/hdd2 /media/windows
If you want to be able to write to NTFS, then look into ntfs-3g, as far as writing to whatever the mac's filesystem is, here's the link I found: [http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/)
Installing and using DOS is far from required. good luck

---

