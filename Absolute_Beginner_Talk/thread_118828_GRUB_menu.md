---
title: "GRUB menu"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by PuNGS on 2006-01-17
Well, when GRUB was booting, I pressed ESC to enter the menu, just for curiosity. But now, every time the system boots I have to choose the kernel that I want to boot... :( 

How can I make GRUB boot the default kernel again?

---

### Post by Iowan on 2006-01-17
Grub should boot the default kernel after a timeout.  You can verify the time setting with **more /boot/grub/menu.lst** from a terminal window.  Mine is set at 10 seconds.

---

### Post by PuNGS on 2006-01-17
I know that the kernel load up after a timeout, but it do not loads, it enters directly into the GRUB menu, where I choose the kernel to boot up.

---

### Post by adwait on 2006-01-17
GRUB? Default Kernel? You mean, now every time you boot....GRUB appears but waits for you to select a choice and doesn't automatically boot into Linux or Windows?? Open the GRUB config file with
```
sudo gedit /boot/grub/menu.lst
```

Now scroll down and find the serial number of the entry that you want selected automatically (start counting with 0). If you want to boot Ubuntu automatically, most probably it will be at no. 0. Now scroll up to find the line
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#

After that add
> default <serial number of entry

---

### Post by PuNGS on 2006-01-17
Hey, my 'timeout' property value is X_seconds. Could this be the problem?

---

### Post by Iowan on 2006-01-17
I wondered if it might have gotten changed, somehow (that's why I recommended checking it).

---

### Post by hen3rz on 2006-01-17
> Hey, my 'timeout' property value is X_seconds. Could this be the problem?
Mine is:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

so maybe?????

---

### Post by PuNGS on 2006-01-17
Yeah, that was it. Thank a lot for helping me, people. I assinged it to 1 and it worked nicely.

---

