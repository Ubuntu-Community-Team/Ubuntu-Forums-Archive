---
title: "dualboot set-up MacOS9/Ubuntu"
date: 2006-07-23
forum: Apple PPC Users
---

### Post by arsche on 2006-07-23
Been wondering whether there are people using a dualboot set-up with MacOS9 and Ubuntu. Also is there a way of achieving this without loosing access drivers in MacOS9 for printing (Epson). Can you make a partition from with Ubuntu an later install MacOS9, or has it to be the other way around.

thanks
arsche

---

### Post by ubuntu-geek on 2006-07-23
This might get you going in the correct direction.

[http://ubuntuforums.org/showthread.php?t=93309](http://ubuntuforums.org/showthread.php?t=93309)

---

### Post by 3rdalbum on 2006-07-24
To dual-boot OS 9 and Ubuntu, you must back up all your OS 9 data, partition your disk (the part of the disk which you want Ubuntu to use should be "unallocated"), install OS 9, then install Ubuntu. As long as you install/copy back your drivers for the Epson printer, it should still work fine.

I *think* it's okay to install OS 9 after Ubuntu, except that the computer will then boot into OS 9 unless you intervene. I purposely set it up this way on my old iMac, and then to get into Ubuntu I started the computer up with Cmd-Opt-O-F held down, and typed this in the prompt:

boot hd:6,yaboot

(the number may vary for your computer, just keep trying numbers until it works).

However, I would recommend installing OS 9 before Ubuntu.

---

