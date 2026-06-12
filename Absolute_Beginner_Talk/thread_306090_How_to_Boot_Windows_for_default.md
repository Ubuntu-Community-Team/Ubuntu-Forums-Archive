---
title: "How to Boot Windows for default"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by turker on 2006-11-24
Hi all,

I've been using Ubuntu for a long time yet due to some specific programs I use I want to boot from Windows first instead of Ubuntu.

I mean, the screen that asks which OS to boot and boots Ubuntu if we don't select none, should boot windows as its default OS.

Is it possible, how can we do that?

thanks...

---

### Post by davmac on 2006-11-26
If you open up a terminal window and type "sudo gedit /boot/grub/menu.lst"

Look for the "default 0" line and change this to the relevant number for where Windows appears on the list.

A couple of things to be aware of, the count starts at zero and you also have to count the "other operating systems" line too.

Hope this helps,

Dave Mac

---

