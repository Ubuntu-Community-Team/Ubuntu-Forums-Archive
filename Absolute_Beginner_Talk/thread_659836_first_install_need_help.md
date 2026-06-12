---
title: "first install need help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by xmunk on 2008-01-06
having problems with bootloader keep getting "error 21 disk not found"
tried following some instructions about reinstalling grub but didn't work.  can't boot into windows or linux.  

im pretty new to linux and to be honest the hard drive numbering is confusing to me.  my setup is on sata drive split in two partitions with windows on the first.  any help would be greatly apreciated im really frustrated so ill be lookin foward to your posts in the morning.  ;)

---

### Post by zasf on 2008-01-06
If the hard drive numbering confuses you, it's time to deepen the subject a bit.

Boot with the live cd and use 'partition editor', it'll give you a picture of your hard drive, its partitions and numbers.

After that, I would take a look at grub's settings (the bootloader). Did you manually change them? Didn't the install process configure it automatically?

---

### Post by Daveth on 2008-01-06
or, if you are lazy

```
sudo fdisk -l
```

which will list them. Your sata will be showing up as sda

---

### Post by Sef on 2008-01-06
Windows XP or Vista?  If the latter, then you need to use its own partitioner to partition.  Did you do that?  What guide did you follow?

---

### Post by xmunk on 2008-01-06
when i restarted from install grub was simply not there so i tried [http://ubuntuforums.org/showthread.php?t=609548]("http://ubuntuforums.org/showthread.php?t=609548")
when i did the find command in grub it came up with (hd0,1) so i continued the instructions with that and grub installed.   upon reboot grub loads gives me options to boot to ubuntu and xp but when i select either thats when i get the error 21.

originally during install i thought grub was manually installed.  i started with 2 windows partitions the second of which i deleted in xp before i tried to instal ubuntu.  ubuntu found the empty space with no problem partitioned it and install seemed to be flawless.  just no way to select the operating system.

---

### Post by Daveth on 2008-01-06
so, when you ran the grub find command bit, did you get all of this sort of stuff afterwards?

"Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done."

You did remember to do the setup part of that grub procedure I take it. With such a simple disk setup I'm not sure why it is not working.
Your error, if you want to read about it, is here

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

