---
title: "Windows 7 does not work after installing Ubuntu 12.04"
date: 2012-08-13
forum: Apple Hardware Users
---

### Post by EmperorKush on 2012-08-13
Windows 7 won't run after I installed Ubuntu, I've triple booted on my Macbook and I installed Windows before Ubuntu.

I used BootRepair and got this report:
[http://pastebin.ubuntu.com/1145708](http://pastebin.ubuntu.com/1145708)

I have no idea what to do, I'm a beginner to all this and I would really appreciate any help.

Thanks.

---

### Post by oldfred on 2012-08-13
Moved to Apple sub forum.

I do not know Macs but they use a hybrid gpt/MBR system as the Mac is booting an older UEFI but boots Windows in MBR. Only the first 3 or 4 partitions then are synchronized. But Windows has to be in the MBR part of the drive and if sda5 is in the gpt only part.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

