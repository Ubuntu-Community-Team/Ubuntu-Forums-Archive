---
title: "ubuntu on external hard disk, auto boot to xp when no ext HD detected"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by user_jeff on 2007-05-10
Hi,

I just installed ubuntu successfully on an external HD yesterday, and it works just fine. This is my first experience with Linux and it looks so nice =D.

My question is, how do I set my comp to automatically boot to XP when I'm not using my external HD? Is there any way to solve this? Because I'm using laptop, and I'm on my external HD when I'm in office.

Thank you,

Jeff

---

### Post by mikewhatever on 2007-05-10
What happens if the external HD is not connected? Do you get error 21 from grub or somethig?

---

### Post by user_jeff on 2007-05-11
Yes, when ext HD not detedted, it shows error 21. And i can't do anything except turn my laptop off or ctrl+alt+del (and error 21 show up again).

---

### Post by confused57 on 2007-05-11
> **user_jeff said:**
> Hi,

I just installed ubuntu successfully on an external HD yesterday, and it works just fine. This is my first experience with Linux and it looks so nice =D.

My question is, how do I set my comp to automatically boot to XP when I'm not using my external HD? Is there any way to solve this? Because I'm using laptop, and I'm on my external HD when I'm in office.

Thank you,

Jeff

You'll need to restore Window's IPL code to your internal hard drive mbr in order to boot without the external drive attached:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You won't be able to boot the external hard drive, without installing grub to the drive's mbr & your bios is able to boot first to your external drive.

Another alternative is to use the Super Grub Disk to boot your external hard drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you want to try installing grub to your external hard drive's mbr, you can use the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

