---
title: "extra option in boot menu"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by philmiller on 2007-02-10
I have a duel boot system; xp and edgy eft.

when i start the computer and the boot loader starts it shows;

ubuntu.kernel 2.6.17-11-generic
ubuntu.kernel 2.6.17-11-generic (recovery mode)
ubuntu.kernel 2.6.17-10-generic
ubuntu.kernel 2.6.17-10-generic (recovery mode)


They both work fine from what I can tell.  Which one should i be using?  Can i get rid of one and how would i do that?  If i can get rid of one which one can i get rid of?

Thanks again!!  You guys are the best!

Phil

---

### Post by taurus on 2007-02-10
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Put a # in front of the entries for the older kernel, ubuntu.kernel 2.6.17-10-generic & ubuntu.kernel 2.6.17-10-generic (recovery mode).

---

### Post by philmiller on 2007-02-10
That seemed to work.  It removed it as an option.  Now for a more difficult question.... why did that work?  Does the "#" make that line look like a comment or something?

Also why did this happen?  how can i prevent it from happening again?

---

### Post by taurus on 2007-02-10
The # means comment so you just comment out the generic kernel.  And how would you prevent it in the future?  Don't install the i386 kernel since the generic kernel is the default that comes with the CD.

---

### Post by mcduck on 2007-02-11
Actually that was the normal result of a kernel update, both new and old kernel will be in the menu, so if the new kernel for some reason doesn't work you can still use the old one.

After you have tested the new kernel and it works fine you can safely uninstall the old kernel packages with Synaptic. This will also remove the extra entries from Grub menu.

---

### Post by Tomosaur on 2007-02-11
The correct way is not to comment out the unwanted lines, but to tell grub to only show the latest kernel version. Commenting out the unwanted bits won't do any damage, but next time you get a new kernel update, you'll have the same problem. There's a line in the menu.lst file which says 'howmany=all'. Change it tp 'howmany=1'.

When you're done, run:
```

sudo update-grub

```

And your menu should be all sorted :)

Alternatively, check the link in my sig.

---

