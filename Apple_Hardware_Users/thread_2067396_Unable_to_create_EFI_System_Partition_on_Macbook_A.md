---
title: "Unable to create EFI System Partition on Macbook Air 3,1"
date: 2012-10-06
forum: Apple Hardware Users
---

### Post by gigabz666 on 2012-10-06
I'm having a hell of a time right now trying to get a bootable system on my wife's Macbook Air.

A few months ago, I was able to wipe OSX 10.7 completely from my wife's MBA and install Ubuntu 12.04 using this method to create a bootable USB drive. [http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/")

I then wanted to try the last version of OSX (Mountain Lion 10.8 ) because I had never properly played with a Mac OS before. I hated it, and wanted Ubuntu back. The problem is that now I'm unable to create a bootable system. I'm able to install Ubuntu, however I cannot create an EFI System Partition during the Ubuntu install. I have tried to use boot-repair to fix the issue but have been unsuccessful.

I'm just wondering if anyone else has had this issue. I've been wondering if the upgrade to 10.8 has somehow rewritten the BIOS to make it so this can't be done at all? I'm not sure but I would really love some help right now.

Thanks.

---

### Post by will1982 on 2012-10-06
I've had the same problem.

I just formatted the drive and tried again :3

---

### Post by gigabz666 on 2012-10-06
You wouldn't believe the amount of times I've formatted and tried over and over. Are you using GParted and creating a GPT partition table?

---

### Post by YannBuntu on 2012-10-09
Hello
What is the URL provided by Boot-Repair?

---

### Post by gigabz666 on 2012-10-10
> **YannBuntu said:**
> Hello
What is the URL provided by Boot-Repair?

[http://paste.ubuntu.com/1262872/](http://paste.ubuntu.com/1262872/)

That was the latest one. However I gave up trying to install Ubuntu without OSX installed. I reinstalled OSX, installed refit (refind wouldn't work) and then installed Ubuntu that way. I have it now running, but it's just annoying that I have to have OSX installed too to get it working.

---

