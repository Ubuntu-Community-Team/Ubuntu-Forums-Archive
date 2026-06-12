---
title: "enable rtc"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by albesan on 2006-12-03
Hello team,

I'm trying to run this program for lighting programming called "Q light"
but I am getting the folowing output

~$ qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
vitut
open /dev/rtc: No such file or directory
open /dev/misc/rtc: No such file or directory


Does anybody now how to enable rtc? I've been looking into it and it seems to reffer to real-time clock.
any help would be great, thanks

a.

---

### Post by kebes on 2006-12-03
I know nothing about "Q light" but check if "/dev/rtc" exists and what the permissions are. On my system:
```

$ ls /dev/rtc -laF
crw-rw---- 1 root audio 10, 135 2006-11-15 17:41 /dev/rtc

```

I guess "Q light" needs access to "/dev/rtc" but looking at the file permissions (on my install of Ubuntu anyway), it doesn't look like ordinary users have access. If you ran your program with root privilege ("sudo qlc") this might fix the problem, but I don't know if you trust the program enough to run it as root.

I suppose you could try changing the permissions on "/dev/rtc" and see if that fixes your problem ("sudo chmod"). Also, if "/dev/rtc" doesn't exist on your system, then that's probably a problem!

---

### Post by albesan on 2006-12-04
hey thanks for the advice.
You are right it seems that RTC does not exist on my system...
I tought that the real-time clock was standard...

Now I'm really lost....

well thanks again.

a.

---

### Post by albesan on 2006-12-04
so... how can you make rtc so that it exist?
any idea??

ty.

a.

---

