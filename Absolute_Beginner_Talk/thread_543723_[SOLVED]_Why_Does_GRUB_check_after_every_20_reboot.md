---
title: "[SOLVED] Why Does GRUB check after every 20 reboots ??"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-05
After I restart my PC after every 20 reboots it goes through a checking process of the kernel etc.

Is this necessary after such short periods ............ if not, can I extend the frequency to a higher number as I turn the PC off approximately  3/4 times per day.

---

### Post by notwen on 2007-09-05
Fsck(file system check) runs every 30ish reboots, which isn't too often on a  Linux Desktop, but can be very bothersome on a Linux laptop, especially it has a large HDD.  This [thread]("http://ubuntuforums.org/showthread.php?t=295262") will give you a tool to post-pone these checks.  Hope this helps you out. =]

---

### Post by oilchangeguy on 2007-09-05
> **chrome307 said:**
> After I restart my PC after every 20 reboots it goes through a checking process of the kernel etc.

Is this necessary after such short periods ............ if not, can I extend the frequency to a higher number as I turn the PC off approximately  3/4 times per day.

i'm not sure if the 20 reboots can be changed. but why not leave the computer on? at the rate you're going, the computer will at some point fall victim to thermal cycling. (small stress cracks can form on the solder that anchors components to the motherboard)

---

### Post by EndPerform on 2007-09-05
Try this: [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by rsambuca on 2007-09-05
You can change the number of boots between disk checks by using the tune2fs command.  In a terminal:```
sudo tune2fs -c **[COLOR="Red"]#[/COLOR]** /dev/hda1
```for the #, set it at 30, 40, etc, whatever you feel comfortable with.  You will also have to set the /dev/hda1 to your specific drive(s).

If you have multiple partitions, it can be benificial to set the fsck intervals just a little bit differently to 31, 32, 33, etc., so that they don't all check at once.

---

### Post by Amazona aestiva on 2007-09-05
It doesn't hurt.

---

### Post by chrome307 on 2007-09-06
Thank you for the explanation and tips on how to change this :)

---

