---
title: "iRiver X20 woes"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by emnaki on 2007-03-17
I've tried everything suggested by these forums to try to get my iRiver device to work with amarok.
I've recompiled amarok, now it has the option iRiver iFP Media Device. But when I try to connect the device, it gives the following error: 'iFP: A suitable iRiver iFP device could not be found'. I've set the pre-connect command as 'sudo mount /dev/sdb /mnt/sdb'. I'm also running amarok as root.
Also running ifp command gives me this
```
kchik@kchik-desktop:~$ sudo ifp ls
Password:
info: ignoring device with UMS firmware.
A suitable iRiver iFP device couldn't be found; perhaps it's unplugged or turned off.
```

Note that ubuntu sucessfully detects the device and sucessfully automounts it.

This is so frustrating!!! I'll probably never buy an iRiver again!

---

### Post by Kateikyoushi on 2007-03-17
Did you check their website for newer firmware ? I updated mine (not same model) and it now functions as a thumbdrive, can write to it with nautilus.

---

### Post by emnaki on 2007-03-17
Yes I can right to it like I can write to any usb drive, but my aim is to make it work with a music management software, (preferable amarok since it is my prefered music player).

---

### Post by today53 on 2008-02-08
hi 

I have the same player and never managed to transfer anything to it.

How did you manage to get it working and transfer files to it?

Have been search the internet for sometime and have not been able to find a solution.

would really appreciate your help.

cheers
roger

---

### Post by mozetti on 2008-02-08
I don't use Amarok, but since it has so many advanced features I'd think it would be able to handle syncing music to a UMS media player, no? If amarok can sync files to any UMS device (like a USB stick, USB hardrive, etc) then you wouldn't need the iFP kludge - just use your x20 like any other UMS device.

Like I said, I don't use amarok, but it seems like UMS syncing would be an easy feature to have. Maybe it doesn't, though.

---

