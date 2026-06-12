---
title: "h feisty/xp"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by lsalminen on 2007-06-23
Hi-

I just installed windows xp on a second partiton, following this guide: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

When I choose Windows Xp from the grub menu, it reloads grub stage 2, and just automatically boots to ubuntu.

Does anyone know what to do?

Thanks, Lee

---

### Post by BobCFC on 2007-06-23
Looking through the comments of that guide ppl seem to have trouble with joining two lines that should be seperate


The example shows

```
title Windows XP

root (hd0,1)

**makeactivechainloader +1 **
```

But the picture underneath shows that makeactive and chainloader +1 should be two lines

[IMG]http://apcmag.com/system/files/images/grub08.article-width.jpg[/IMG]


My other thought is maybe you copied the (hd0,1) from the example but your windows partition is somewhere else... you will need to investigate.

---

