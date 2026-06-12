---
title: "ubuntu updates keep hosing my mini"
date: 2009-05-29
forum: Apple Hardware Users
---

### Post by imrazor on 2009-05-29
It seems that every time that my initial ramdisk gets updated, my ubuntu install gets hosed on my Mac mini (Core Duo 1.8GHz.) First a little background; first I tried installing 8.04 server, because I'd like to try using my mini as an smb/rsync/nfs/dns server. The initial install seemed to go well, and I successfully booted up 8.04 server. However, the very first update was a kernel update, and when I applied that and rebooted, my LCD TV started displaying "No Signal". No information, no hard drive activity, just "No Signal". 

So then I decided to try 9.04 Desktop. All went well initially, and I got the system up and running without a problem. I then decided to try Kubuntu (sudo apt-get install kubuntu-desktop), and everything seemed to proceed well. However, when I selected the penguin from refit, I got a couple of minutes of penguin, then "No Signal" again. I tried reinstalling grub both times (by booting off the CD, mounting the dead partition, chrooting to the partition, and then doing "grub-install /dev/sda3".) The only commonality I can find is that both the kernel update and the kubuntu update modified my initial ramdisk.

Anyone have any idea why apt-get updates keep hammering my mini? BTW, OS X boots happily every time, and, yes, I've tried re-syncing my partition with refit. Each time it says that no sync is required.

---

### Post by imrazor on 2009-05-30
Well, here's an update. I can now boot Jaunty - most of the time. The problem appears to be that GRUB is not initializing video properly at boot time. Or maybe that's rEFIt's job.

To be a bit more detailed, I struggled for a while and then found that I could boot while holding down the enter key AFTER rEFIt's penguin disappeared. I tried various fixes (changing the splash screen, turning on the nosplash option in grub's config file, etc.) Eventually I got it to the point where it would display a blank screen for 3-4 minutes at boot, and then eventually come to the gdm login screen. I could then login and use X normally, but I couldn't access virtual TTYs - I just got a blank screen when I tried. For now, gdm will eventually come up ... most of the time. I'm going to do some more research to see if this is a known problem with rEFIt or grub.

---

### Post by imrazor on 2009-05-30
Alright, I seem to have found a fix. I'm not sure whether to blame rEFIt or grub, but to get console video initialized what I've done is specified the 'textonly' option in /efi/refit.conf on my HFS partition. The text screen is much uglier than the GUI menu, but, hey, it works. I'm hoping this post may help someone out in the future.

---

