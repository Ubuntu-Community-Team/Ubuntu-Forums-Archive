---
title: "Double Entry on Dual Booting MBR"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Buckweet on 2007-06-29
I installed Ubuntu with the Live CD, then installed over that with the text-prompt install CD.
Ubuntu loads perfectly - I'm very happy with the experience so far. No complaints there.

I'm still dual-booting - I've got some drafting software that I haven't been able to find a replacement for yet, and unfinished projects.

My problem is, for some reason, the GRUB (?) boot screen shows two installs of Ubuntu.
I'd prefer if it didn't.

I know I goofed something up, but I'm too much of a newb to know what; and I've got just enough of a reputation as "competent with computers" to be bothered by it.

I don't mind if the solution is to reformat and reinstall Ubuntu - all I've done is updates, and try out a few peripherals.

How do I fix this?

---

### Post by overdrank on 2007-06-29
> **Buckweet said:**
> I installed Ubuntu with the Live CD, then installed over that with the text-prompt install CD.
Ubuntu loads perfectly - I'm very happy with the experience so far. No complaints there.

I'm still dual-booting - I've got some drafting software that I haven't been able to find a replacement for yet, and unfinished projects.

My problem is, for some reason, the GRUB (?) boot screen shows two installs of Ubuntu.
I'd prefer if it didn't.

I know I goofed something up, but I'm too much of a newb to know what; and I've got just enough of a reputation as "competent with computers" to be bothered by it.

I don't mind if the solution is to reformat and reinstall Ubuntu - all I've done is updates, and try out a few peripherals.

How do I fix this?
Hi I believe what you are seeing (since you update your system) is a kernel update and that is why you are seeing two options. I would leave it in place just because if you keep updating your current kernel and something happens you could be able to boot to the other one and save your data. ;)

---

### Post by hysteresis on 2007-06-29
One of your updates was probably a kernel update. you can edit /boot/grub/menu.lst and comment out or delete one of the kernel choices.
  1. <alt-F2>  gksudo nautilus
  2.  enter password
  3.  navigate to /boot/grub/menu.lst.  right click and open with text editor. edit the file.

---

### Post by Buckweet on 2007-06-29
Cool!

I figured it would be fairly simple to solve.

I'll try that out when I get home from work.

Thanks.

---

