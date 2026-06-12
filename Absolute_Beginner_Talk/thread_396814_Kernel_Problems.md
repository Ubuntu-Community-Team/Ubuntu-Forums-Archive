---
title: "Kernel Problems"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-03-29
I recently did some upgrades, via the update, one of which I believe was stuff for NVIDIA cards.  I have done a reboot and now my X server does not work with kernel 2.6.17-11 generic.

At the same time I had been trying to work on getting Beryl to finally work.  I got through the first 2 steps on this HOW TO [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy) and then gave up because I didn't want to have to work through the text only terminals.

Now I am not sure if it was the updates through Ubuntu, or if it was me messing with the stuff for Beryl, but when I rebooted, X would not work.  I didn't make any new configurations to the X server itself, but I tried to restore from a backup and it still wouldn't work.  The error report gave the following information:

```

Error: API mismatch: The NVIDIA kernel module has the version 1.0-8776,
 but this X module has the version 1.0-9746.  Please make sure that the
 kernel module and all NVIDIA driver components have the same version

```

Now comes the fun and interesting part.  I have kernel 2.6.17-10 on my computer as well (and was thinking about removing it) so I tried to boot into that instead of 2.6.17-11.  When I did I was greeted with a different NVIDIA splash screen than I had seen before.  So then I tried to use Beryl, which worked for the first time ever.

Now as a joyous and fun occassion as this is for me, I was wondering should I even worry about this?  Should I just boot into 2.6.17-10 instead of 2.6.17-11, at which I would want to make it so I just boot into 2.6.17-10 automatically rather than .11.  Any advice would be greatly appreciated.

---

### Post by chalex on 2007-03-29
You can change the value of the "default" parameter in /boot/grub/menu.lst to change which kernel boots.  That what I did when it happened to me a few days ago, because I'm too lazy to look up the instructions on how to reinstall the right nvidia kernel module.

---

### Post by shaft350x on 2007-03-29
yeah so ok, I was playing around with Beryl, got it to crash.  Now I can't get Beryl to run anymore even with the 2.6.17-10 kernel, let alone that the 2.6.17-11 kernel still doesn't load.

---

### Post by shaft350x on 2007-03-30
Just an update.  I've gotten Beryl to work, at least now, by restarting Beryl after loading the manager.

---

