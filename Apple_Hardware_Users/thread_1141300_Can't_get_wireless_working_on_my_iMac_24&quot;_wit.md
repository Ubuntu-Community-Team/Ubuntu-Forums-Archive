---
title: "Can't get wireless working on my iMac 24&quot; with 9.04"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by tintin_uk on 2009-04-28
Hi,

Ubuntu newbie having trouble getting wireless working. On loading the desktop it appears that Ubuntu can't see my wireless connection. Terminal seems to suggest that the wireless card is DISABLED. However, if I go into Hardware Profiles it says that the Broadcom driver is active.

Can anyone help?

Not sure if its relevant but i'm dual booting Ubuntu through Boot Camp using Wubi.

Any help appreciated.

TT.

---

### Post by learning on 2009-04-28
[http://ubuntuforums.org/showthread.php?t=1138801](http://ubuntuforums.org/showthread.php?t=1138801)

see if my problem helps you any

---

### Post by tintin_uk on 2009-04-28
Yes, I did see your post originally and tried the terminal commands you listed but after typing the second line I got an error message so I wonder if we're having the same problem but in different ways.

Did any of the suggested ideas you were given work at all?

TT.

---

### Post by learning on 2009-05-08
I still have to type the terminal commands.  For whatever reason (guess I'm not smart enough), I can't get it to keep my settings after a reboot.

second command should also use sudo... sorry I left that out.

---

### Post by pxwpxw on 2009-05-08
> **learning said:**
> I still have to type the terminal commands.  For whatever reason (guess I'm not smart enough), I can't get it to keep my settings after a reboot.

second command should also use sudo... sorry I left that out.

The problem is that the ssb module keeps coming back.
On imac8,1 24inch, the cure was to folow your procedure and after running depmod -a, update initrd.img
```

sudo update-initramfs -u

```
That makes it stick.

---

### Post by tintin_uk on 2009-05-09
What worked for my 2.8ghz iMac was to disable the Broadcom driver, reboot, re-enable the driver and re-boot again. My wireless network was instantly picked up and no terminal shenanigans needed.

TT.

---

