---
title: "Windows reports an error through dualboot"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by MysticAurora on 2007-03-03
Hi. I've attempted to dualboot Windows and Linux again. This time, I've come very close to getting Windows working. I'm positive Linux works, but Windows refuses. It may have something to do with how GRUB rewrites the MBR or something. I'm not sure, but when I go to boot Windows, it gives me a blue screen with a big, ugly error:

```
A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:

*** STOP: 0x0000007B (0xF7C4F640 0xC000000E, 0x00000000, 0x00000000)
```

Windows was loaded through GRUB 1.5 with the following settings:

```
rootnoverify (hd0,0)
makeactive
chainloader +1
```

My hard drive is setup as follows:

```
Partition #1: Windows
Partition #2: Linux
Partition #5: linux-swap
```

I have no idea what could be causing this, as I told GRUB to install itself to /dev/sda. I had tried (hd0) before, and it didn't work. Is there anything I can do to finally get this dualboot setup finished?

EDIT: The OSes in question are Windows XP (no SP1/2) and Ubuntu Edgy Eft 32-bit (LiveCD).

---

### Post by oilchangeguy on 2007-03-03
google the error number, or search microsoft's knowledge base.

---

### Post by MysticAurora on 2007-03-03
GRUB doesn't spit an error at me. Windows does.

---

### Post by oilchangeguy on 2007-03-03
ok, great. the bsod comes up when you try to boot windows. thats why i tried to point you in the direction to get help to find out what the error message means. nobody here is going to be able to decode the message.

---

### Post by louieb on 2007-03-03
XP Service Pack 2 fixed a lot of problems. One thing window does is keep a copy of the MBR and partition table. It probably freaked out when it saw it is different. And that just my wild as guess of the day.
Have an XP CD? Google recover Windows.

---

