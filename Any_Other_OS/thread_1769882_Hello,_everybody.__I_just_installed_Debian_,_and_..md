---
title: "Hello, everybody.  I just installed Debian , and ......."
date: 2011-05-28
forum: Any Other OS
---

### Post by ecr959 on 2011-05-28
I wanted to say hello.  I am a long-time Ubuntu user and member of this forum, but the latest ver (11.04)  has made me stray .. I installed Debian Squeeze today.  As my one and only distro/partition. 

Any tips or dos and don't from here ?   The install went well, I solved a couple  of little things already, but I have one biggie that someone here might help me with.

I made my full data backup on a flashdrive, while I still had Ubuntu.  Now Debian says it can't read it.  "bad superblock" it says.  I looked at dmesg and it said "no VRS found".  I ran Disk Utility, that says the flashdrive is OK.   I took the flashdrive to my daughter's PC, which has Windows on it, the flashdrive and all the data on it was recognized OK.    So I think the problem is Debian assumes my flashdrives are formatted with ext 2 or ext 3,  when this flashdrive is formatted with FAT32.    Am I right ?  I think Ubuntu is flexible in this and will mount it.

What do I tell Debian so it will mount this FAT32 flashdrive ?
It loads OK on a Windows pc, so its not corrupted.  
I will appreciate any help or suggestions.:D

---

### Post by satanselbow on 2011-05-28
If you can read the data on your Windows machine why not just copy the data across - reformat the drive and try again?

Doesn't actually explain what has happened but will verify your data is safe...

---

### Post by PhilGil on 2011-05-28
This post might help.
[http://forums.debian.net/viewtopic.php?f=7&t=60190](http://forums.debian.net/viewtopic.php?f=7&t=60190)

From the thread on the Debian forums, it appears that a USB device will not auto-mount if there is already an entry for the device identifier in fstab. The solution is to comment out (or delete) the fstab entry for the device.

Cheers

---

### Post by wojox on 2011-05-28
Debian forums is usually a good place to look. [Unable to mount new Volume]("http://forums.debian.net/viewtopic.php?f=7&t=60190")

---

### Post by ecr959 on 2011-05-28
> **wojox said:**
> Debian forums is usually a good place to look. [Unable to mount new Volume]("http://forums.debian.net/viewtopic.php?f=7&t=60190")

Thank you, WOJOX.  I just joined the official user mailing list, and I will also join at this link you gave me.  I read it, understood that I have to edit out a certain line in FSTAB.  I'm gonna try tonight, after dinner.

Thanks

---

### Post by ecr959 on 2011-05-28
Thank you Phil.  I know my data is safe.  I copied it all from the flashdrive to a SD card, but Debian wouldn't read that either.  The copy process flew by without problems reading or writing.

I think I found my solution. Read below.

---

### Post by ecr959 on 2011-05-28
Thank you Satan,  I got the answer from a Debian user forum.  Since I did my install from a usb flashdrive, there is a line in FSTAB that is causing this problem. I will edit out the line, that should do it.

---

### Post by strungoutfan78 on 2011-07-03
Thanks so much for posting your solution!  I just did the same thing on a Debian Squeeze install from a USB drive.  The fstab entry had /dev/sdb1 listed as a cdrom drive for the install.  I would think the post-install scripts would take care of this but apprently not.  Anyway, kudos.:KS

---

