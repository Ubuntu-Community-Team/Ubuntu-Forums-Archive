---
title: "Problems Booting"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by alex1001 on 2008-01-27
Hi, I just installed Ubuntu 7.10 yesterday, and I was curious about the boot time. Whenever I start up the computer, it sits for a few minutes with a black screen waiting for Ubuntu to boot, is this common? Is there any way that I could cut this down?

I'm a newbie when it comes to using Linux, so I suppose I have a basic understanding of how to get around, but not much more than that.

Thank you, I really appreciate all your help!

---

### Post by taurus on 2008-01-27
Maybe you have the timeout for too long in /boot/grub/menu.lst.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
cat /boot/grub/menu.lst
```

---

### Post by exneo002 on 2008-01-27
depends on the powr of you box I have an hp pavilion a819n with 512mb and it sits for a few seconds maybe your box is over worked well if its an old box try xubuntu or dsl or dsl-n well good like ask this on xchat if you want immediate results

---

### Post by philinux on 2008-01-27
Click the link for known bugs. Long boot times is one of them for some.

---

