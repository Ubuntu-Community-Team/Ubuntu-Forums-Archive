---
title: "booting from external usb HD question"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by PhiAlpha314 on 2008-04-03
Okay I just installed ubuntu 7.10 on my 250gb LaCief (spelling?) usb external HD and have windows xp still on my laptop.  Everything works great on both windows and ubuntu except that I can not start my laptop now without my external HD connected and turned on before I turn on my laptop.  It isn't *that* big of a deal because I don't take my laptop off my desk much but still when I do I don't want to have to take my external HD with me.  Can anyone help me out?

---

### Post by Diabolis on 2008-04-03
That is because the booloader is installed in your external hdd.

In order to bootup correctly the pc loads this:
bios / bootloader / operating system

So you probably want to install the bootloader on the other drive. Ubuntu uses grub, windows uses somehting called ntldr I think.
[this might work]("http://www.neowin.net/forum/index.php?showtopic=292614")

---

### Post by rolnics on 2008-04-03
> **Diabolis said:**
> 
[this might work]("http://www.neowin.net/forum/index.php?showtopic=292614")

That will get windows back, but what about Ubuntu? Maybe using the live cd to install grub again would give the option?

---

### Post by Diabolis on 2008-04-03
mmm I guess it will be easier if you just use grub as your bootloader. Grub can boot anything, it doesn't matter if its window or linux.

So, pluggin your external hdd and turn on your pc. While at the grub menu type **c** in order to enter a command line and issue this commands:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
```

So the **output** of find is the **input** of root.

You can do it within an already booted system by typing at a terminal
```
sudo grub
```

And you can also do it from a live-cd.

[similar scenario]("http://ubuntuforums.org/showthread.php?t=725689&page=4")

---

### Post by PhiAlpha314 on 2008-04-03
hey thanks a bunch for the quick responses. Just making 100% sure tho, Installing the new grub isn't going to wipe my hdd, right?

---

### Post by Diabolis on 2008-04-03
no, the worst thing that can happen if you do it wrong is that you'll wreck grub, in that case you can fix it by using the same commands posted above.

---

### Post by rolnics on 2008-04-03
Everything else should be ok, it will be grub that's messed up, not being able to point in the right direction to load either windows or linux or both! Like Diabolis said use the commands posted to fix the problem.

---

