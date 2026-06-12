---
title: "[SOLVED] BusyBox? What the..."
date: 2007-10-29
forum: Apple PPC Users
---

### Post by docinsano on 2007-10-29
Here's the situation so far: I installed Gutsy on my iMac. 400 mHz and 512 ram worked fine with feisty, even though Nautilus didnt work.  Anyways, every time i boot the old mac up, the ubuntu loading screen just locks up.  After about five minutes, i get some kind of BusyBox thing.  Now, here come the questions:

1-What the heck is BusyBox,
2-How do i use it, and
3-How can i get Gutsy to run nicely on my iMac

Thanks in advance

---

### Post by 3rdalbum on 2007-10-30
Does it give an error just above the BusyBox thing? BusyBox is just a command-line shell for if things go pear-shaped.

---

### Post by kahrn on 2007-10-30
Busybox will likely come about if a piece of hardware cannot be initialized. I also got a busybox terminal due to [this bug]("https://bugs.launchpad.net/ubuntu/+bug/103148"), which is another thing it could be. 

Have you changed any hardware recently? The best thing to do right now is to edit the grub boot line and boot using verbose mode. To do this, when grub loads quickly modify the boot line, remove 'splash' and add 'verbose' and then boot using this line. Hopefully it should give you a little information on what is failing.

---

### Post by docinsano on 2007-11-02
Doesn't show any errors, I haven't changed any hardware, just a BusyBox prompt and thats it. Doesn't get any better than that.

---

### Post by BoneKracker on 2007-11-03
Try switching your vt.  There might be useful error dialog on tty1 and you might be looking at tty7 without realizing it.

alt+F1

---

### Post by stmiller on 2007-11-03
Look at this thread and see if this will help:

[http://ubuntuforums.org/showthread.php?t=581280](http://ubuntuforums.org/showthread.php?t=581280)

---

### Post by docinsano on 2007-11-29
> **BoneKracker said:**
> Try switching your vt.  There might be useful error dialog on tty1 and you might be looking at tty7 without realizing it.

alt+F1

I tried this and this came out of it:

```
Loading, please wait...
           Check root= bootarg cat /proc/cmdline 
            or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda3 does not exist. Dropping to a shell!
```

I understand that Gutsy has issues with recognizing some mac ide drives. Ive tried  modprobe ide_core a few times to no avail.  I'll keep trying though. In the meantime, any advice would be appreciated. thanks. 

The Dr.

---

### Post by docinsano on 2007-11-29
Success! It works now all but for a "volume control" error and an error starting the GNOME settings daemon. I guess its back to work now. 

Later.

The Doc

---

### Post by BoneKracker on 2007-11-29
Congratulations.

Add an entry here explaining what the problem and solution were for other people who experience the same problem and arrive here from a search.

On the sound thing, probably best to start a new thread (if you're not able to discover the answer by reading documentation and/or searching).

:)

---

### Post by yellowbeard on 2008-04-12
yes i have the same issue how did you solve it?

---

### Post by slacka-vt on 2008-04-12
Personally, I think there's a bug in the new powerpc kernel.
My ability to boot into my Mac OS X partition vanished literally over night.
I can still access my Macintosh HD but I can't boot the OS.

At the same time, my Hardy install, which has run flawless, booted into BusyBox.
This coincides with the linux update 2.6.24-16 yesterday.
After force restarting my system I was able to boot into Ubuntu but my yaboot.conf
was completely wiped out (like over-written almost ?)

very strange
~s

---

### Post by stream303 on 2008-04-12
I think for some, the transition from Beta to Beta-Feature-Freeze might be problematic.  There seemed to be so many changes and possible regressions.

I wonder if starting with a clean slate with the latest daily image might help...

---

### Post by slacka-vt on 2008-04-12
Funny thing is . .. 
My Ubuntu eventually booted up normal, and Mac OS X is dead.
I booted into my emergency partition, repaired permissions,
repaired the disk (there were some invalid header references ?!)
And Mac OS X is still dead, I get the apple logo swirl but it eventually just reboots.
Over and over again. 
At least my Ubuntu is safe and soundn:lolflag: 
it's all I ever use any how.

:guitar:

~s

---

