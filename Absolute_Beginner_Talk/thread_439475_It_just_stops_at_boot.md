---
title: "It just stops at boot"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2007-05-10
Okay here's all the info I got.

first it says: > Unable to locate RSDP

Then it goes to the boot loading thing but it doesn't seem to load at all.

then it comes up with this message:

> ata1.00:        exeption Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
ata1.00:        (BMDMA stat 0x64)
ata1.00:        cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096


BusyBox v1.1.3 (Debian 1:1.1.3 -3ubuntu3) built-in shell (ash)
Enter 'help' for a list of built in commands

/bin/sh: can't access tty; job control turned off
(initramfs) [  324.021448] Buffer I/O error on device sda, logical block 0
ata1.00:        exeption Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
ata1.00:        (BMDMA stat 0x64)
ata1.00:        cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096

ata1.00:        exeption Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
ata1.00:        (BMDMA stat 0x64)
ata1.00:        cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096
[384.277512] Idm_validate_partition_table(): Disk read faild


I installed it from a DVD I bought from Linuxcd.org. I installed this after a year of using Ubuntu edgy.
Also I have dial-up so I can't download the alternative install cd

Does anybody know what's going on?
thank you so much

---

### Post by lakersforce on 2007-05-10
I dont think anyone can help you with that error. No one knows what is causing it. Canonical did a real bad job on Feisty Fawn there. I would recommend 6.06 or 6.10.

---

### Post by fakie_flip on 2007-05-10
Try searching some of your error message in Google and this forum.

---

### Post by Mazehero55 on 2007-05-10
well that sucks, and after I paid $10 on an install DVD too!

So nobody knows anything on how to fix this?

---

### Post by fakie_flip on 2007-05-10
> **Mazehero55 said:**
> 
I installed it from a DVD I bought from Linuxcd.org. I installed this after a year of using Ubuntu edgy.
Also I have dial-up so I can't download the alternative install cd

Does anybody know what's going on?
thank you so much

If you are patient on waiting, then go here, and get Feisty sent to you in the mail for free.

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Edit: Maybe I read wrong. At first I thought you bought a DVD of Edgy, but maybe the DVD you bought was Feisty.

---

