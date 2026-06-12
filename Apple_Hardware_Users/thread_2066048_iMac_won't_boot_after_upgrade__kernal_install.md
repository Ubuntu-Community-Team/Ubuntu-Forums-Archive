---
title: "iMac won't boot after upgrade / kernal install"
date: 2012-10-03
forum: Apple Hardware Users
---

### Post by JustinAlf on 2012-10-03
Strange problem.  Ubuntu works fine on my iMac if I choose previous kernals and use kernal 2.6.....25.  (Don't know exact string).

The newest kernal that was installed after my upgrade was 2.6.....32.  I try booting into that kernal and it just goes to black screen after about 20 seconds.  About 50% of the time I get a boot loader, and then black.  Other times I get black instantly after grub.

Any thoughts?

I have a Intel Core i3 3.07 GHZ Imac 27 inch.  32 bit Ubuntu.

---

### Post by windscape on 2012-10-03
Hi,

Try editing the kernel command line for 2.6.32 in grub and add nomodeset

---

### Post by JustinAlf on 2012-10-04
> **windscape said:**
> Hi,

Try editing the kernel command line for 2.6.32 in grub and add nomodeset

Added.  I get to the bootscreen and it acts like it's loading and get all the way through and then freezes on a loading boot splash screen.

Still only can boot in kernel 2.6.25.

---

### Post by windscape on 2012-10-04
Hi,

Try removing quiet and splash from the kernel command line.

---

### Post by JustinAlf on 2012-10-04
> **windscape said:**
> Hi,

Try removing quiet and splash from the kernel command line.

Added.  It no longer has the splash screen but it still fails.  It goes through lines of code and then quits.

---

