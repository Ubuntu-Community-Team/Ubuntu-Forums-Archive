---
title: "System won't start after adding KDE"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by fairfield on 2007-06-16
I have been running Ubuntu 7.04 on a Fujitsu Lifebook laptop. It worked flawlessly. I then added KDE by means of apt-get install kubuntu-desktop. That also worked great. I could log on and off in GNOME or KDE. However, I got a big shock when I turned the computer off and then on. What I got was

[  35.066479] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[  35.066554]

What causes this and is there a way to fix this problem? The Ubuntu partition is 10 GB and 50% used. I also have two other Linux distros and Windows XP. The two Linuxdistros can read/write all other partitions.

Can anybody help? Thanks.

---

### Post by floke on 2007-06-16
Mu guess? You pulled in something else, such as a kernel update, that had borked your grub.

Check the output of 'sudo fdisk -l' with your /boot/grub/menu.lst entry to make sure that grub is pointing to the right place.

---

### Post by floke on 2007-06-16
Ok first post - probably bit too technical.
Can you go to a terminal and (post the outputs of() type, first

sudo fdisk -l

and then

cat /boot/grub/menu.lst

---

### Post by fairfield on 2007-06-16
In understand what you are saying, but I cannot get to the terminal as Ubuntu does not start after this kernel panic message. I can only look at folders or files on my Ubuntu partition using one of my other distros, but I do not know here to look.

---

### Post by fairfield on 2007-06-16
I should perhaps add that I start my four OS by lilo of one of my other Linux distros.

---

### Post by floke on 2007-06-17
My guess would be then that lilo is pointing to the wrong place - does the boot sequence actually start or does it blow up from the outset?

---

