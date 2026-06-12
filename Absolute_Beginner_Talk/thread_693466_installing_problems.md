---
title: "installing problems"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by sfarber on 2008-02-11
Hello.
I have 2 HD. First is 80GB SATA and has a WinXP on it,
The second is AT100 20GB IDE.

I tried to load ubuntu 7.10, but I keep getting the emask errors on initramfs (the regular error with buffer I/O).
I tried to add to the boot line the "all_generic_ide noapic", but it still showing the errors.
in version 7.04, adding that to the boot line solved the error.

The problem is when I install the ubuntu everything looks OK, but when I restart the computer it stuck on "GRUB loading, please wait...".

I have tried to install grub on the other HD (The 20GB IDE) but it loads very slowly, and stuck on the same line.

my questions are :
1. Why can't I load Ubuntu 7.10?
2. Why can't I install ubuntu on secondary HD?
3. Why GRUB doesn't work?

Any help will be great, I am fighting this over a week.

Shay.

---

### Post by hyper_ch on 2008-02-11
Hmmm, how about you unplug the windows harddisk so that you only have one harddisk in there.

Can you then install Ubuntu fine?

If so, can you set in the bios that it shall boot from the ubuntu harddisk as primary device?

---

### Post by sfarber on 2008-02-11
Wll I'll give it a try.
This is very strange problem.... I had before ubuntu 7.04 64Bit on the Main HD (SATA 80GB), and there were no problem.

Is it posibble that my secondary HD is damaged?

---

### Post by hyper_ch on 2008-02-11
might be that it's damaged...

---

