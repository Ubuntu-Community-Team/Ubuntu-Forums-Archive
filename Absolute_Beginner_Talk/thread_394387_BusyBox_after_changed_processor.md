---
title: "BusyBox after changed processor"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by jrmcc999 on 2007-03-26
I replaced my AMD Athlon CPU with a Sempron recently.  The motherboard supports it just fine.  After the upgrade, Ubuntu (Edgy) sometimes freezes for a long time after the progress bar has just started and eventually returns to a BusyBox prompt.  Hard drive activity stops with the progress bar.  Other times, it boots just like always and operates normally.  What is the keystroke sequence to bring up the text information sequence instead so that the progress bar is not shown?  I'd like to see where the boot is freezing.  Any other insight would be appreciated.  I thought I saw in one of the system information widgets once that Ubuntu still thinks the processor is an Athlon.  I can't remember which tool showed this.  Is there a way to re-run hardware detection, like you could with Anaconda and Redhat?  Thanks!
:guitar:

---

### Post by lamalex on 2007-03-26
sudo nano /boot/grub/menu.lst and remove the word quiet from your kernel.

---

