---
title: "[SOLVED] My computer has crashed..."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-11-14
kinit: No resume image, doing normal boot...
Done.
[16.096621] kjournals statring. Commit interval 5 seconds
[16.096680] EXT3-fs: hda2: orphan cleanup on readonly fs
[16.172037] usb 2-1: new full speed USB device using ohci_hcd and address 4
[16.376840] usb 2-1: configuration #1 chosen from 1 choice
_

That is the last 6 rows I get in the recovery mode when i try to boot up...
I got this problem after I had tried to get a secondary screen to work and it told me to reboot and then it didn't work. :(
The normal ubuntu live cd crashes when it tries to boot too... But I can get the nubuntu 6.10 live cd to work.
Anyone who knows how to fix this?

---

### Post by staticsage on 2007-11-14
Do you have any peripherals plugged into your computer? The first thing I would try is to remove any devices (USB devices particularly). Try to boot without the USB devices plugged in. I'm not really sure if it would help, but from the log you pasted it looks like it's hanging when trying to access a usb device. Are you running off of an external hard drive?

---

### Post by spydon on 2007-11-14
Nope, nothing is plugged in. All usb ports is empty. But when I first rebooted it the two last rows wasn't there.
And no i'm not running from an external harddrive.

---

### Post by staticsage on 2007-11-14
I found this post: [http://ubuntuforums.org/showthread.php?t=467521](http://ubuntuforums.org/showthread.php?t=467521)

The user was having the same issue as you. The commands found in post#15 may be of some help if you can get your system booted from a live CD. Perhaps try knoppix [http://www.knoppix.org/](http://www.knoppix.org/)

When burning the CDs, burn them at a slow setting to avoid any errors on the media.

---

### Post by spydon on 2007-11-14
Thx I hope it will work, I have a whole bunch of live cd's to test with :).

---

### Post by spydon on 2007-11-14
It worked! Thank you very much staticsage!!!! :D

here is the commands if anyone else stumbles over this thread:

Run these too:
```
sudo e2fsck -f -y -v /dev/hda2
```

and

```
sudo e2fsck -C0 -f -p -v /dev/hda2
```
And thank you Herman who came up with these commands in the other post :)

---

