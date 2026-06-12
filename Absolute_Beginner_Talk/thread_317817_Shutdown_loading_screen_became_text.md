---
title: "Shutdown loading screen became text"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by sylv3rblade on 2006-12-13
err.. I just succeeded in editing the grub menu to replace the old one with grub-gfx, after choosing restart on the menu, the old, shutdown splashscreen (the one with the progress bar and status of what's going on) was replaced by simple text... err.. did I do something wrong or is that a side effect of removing the original grub?

Using Dapper

---

### Post by mcduck on 2006-12-13
Do you still have 'splash' at the end of your kernel line?

could you post you /boot/grub/menu.lst here?

---

### Post by sylv3rblade on 2006-12-13
the only thing that changed is the gfxmenu line on line 1

---

### Post by mcduck on 2006-12-13
well, I have no idea. I don't see any reason why both wouldn't work together but as they clearly don't then it just might be that you can't have both at the same time..

---

