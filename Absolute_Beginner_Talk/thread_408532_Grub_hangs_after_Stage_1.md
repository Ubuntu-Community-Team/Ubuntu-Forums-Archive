---
title: "Grub hangs after Stage 1"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2007-04-13
After installing 6.10 on my WD Passport USB drive, with grub set to install at /dev/sda, I reboot and find that Grub loads only Stage 1, then hangs up before running Stage 2. Super Grub doesn't
automatically find Grub on the system.

What's going on?

---

### Post by dstew on 2007-04-13
My son had a problem with a linux installation on a usb hard disk. It would only boot from a USB 2.0 plug, not the other USB plugs, which seemed to be slower, maybe were USB 1.0.

Do you get a grub error message?

---

### Post by BeardedOne on 2007-04-14
Thanks for your help.

No, I don't get an error message.  It shows only the line first Grub line, then stops. All my USB ports are USB 2.0.

---

### Post by dstew on 2007-04-15
Can you boot an Ubuntu live Cd on your system? If so, we can troubleshoot your installation from there.

If you can boot a live CD, open a terminal window (Applications --> Accessories --> Terminal) and enter the command **sudo fdisk -l**. Post the results to the forum.

---

### Post by BeardedOne on 2007-04-16
Thanks dstew,

It's weird. I re-installed about 5 times and blindly worked my way through SuperGrub, and managed to boot clean once. From there I was able to mount the drive, edit grub, and get a stable boot. So far so good. This is a lot of work, but I'm learning.

Now to see if I can get my wireless working.

---

