---
title: "No luck-- Ubuntu 11.04, MacBook Pro 8,1"
date: 2011-09-21
forum: Apple Hardware Users
---

### Post by Samushighwind on 2011-09-21
I have been trying for weeks to install a working distribution of Ubuntu on my MacBook Pro 8,1.

I've tried everything.  I created partitions using Boot Camp and installed refit-- and then I burned a disc and I first tried 64-bit 11.04, which always showed the splash screen, but then the deadly:

> BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu9) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) Unable to find a medium containing a live file system.

I then tried 32-bit and 64-bit versions of 10.04, 10.10, and 11.04.  All returned the same problem, except one-- I was able to successfully install 64-bit 10.04.  I'm not sure why exactly this is, and I don't know if compatibility would also extend to earlier releases, but it seems like the most recent releases don't work well with my Mac.

But this would imply 10.04 *does* work well with my Mac.  Well, the ethernet works-- if I have an Apple USB ethernet adapter, which I temporarily stole from my roommate, plugged in.  Multitouch and right-clicking in general are screwed, so even if other drivers like visual effects and proper resolution detection were available, I wouldn't be using a truly functional operating system.

So I wiped the partition and started over.  I tried again with 11.04.  I read somewhere that booting it from a USB drive might solve my problem.  But "might" should have been "probably won't", since Apple computers don't seem to recognize that OS installers can be run off of external drives.  Every time I tried this solution in any way (selecting any of the many refit options that point to the same drive), I got "Non-system disk", which is not entirely helpful.

Convinced that my Macintosh could not install Ubuntu but a non-Macintosh certainly could, I went to install it on an external drive using my friend's Dell.  The installation actually worked perfectly.  I now have Ubuntu 11 installed on a hard drive.

But now I don't know what to do with this, or if I can do anything with it.  I have tried using dd in terminal to send my installation to my hard drive partition.

```
sudo dd if=/dev/disk1 of=/dev/disk0s4
```

I used "diskutil list" to find the drive identifiers, but I'm not sure if I wrote the of= correctly.  Whenever I hit enter, the operation appears to begin after I am asked for my password, and the entry field never reappears-- for over an hour.  I've given up waiting.

I need some sort of solution.  I really want to use Ubuntu on this computer.  Has anyone had luck that could aid my predicament?

Thanks

---

### Post by phthenry on 2011-09-21
I get the same problem:

> (initramfs) Unable to find a medium containing a live file system.

I was able to install the LTS 10.04 from the Ubuntu main download page, but this installation did not recognize either my ethernet card or my wireless card, so even though I had a working operating system, I had no internet connection. (I tried all the steps to get my broadcom card to work, but nothing helped.)

On other forms I have seen that one workaround to the "no live file system" problem *might be* booting from a USB device, but I have not tried this yet.

---

### Post by Samushighwind on 2011-09-22
I tried this, but I was unable to get it to load off of the USB device.  Do you have any idea how that would work?

---

### Post by phthenry on 2011-09-23
Here are the links I looked at. Apparently, you have to book from both the USB and the CD at the same time. I haven't tried this myself, so I can't be more specific. Sorry.

[link1]("http://ubuntuforums.org/showthread.php?t=1332782")

[link2]("https://help.ubuntu.com/community/LiveCDCustomization")

---

### Post by Samushighwind on 2011-09-23
I successfully followed the specific Mac instructions for creating the bootable USB.  The trouble is getting my Mac to recognize it.  I tried pressing C for CD and it just got stuck on a white screen for next to forever before reverting to the refit menu.

---

### Post by Samushighwind on 2011-09-24
I booted both at the same time, works now.  Thanks!

---

### Post by phthenry on 2011-09-24
Did you get everything to work? If so, maybe I will try it as well!

---

### Post by psrdotcom on 2011-10-10
[URL="http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/"]http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/
[/URL]
try this link, might be helpful ..

---

