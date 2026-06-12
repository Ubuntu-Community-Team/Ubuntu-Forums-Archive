---
title: "Wrtiting capabilities from Windows"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-03-07
I've been using ext3 for quite some time and with the ext2 ifs driver, it's been extremely stable for me to 
write to this partition from Windows. My question is, what is the current status of drivers for filesystems 
such as Reiserfs? Everything I read about is about 2 years old and I wanted to find a current status 
regarding the matter. I'm interested in the Reiserfs, but need to write to it from windows at work.

Thanks for your help!

---

### Post by Oldsoldier2003 on 2008-03-07
> **shanepardue said:**
> I've been using ext3 for quite some time and with the ext2 ifs driver, it's been extremely stable for me to 
write to this partition from Windows. My question is, what is the current status of drivers for filesystems 
such as Reiserfs? Everything I read about is about 2 years old and I wanted to find a current status 
regarding the matter. I'm interested in the Reiserfs, but need to write to it from windows at work.

Thanks for your help!
I wouldn't write to any non windows FS from windows if i could help it. if you need a shared partition for data you are better off writing from windows to a fat32,NTFS, or a samba share.

---

### Post by gpilkay on 2008-03-07
While it doesn't really help with the specific problem, I worked around it in my own system by using a thumb drive stuck in the back.  Anything can read the USB drive, so I just move files from Windows to it, then to the other system.  Made life less hectic.

---

### Post by SunnyRabbiera on 2008-03-07
it might be best to keep ext3 for ubuntu as XP will read it like a fat32 system, the others are not so fortunate.
from what i know ext3 has a lot of similarities to fat32 but does not inherit its flaws.

---

### Post by shanepardue on 2008-03-07
> **gpilkay said:**
> While it doesn't really help with the specific problem, I worked around it in my own system by using a thumb drive stuck in the back.  Anything can read the USB drive, so I just move files from Windows to it, then to the other system.  Made life less hectic.
Your thumb drive is fat32.

I'd have to say the ext2/3 driver worked great and I didn't see a problem with it's read/write capabilities. If the Reiserfs drivers don't work properly, I'll revert to ext3.

---

### Post by HuwSy on 2008-03-07
my experience with ext2 ifs, and probably anyother windows driver for a journalised filesystem, is that when windows crashes it doesnt complete the journal writing properly and ends up widing out a whole lot of data on the drive if it was in the middle of a write action. This happened a few times during windows updates when it got a bit confused about the driver an killed a partition completely, well almost, there probably was some recoverable data but it had only just been backed up so i never really looked at how much of a mess it had actually made.

the downside of ntfs with ntfs-3g is that you need a clean shutdown from windows to be able to mount it under linux, so if you crash in windows then you have to reboot into windows to shutdown nicely before use.

personally id stick with a san or dedicated file server type arangement so theres less risk of data loss from an os falling over, and gives anyone you trust on the network access.

---

### Post by shanepardue on 2008-03-07
> **HuwSy said:**
> my experience with ext2 ifs, and probably anyother windows driver for a journalised filesystem, is that when windows crashes it doesnt complete the journal writing properly and ends up widing out a whole lot of data on the drive if it was in the middle of a write action. This happened a few times during windows updates when it got a bit confused about the driver an killed a partition completely, well almost, there probably was some recoverable data but it had only just been backed up so i never really looked at how much of a mess it had actually made.

the downside of ntfs with ntfs-3g is that you need a clean shutdown from windows to be able to mount it under linux, so if you crash in windows then you have to reboot into windows to shutdown nicely before use.

personally id stick with a san or dedicated file server type arangement so theres less risk of data loss from an os falling over, and gives anyone you trust on the network access.
This is just an external hard drive though..I'm not looking for a hardcore option such as a san.

Thanks anyway.

---

