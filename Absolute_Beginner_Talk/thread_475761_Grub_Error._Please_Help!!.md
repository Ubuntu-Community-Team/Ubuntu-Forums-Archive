---
title: "Grub Error. Please Help!!"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by bomb-24 on 2007-06-16
Re: Grub error 5 with new drive
I recently installed ubuntu on a flash drive. I didnt want to disturb my xp installation at all. I used a 4 gig flash drive, went through the installation process and when it rebooted and went to the grub menu it stated: grub loading stage 1.5
grub loading, please wait...
ERROR 5
What can I do?? I am out of options. I cant boot my xp now, all I have is the live cd to run. Can someone please help me?

---

### Post by gn2 on 2007-06-16
> **bomb-24 said:**
> I cant boot my xp now, all I have is the live cd to run. Can someone please help me?
.
Have you removed the flash drive before trying to boot XP?

If not, try booting XP with the flash drive unplugged.

If it still won't boot and you get a GRUB screen, it looks like you've installed GRUB to the Windows drive MBR.

A fixmbr from either a Windows CD or boot floppy or Super Grub CD should get XP booting again.

More info here: [http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk](http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk)

---

