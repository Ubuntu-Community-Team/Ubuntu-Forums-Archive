---
title: "External Harddisk PLEASE HELP!"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by hcwegge on 2008-01-13
Hi. I'm pretty new to ubuntu but have played a little with the terminal so I know a few basic things(VERY basic)... I have been using my Western Digital external harddisk for a week or so but now suddenly it started saying "read-only" so now I can't create folders nor copy anything to the harddisk. I have tried to set the permissions but they are already on "create and delete files" so I dont understand how I am not allowed to use it. As I said it has worked before so its very odd...
The filesystem on the external harddisk is .vfat and I'm running ubuntu gutsy 7.10.

Please help me someone!!!

HC

---

### Post by candtalan on 2008-01-13
I not an expert but can offer a few comments which may lead to some help:

- How is the external Hard drive connected - by LAN ethernet cable or by USB connection?

- is the drive used only ever by ubuntu (Linux that is) or is it also used by windows sometimes?

- The drive filesystem is vfat so if the file system has somehow got damaged, then there is a fair chance that a tool such as scandisc might repair it.

- note that the permissions reported by linux may be a bit unusual  because I think the vfat filesystem does not support all the permissions etc etc that linux filesystems do

- note that permissions of a high level directory may not be the same as permissions of the directory contents  - lower directories or files. directories might be different to each other for permissions. Check that you were using the same directories or files on the earlier occasions?

hth

---

### Post by hcwegge on 2008-01-13
I just tried booting into windows and there it worked with writing onto the harddisk. It's connected through a USB-cable...
 Do you know what it can be then? I also ran the scandisk in windows...

---

