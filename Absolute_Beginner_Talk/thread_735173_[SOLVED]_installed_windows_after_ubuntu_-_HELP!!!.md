---
title: "[SOLVED] installed windows after ubuntu - HELP!!!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by shedokan on 2008-03-25
I installed windows after I installed ubuntu of another partion and then I recovered grub using this:
[http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

but now I can't dual boot windows and ubuntu.

please help!!! I need it fast

thanks.

---

### Post by OffAxis on 2008-03-25
What's it do?
As in, where does it fail?
Does grub come up?

More information is needed.

---

### Post by shedokan on 2008-03-25
at the start it only booted windows but when I recovered grub it only boots ubuntu.

---

### Post by shedokan on 2008-03-25
bump, please!

---

### Post by TeoBigusGeekus on 2008-03-25
[http://ubuntuforums.org/showthread.php?t=733218]("http://ubuntuforums.org/showthread.php?t=733218")

---

### Post by shedokan on 2008-03-25
what should I add to the grub menu list?

here is my "sudo fdisk -l":
```
Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43df43df

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       12158    97659103+  83  Linux
/dev/hdc2           12159       12280      979965   82  Linux swap / Solaris
/dev/hdc3   *       12281       19456    57641220    7  HPFS/NTFS


```

thanks.

---

### Post by TeoBigusGeekus on 2008-03-25
title     Windows NT/2000/XP (loader)
root          (hd0,2)
makeactive
chainloader   +1

---

### Post by shedokan on 2008-03-26
thanks!
and one last thing, what is the "quiet" option?

thanks.

---

### Post by TeoBigusGeekus on 2008-03-26
No idea.

---

### Post by shedokan on 2008-03-26
ok but thanks anyway!

---

