---
title: "Xubuntu: Cannot unmount/eject external hard drive - URGENT HELP PLS!"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kenwong on 2007-11-15
as topic.

---

### Post by FuturePilot on 2007-11-15
Is there any type of error that you get?

---

### Post by Inxsible on 2007-11-15
have you given it enough time. Maybe its writing some data on the drive.

---

### Post by kenwong on 2007-11-15
It says "cannot unmount volume" and "there is data that needs to be written to the device ..."

---

### Post by Inxsible on 2007-11-15
> **kenwong said:**
> It says "cannot unmount volume" and "there is data that needs to be written to the device ..."Give it some time and then try again.

---

### Post by kenwong on 2007-11-15
Already 2 hours.

---

### Post by kenwong on 2007-11-15
What if I simply unplug the USB cable or shut down my computer?

---

### Post by Inxsible on 2007-11-15
> **kenwong said:**
> What if I simply unplug the USB cable or shut down my computer?if your USB drive has an on-off switch, use that to switch it off before you try unplugging the USB cable

---

### Post by kenwong on 2007-11-15
There is no.

So, what should I do?

---

### Post by Inxsible on 2007-11-15
> **kenwong said:**
> There is no.

So, what should I do?Shutdown your computer, I guess, and pray that nothing goes wrong :)

Most times its ok to do this, although it can damage your drive, if you do this often

---

### Post by kenwong on 2007-11-15
I tried sudo eject and here are the results:

ken@ken-laptop:/root$ sudo eject /dev/sdb1
umount: /media/LACIE: device is busy
umount: /media/LACIE: device is busy
eject: unmount of `/media/LACIE' failed

---

### Post by markharding557 on 2007-11-15
go into system monitor processes,find the process that is using the drive and kill it.
you should then be able to unmount it

---

### Post by schorsch on 2007-11-15
What is the output of
```
lsof /media/LACIE
```
in a terminal?

---

### Post by kenwong on 2007-11-15
Hi, markharding557, I finally need to shut down my computer just a couple of hours of ago before you posted.

Before I shut it down, I went into System Monitor and did a few clicks then closed Firefox. I don't know which action(s) matter but anyway I was then able to unmount the drive. But still it was there and I tried to eject it in Terminal but failed.

I suppose I should also eject it although it has been unmounted.

Did I used the wrong command or what?

---

### Post by markharding557 on 2007-11-16
> **kenwong said:**
> Hi, markharding557, I finally need to shut down my computer just a couple of hours of ago before you posted.

Before I shut it down, I went into System Monitor and did a few clicks then closed Firefox. I don't know which action(s) matter but anyway I was then able to unmount the drive. But still it was there and I tried to eject it in Terminal but failed.

I suppose I should also eject it although it has been unmounted.

Did I used the wrong command or what?

i think it's normal for the drive to show up after unmounting,the card reader on my printer always shows even though there is no media in it and it is not mounted.
you would have to disconnect the device to make it not show

---

### Post by kenwong on 2007-11-18
I am not sure whether this is normal with xubuntu as I have converted and used this OS for 2 weeks only.

But my iMac box behaves differently.  I eject the external hard drive (or ipod) and it then disappear from the desktop.  I am comfortable to unplug it.

---

### Post by davebgimp on 2007-11-24
I have the exact same errors with Xubuntu and any USB device. It automounts fine, but unmounting, through Thunar or using umount generates errors and that the device is busy. Now, when I say this, I mean there's no data still left to be written or anything like that.

---

