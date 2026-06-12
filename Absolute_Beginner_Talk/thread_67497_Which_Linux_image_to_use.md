---
title: "Which Linux image to use ??"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-09-20
I'm presently using linux-image-2.6.10-5-686.

I noticed, however, that there's a later version in synaptic. Namely, linux-image-2.6.11-1-686.

Which is best ? Should I be using this later kernel, or will it break things if I install it and remove the older image ?

regards,
grofaz

---

### Post by az on 2005-09-20
f you install the package, that kernel will be added to your menu when you boot.  The most recent kernel is the default.

Odd-numbered kernels are development kernels, which means they are not stable like even-numbered kernels.  The the odd-number kernel gets mature enough, it becomes even numbered.

So, 2.6.10 is more stable than 2.6.11.   2.6.11 is more recent than 2.6.10, but it will not be as stable as 2.6.12 will eventually be released as a stabel kernel. 


So, you probably do not want to install it.  If you do and you cannot boot it, or want to remove it, you can just do that.

---

### Post by bsussman on 2005-09-20
(edit)
Kernel upgrades are, by definition, potentially dangerous activities
(end edit)


grub can handle multiple images.  And the new one should not affect anything unless it is booted.

If you install the new one, do not remove the old one until at least 1 week after you think the new one is fine.  ;-)

I do not remove the old one(s) until the list in grub gets annoying.  I have plenty of disk space...

(edit)
This edit was done under 2.6.11 - it works for me but that doesn't mean you should be any less cautious!
(edit)

---

### Post by bsussman on 2005-09-20
[QUOTE=azz]
Odd-numbered kernels are development kernels, which means they are not stable like even-numbered kernels. The the odd-number kernel gets mature enough, it becomes even numbered.

[/QUOTE]
What is your source for this? Mine is [http://en.wikipedia.org/wiki/Linux_kernel#Version_Numbering]("http://en.wikipedia.org/wiki/Linux_kernel#Version_Numbering") , among others

For release number x.y.z  , this is true about y but NOT z, as far as my research shows.

---

