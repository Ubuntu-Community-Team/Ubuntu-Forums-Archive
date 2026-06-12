---
title: "Multiple booting problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-02-14
Please help

I recently installed 64 bit version of gusty, I was in gparted in that version adding extension partions, now when i reboot, 64 bit version wont boot, I also had deleted my 32 bit version. I had both setup

All that happens when I reboot is ubuntu starts to load then i get a black screen and my computer makes noise and does nothing, also after rebbot my windows is corrupted and a file is missing. I know my partitions are fine because i can boot from the live 32 bit cd and see all my files.

Another weird thing is that i can't boot from the 64bit live cd, the excat same problem as the regular.

---

### Post by randy78 on 2008-02-14
> **anderskitson said:**
> Please help

I recently installed 64 bit version of gusty, I was in gparted in that version adding extension partions, now when i reboot, 64 bit version wont boot, I also had deleted my 32 bit version. I had both setup

All that happens when I reboot is ubuntu starts to load then i get a black screen and my computer makes noise and does nothing, also after rebbot my windows is corrupted and a file is missing. I know my partitions are fine because i can boot from the live 32 bit cd and see all my files.

Another weird thing is that i can't boot from the 64bit live cd, the excat same problem as the regular.

Did you right click the proper partition, select Manage Flags and put a check mark next to boot?

Try that and let us know

---

### Post by anderskitson on 2008-02-14
ok well, the 64bit wasn't flagged as boot, but i restarted and still have the same problem, was marked as boot, but still corrupted

---

### Post by randy78 on 2008-02-14
When you say corrupted, do you mean that Windows will not boot?

Type out the error message it gives you, so I can see what's going on...

It sounds like your MBR was written over by Ubuntu, which is common if you aren't careful, and now Windows won't boot...

Let us know

---

### Post by anderskitson on 2008-02-14
Ok Heres what I know

In Gparted

Sda2 Is Linux swap
Sda3 Is Ntfx (windows xp)
Sda4 is ext2 (gusy 64bit)

The windows error is
windows root \system32\hal.dll
Please install file

---

### Post by anderskitson on 2008-02-14
allright i have fixed windows boot, i had to go into my boot.bin file and change  defaults to partition 2, becuase I formatted partition 1  and bumped everything down 1. But still having problems with 64bit boot regular or live cd

---

### Post by anderskitson on 2008-02-14
Update:
I have gotten rid of the splash menu for the 64bit, and now it goes through a whole bunch of text lines, i get this error
dev/sda4 was not clenanly umounted
check forced
0.6% not contigius
fsck died with exit status 1

fsck 1.40.2
fsck.ext2 unable to resolve (a bunch of numbers)
fsck died with exit status 8

---

### Post by anderskitson on 2008-02-14
Fixed i hope:

I just typed reboot in, and it started up fine so hopefully next time i restart it works fine

---

### Post by anderskitson on 2008-02-14
ok well im still getting the same error when booting, how to i unmount it properly when im running it

---

