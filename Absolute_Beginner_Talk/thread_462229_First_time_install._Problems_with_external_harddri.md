---
title: "First time install. Problems with external harddrive"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by SpacedMonkey on 2007-06-02
Hi everybody. I've read up on problems connecting an external harddrive to Ubuntu. But haven't been able to find information that can help an "Absolute Beginner"

Here's my dilemma. In order to get my wireless USB to work on my system, I have to copy over a few files. Rather than burn a CD with 20k of files, I figured, I'd just put them on my external HD (I think it was in NTFS)

However, I plugged it into my other computer with Ubuntu 7.0.4 and nothing.

So I do some reading up. 

fdisk -l        does nothing. Shows nothing, just gives the prompt again. So I can't see any HD's with that, let alone see if the new one is on.

I checked dmesg and see the following:
(Forgive me if it's not quite perfect. I have to transcribe it since the Ubuntu box has no network connection.)
usb 5-3: new high speed USB device using ehc1_hcd and address 12
usb 5-3: device descriptor read/64, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 13
usb 5-3: device descriptor read/64, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 14
usb 5-3: device not accepting address 14, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 15
usb 5-3: device not accepting address 15, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 16
usb 5-3: device descriptor read/64, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 17
usb 5-3: device descriptor read/64, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 18
usb 5-3: device not accepting address 18, error -71
usb 5-3: new high speed USB device using ehc1_hcd and address 19
usb 5-3: device not accepting address 19, error -71

Now here's the kicker, and has me a littttttttle pissed off. I reconnected the external harddrive to my windows XP laptop to see if it is indeed NTFS or FAT, and now Windows XP won't recognize it. It just pops up saying it's an Unknown Device.

Now I've used this external HD for awhile, and it's never had any problems, so I doubt it just magically died just now. 

So, now that it's not responding to Windows anymore. How do I get this to mount on Ubuntu 7.0.4?

---

### Post by bobbocanfly on 2007-06-02
I got this problem with my FAT32 flash drive, i plugged it into Ubuntu, didnt work then wouldnt work in windows. Unfortunately I had to reformat the drive to get it working.

---

### Post by SpacedMonkey on 2007-06-02
> **bobbocanfly said:**
> I got this problem with my FAT32 flash drive, i plugged it into Ubuntu, didnt work then wouldnt work in windows. Unfortunately I had to reformat the drive to get it working.

I sure hope this isn't the case... considering I have quite a lot of info on the external harddrive (backups of important data, etc) I may rip the old HD out and put it into my ubuntu box directly. The old NTFS drives in the box seem to work just fine.

But I would still like to figure out around this external HD situation.

---

### Post by SpacedMonkey on 2007-06-02
Well, all is not lost. The data is still on the HD, and I was able to move over my files. No idea why it no longer will connect to any Windows box that I have. This is kind of annoying.

---

