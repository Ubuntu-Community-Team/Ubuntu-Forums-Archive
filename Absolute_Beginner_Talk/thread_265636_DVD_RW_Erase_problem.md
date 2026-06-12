---
title: "DVD RW Erase problem"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-09-26
I am using Ubuntu Dapper 6.06lts. Novice user of Linux.
I have a problem with DVD RW disks in that once I have burned data to the disk no program I use including Gnomebaker, K3B and even NeroLINUX, will erase the disk and reburn. K3B gives me the trumpet but nothing actually happens.
I also get an error from NeroLINUX saying on startup that it cant access /dev/sg0 Generic device and cant access /dev/sg1 Generic Device.
I don't have any problems burning cd's or DVD blanks but the problem seems to be only ersing and reburning DVD's.
I dont have any problems using Nero on Win XP as RW DVD work fine there.
Can anyone please give me some advice for this problem. Have I some kind of permissions setup problem with the drives or a mounting problem. Has to be something with my setup as all three progs are the same. I have tried DVD +RW and also DVD-RW various brands, same same.

---

### Post by xyz on 2006-09-26
> sudo umount /dev/cdrom
cdrecord dev=/dev/cdrom blank=fast
in a terminal.
Learned it from the Ubuntu Dapper Guide if you want to check.

---

