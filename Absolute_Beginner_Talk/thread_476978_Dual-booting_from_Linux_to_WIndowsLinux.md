---
title: "Dual-booting from Linux to WIndows/Linux"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Anonii on 2007-06-17
Hello there,

yesterday I decided to remove my Gentoo system and replace it with Gutsy. My PC used to hold, a Gentoo system, Windows and another shared partition for songs. Unfortunately, instead of deleting my Gentoo partition, I deleted my Windows one. That's not that big of a problem considering that I didn't have important stuff in my Windows partition, but I still have to remake it. The issue here is that, afaik, if I install Windows now in the place of my extra and unused Gentoo partition, Windows will also remove my MBR. How can I restore it after that? Anyone experienced with this kind of procedure that can help me? Thanks.

(I'm not gonna format my whole HD, since I lose my songs that way, and I also want to know how to fix this problem.)

---

### Post by alienexplorers on 2007-06-17
In Ubuntu it is easy to restore the MBR.  Not sure with Gentoo.  With Ubuntu you boot your install disk.  Enter Terminal and type sudo grub
Enter
> find /boot/grub/stage1
you will get an output like (hd#,#)
Enter
> root (hd#,#)
then Enter
> setup (hd#)
remember to leave off the partition number and use only the disk number.

---

