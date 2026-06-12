---
title: "[SOLVED] grub kernel options"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-01-27
Hello,

What does the 'ro' option in the grub menu.lst file mean?

```

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8029d128-8b3f-49d3-add8-0c5a323e8f02 ro quiet splash

```

I want to remove my boot splash screen so I can see the output at boot time.  Do I need to keep the 'ro' option after the UUID.

I was reading somewhere that boot loaders will boot a file system from the kernel image as read-only, to make sure nothing gets screwed up, but I couldn't find a resource that told me if 'ro' has anything to do with that (read only?).

I assume 'quiet' and 'splash' work together?  Can I remove 'splash' and keep 'quiet'?

I realize I could just modify it and test by rebooting, but I don't want to get stuck without an operating system!

Thanks!

---

### Post by wormser on 2008-01-27
This is the second thing I do on every Ubuntu install.  The ro is read only.  Just remove the quiet splash part.  You can remove quiet and leave the splash part.  For me it was too hard to read.  The splash is there but at the bottom you have a box with the boot up dialog.  You can also have the same effect by removing the quiet splash in the default options part of grub.  Just search menu.lst for it.

---

### Post by aBitLater on 2008-01-28
> **wormser said:**
> This is the second thing I do on every Ubuntu install.  The ro is read only.  Just remove the quiet splash part.  You can remove quiet and leave the splash part.  For me it was too hard to read.  The splash is there but at the bottom you have a box with the boot up dialog.  You can also have the same effect by removing the quiet splash in the default options part of grub.  Just search menu.lst for it.

Thanks wormser. Now I can see my startup output.

Also, do you know about _shutdown_ console output?  When I shutdown my opensuse machine, I get a lot of console output, but with ubuntu (after removing 'quiet splash' from kernel option), I only see a few lines of output, starting with 'Shutting down, please be patient', or something like that, then about 4 or 5 lines of info about the network manager.

Regarding the default options, I see this:
```
## DO NOT UNCOMMENT THEM, Just edit them to your needs
```

So the '#' symbols don't need to be removed?

---

