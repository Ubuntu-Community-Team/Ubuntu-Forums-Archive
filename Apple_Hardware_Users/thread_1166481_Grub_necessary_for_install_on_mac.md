---
title: "Grub necessary for install on mac?"
date: 2009-05-21
forum: Apple Hardware Users
---

### Post by Greevous on 2009-05-21
I just installed Ubuntu on my Mac, but I forgot to install the grub via the "Advanced" button when I was finished setting it up. Is it necessary if I already installed rEFIt? And if so, is there a way to install it now after Ubuntu is already written to the hard drive? Thanks.

---

### Post by Sef on 2009-05-21
Moved to Apple Users forum.

---

### Post by pxwpxw on 2009-05-22
> **Greevous said:**
> I just installed Ubuntu on my Mac, but I forgot to install the grub via the "Advanced" button when I was finished setting it up. Is it necessary if I already installed rEFIt? And if so, is there a way to install it now after Ubuntu is already written to the hard drive? Thanks.
Yes you do need grub (assuming you have an Intel Mac).
If you did nothing it could have installed to the MBR by default, unless you were asked where to install and then failed to enter anything.
What ubuntu version was installed, and what is your Mac model?
What happens when you try to restart?

---

### Post by skullmunky on 2009-05-27
You do need Grub.  It probably installed it to the MBR instead of to the Linux partition when you went through the installer, and now when you boot you just get the penguin logo and nothing else.

You can install grub to the correct partition by booting into the live CD and using grub from the terminal, but it's easier to just re-install and make sure to click the Advanced button at the right point.

This happens to me pretty much without fail every single time I install Ubuntu on a Mac.  I always forget and have to do it again.

I wish the instructions had that part in huge red blinking text.

---

