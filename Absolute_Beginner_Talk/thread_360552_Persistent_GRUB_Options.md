---
title: "Persistent GRUB Options?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-02-13
In my GRUB boot options, I have to add "ide=nodma" to the list of kernel boot options in order for it to recognize / mount my second hard drive.

However, anytime I upgrade my kernel and GRUB re-configures itself, it reverts all my OSes (both the new and older kernels) to the default values, which doesn't have the nodma option. Is there a way to keep this persistent across updates? I'd be nice if it added it to new kernels, too, but not a necessity.

I see "default kernel options" at the top of the menu.lst, but what does it mean "for automagic boot options"? I don't really want to start messing with stuff and breaking my GRUB.

---

### Post by confused57 on 2007-02-13
This may help you:
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)

---

