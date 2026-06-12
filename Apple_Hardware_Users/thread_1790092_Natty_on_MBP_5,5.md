---
title: "Natty on MBP 5,5"
date: 2011-06-24
forum: Apple Hardware Users
---

### Post by Bachstelze on 2011-06-24
So yesterday I installed Natty on my MPP 5,5 and I forgot to tell the installer to install GRUB on the boot sector of the Ubu partition, so I installed it on the MBR and got the now-infamous need-to-hard-reboot-5-times bug: 

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

Restorig the firmware Worked For Me™, but apparently not for everyone, so I'd rather not take chances. Can anyone confirm that isntalling Natty with GRUB on the boot sector of the partition works fine on a 5,5? Otherwise I guess I'll just stay with Maverick.

Thanks

---

### Post by johnmurrayvi on 2011-06-24
Which version/disk did you use? I believe the Mac alternative disk has this is fixed.

---

### Post by Bachstelze on 2011-06-24
I used the standard desktop image as I always do. I will try the Mac one, thanks.

---

