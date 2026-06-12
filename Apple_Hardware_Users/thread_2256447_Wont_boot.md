---
title: "Wont boot"
date: 2014-12-12
forum: Apple Hardware Users
---

### Post by marko17 on 2014-12-12
Good day,
Ive spent days trying to install Ubuntu on my macbook pro. Clean install, no other OS, Installed fine (first I did 12.04.01 lts...worked for a week, updated kernel - recommended update)...would not boot. Tried same distro again, no luck, downloaded 12.10, installed fine, wont boot...flashing cursor. 

Rant boot repair, created boot-grub flag, rebooted....black screen. Wont go. 

Here is my log.

[http://paste.ubuntu.com/9493064/](http://paste.ubuntu.com/9493064/)

Please help. I know its something simple, but Ive been starting at this for days, and Im stuck.

Thank you ,


Marko

---

### Post by marko17 on 2014-12-12
Just an update....it booted...but it took forever (it was 20 mins...I left for lunch and we I got back it was up) Anyone?

---

### Post by oldfred on 2014-12-15
Moving thread to Apple sub-forum.

Do not know Mac.

But it looks like you have converted from UEFI boot to BIOS boot. I thought with a Mac UEFI was prefered. And with your BIOS boot you seem to have the hybrid MBR/gpt configuration which is not required as Ubuntu works with gpt. Only Windows has to have the hybrid configuration as it only boots in BIOS mode with Mac.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

Only 12.04 & 14.04 are LTS supported. the 12.10 is obsolete and would not work as the repositories are closed for updates. Only use current versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

