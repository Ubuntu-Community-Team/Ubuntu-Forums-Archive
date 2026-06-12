---
title: "Messed up Grub"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by cremnob on 2005-12-27
Well I decided to delete an old distro and its swap area with partition magic. But now GRUB errors out because its looking for that old distro. How do I remove grub and boot into Windows? Can I use the ubuntu live cd and get rid of it that way?

---

### Post by sciurus on 2005-12-27
Do you know which partition Windows is on? I think you can do something like

grub> rootnoverify (hd0,0)
grub> chainloader +1
grub> makeactive
grub> boot

at the GRUB prompt to boot Windows. That assumes Windows is on the first partition of the first disk. If it was on the second partition, for example, the value would be (hd0,1)

Since what you say you want to do is completely remove GRUB, I would boot the Windows CD into the [Recovery Console]("http://support.microsoft.com/default.aspx?scid=kb;EN-US;314058") and use the fixmbr command.

---

