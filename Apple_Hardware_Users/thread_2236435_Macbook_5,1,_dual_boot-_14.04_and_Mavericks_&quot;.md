---
title: "Macbook 5,1, dual boot- 14.04 and Mavericks &quot;Still waiting for root device&quot;"
date: 2014-07-26
forum: Apple Hardware Users
---

### Post by caluminium on 2014-07-26
Hi all, thanks so much in advance for having a look at this problem for me.

I followed the instructions on [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) and also had to use this thread [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229) to attempt to fix the partitions.

I can now boot ubuntu perfectly well via grub, but can not boot to Mac OS anymore. I got part way through and got the message "Still waiting for root device". I installed and ran boot-repair, and got this - [http://paste.ubuntu.com/7870040/](http://paste.ubuntu.com/7870040/)

Restarted, same problem in OS boot, but ubuntu still is fine.

Any tips on what I should try next?

Cheers.

---

### Post by este.el.paz on 2014-07-27
> **caluminium said:**
> Hi all, thanks so much in advance for having a look at this problem for me.

I followed the instructions on [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) and also had to use this thread [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229) to attempt to fix the partitions.

I can now boot ubuntu perfectly well via grub, but can not boot to Mac OS anymore. I got part way through and got the message "Still waiting for root device". I installed and ran boot-repair, and got this - [http://paste.ubuntu.com/7870040/](http://paste.ubuntu.com/7870040/)

Restarted, same problem in OS boot, but ubuntu still is fine.

Any tips on what I should try next?

Cheers.

I don't know too much about CLI stuff, but quickly looking at what you've posted, it looks like you have Ubuntu up front on the HD . . . ???  I've done a few dual boot and triple set ups on a few computers and it seems like the general wisdom is . . . put OSX up front . . . install it first . . . then add the linux system in the partitions after the first one.  Depending on which iso you have you may need rEFInd to help boot the non-EFI systems . . . .  OSX doesn't play well with others, so putting it in after the linux install seems to mess stuff up . . . .  I just used Disk Utility to cut the HD up . . . putting the OSX in HFS+ format . . . and the linux as "Free space" or "FAT" . . . whatever the options are.  OSX in sda1 or whatever, and linux in 2, 3, with something for GRUB, etc.

e.e.p.

e.e.p.

---

