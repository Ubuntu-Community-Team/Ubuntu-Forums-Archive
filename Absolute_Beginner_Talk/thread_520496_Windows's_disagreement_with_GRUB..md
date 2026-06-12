---
title: "Windows's disagreement with GRUB."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-08-08
Okay, heres what happens.

Ive got my GRUB setup just the way I like, everything works.

But once I boot up windows its byebye GRUB - I don't see it again next boot.

I keep having to boot the Ubuntu liveCD and change the boot flag back to the original partition.

Anyway to prevent windows doing that?

---

### Post by igknighted on 2007-08-08
> **Kitsun said:**
> Okay, heres what happens.

Ive got my GRUB setup just the way I like, everything works.

But once I boot up windows its byebye GRUB - I don't see it again next boot.

I keep having to boot the Ubuntu liveCD and change the boot flag back to the original partition.

Anyway to prevent windows doing that?

It sounds like you went with a rather atypical boot setup.  The boot flag shouldn't matter.  Where did you install grub to, the MBR - (hd0), or the partition Ubuntu is on - (hd0,#) (where # is the partition #)?  Grub should boot from the MBR ideally, and windows bootloader should be overwritten (should you decide to remove Ubuntu later you can restore the windows bootloader).  This ends up with the MBR having Ubuntus info, windows boot info is on its partition, and the position of the boot flag doesn't matter.

If you can describe how yours is laid out we could help you sort out what might be going wrong.

---

### Post by skymera on 2007-08-08
i had that problem.
but eve when grub stayed, it dissapeared next boot.

i added ubuntu to XP's boot menu.

but still it was annoying. hope something works.

---

### Post by cobrn1 on 2007-08-08
How have you been putting GRUB back onto the MBR, out of interest?

---

### Post by Kitsun on 2007-08-08
Ah, Ive got 3 partitions:

1, Ubuntu
2, WinXP
3, Swap for Ubuntu

Simply loading the liveCD and giving the Ubuntu partition the boot flag lets me get to GRUB, but when I start windows it changes.

Theres only one harddrive.

I did install windows second, so I must've did something incorrectly.

---

### Post by igknighted on 2007-08-08
> **Kitsun said:**
> Ah, Ive got 3 partitions:

1, Ubuntu
2, WinXP
3, Swap for Ubuntu

Simply loading the liveCD and giving the Ubuntu partition the boot flag lets me get to GRUB, but when I start windows it changes.

Theres only one harddrive.

I did install windows second, so I must've did something incorrectly.

Say no more, there's the issue right there.  Ubuntu's grub bootloader was overwritten by windows.  See this page for instruction on how to fix it: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub).  It's nothing you did incorrectly, its just that windows just kinda does what it wants and doesn't tell you what its doing.  It doesn't like to share ;).

---

