---
title: "Boot up problem"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by esl1885 on 2007-12-20
I just installed 7.10, but when it tries to boot, I jusy get a black screen and nothing happens. When I press alt/f1, it then boots OK. Can someone tell me how to fix this?
Thanks in advance for any help.

Sam

---

### Post by dstew on 2007-12-20
Which version of Ubuntu did you install? What are the specs of your machine (processor, clock speed, graphics card, memory, disks).

---

### Post by evil316 on 2007-12-20
Yes, if you press ALT F2 it will show the text on the screen during boot and I'm assuming you are saying when it does that it boots faster?  If that is the case then the problem is with the resolution of the spash screen.  Edit the file /boot/grub/menu.lst file and find a line that starts with kernel and ends with quiet splash, take out the quiet splash, save, reboot and you're good to go.

---

