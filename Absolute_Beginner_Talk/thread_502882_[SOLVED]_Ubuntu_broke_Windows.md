---
title: "[SOLVED] Ubuntu broke Windows"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Twisted-Daemon on 2007-07-17
Hey guys,

I've read around the forums and a few people have experienced this problem... but mine is slightly different.

I installed Ubuntu onto an external USB HDD via my laptop, which worked fine.

When the external USB HDD is plugged in I get the option to boot to either Ubuntu or Windows, when it's not plugged in however I get Grub stage 1.5 and then error 21.

I've looked at the forums and I need to reset the master boot record or something like that, but the Windows XP recovery disc that I have for my laptop doesn't do that, it simply reinstalls Windows and then at the first reboot I experience the same problem.

Also if I am booted into Windows  I can't access any of the files that are stored on the exernal HDD. So I'm finding it really hard to back stuff up right now.

Any help would REALLY be appreciated.

Thanks in advance.

---

### Post by Zzl1xndd on 2007-07-17
If your recover CD doesn't have a repair option then I can send you an ISO of what ever version of Windows you are using just added me to your favorite IM client.  After repairing the MBR Grub will be gone and you will have to reinstall it. As for your Hard drive did you let Ubuntu have the whole thing as it would use the Ext3 file system and windows can't read that with out extra's installed.

---

### Post by Jimmyfj on 2007-07-17
How did you partition the USB disk? If you allowed Ubuntu to take over the entire disk you'd have the EXT3 file system on that disk. Then you need a special prog to access your USB disk, but from Ubuntu you just need to install NTFS read/Write support.

As for the problems with GRUB - As you say yourself it works when you insert the disk, and doesn't work when you unplug it. That is because the GRUB info needed is stored on the USB disk. So for you to boot it every time you'll need the disk available at every boot.

---

### Post by punky on 2007-07-17
> **Twisted-Daemon said:**
> I installed Ubuntu onto an external USB HDD via my laptop, which worked fine.

I wouldn't recommend that, it would make your Ubuntu run really slow.


> When the external USB HDD is plugged in I get the option to boot to either Ubuntu or Windows, when it's not plugged in however I get Grub stage 1.5 and then error 21.

I should imagine its because it can't find Ubuntu because thre HDD is disconnected

> I've looked at the forums and I need to reset the master boot record or something like that, but the Windows XP recovery disc that I have for my laptop doesn't do that, it simply reinstalls Windows and then at the first reboot I experience the same problem.

Resetting the MBR would remove grub and force the computer to boot into Windows. You can do that by using the console on the XP disk or download a Windows boot disk and doing "fdisk /fixmbr" (Use at own risk, back up important files first, etc). However after that, if you go into your BIOS menu (press del of F12 or whatever it says when the computer first turns on), you might be able to change the boot order so that USB appears before HDD. That means if Ubuntu is connected, it will boot, and if it isn't, it will boot Windows.

> Also if I am booted into Windows  I can't access any of the files that are stored on the exernal HDD. So I'm finding it really hard to back stuff up right now.

You need the right drivers. Various ways/sites of doing it. Try googling with 

windows ext3 

or something like that, and it brings up a few sites like: [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

HTH.

---

### Post by Carlos Santiago on 2007-07-17
IMHO, you have to set the Windows option in /boot/grub/menu.lst correctly. Mine is:
```
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

```
Dont forget to save a BACK UP copy of your previous /boot/grub/menu.lst, for security.

---

### Post by Twisted-Daemon on 2007-07-17
Just want to say thanks to all you guys for your quick replies and help.

I managed to fix the master boot record using MbrFix ... After screwing with the syntax for a long time it rewrote the MBR to the usual Windows setup.

I can now boot up my laptop without it being connected to an external hdd :D

Thanks again

---

