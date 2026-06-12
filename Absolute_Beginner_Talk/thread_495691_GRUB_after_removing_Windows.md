---
title: "GRUB after removing Windows"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-07-08
I've got a question to plan my future steps in Ubuntu. Now, I have a dual-boot system, but I'm planning to remove Windows. Is it necessary to reconfigure/reinstall GRUB apart from obviously removing Windows' entry in menu.lst?

Thanks in advance!

---

### Post by Vajra Vrtti on 2007-07-08
Just delete the Windows entry in the grub's *menu.lst *and use it's partition for something more useful.

---

### Post by cobrn1 on 2007-07-08
yep, it's just as simple as removing the widows entry (or comment it by putting # infront of all it's lines if you might keep it). If you're sure you're removing windows, ie, reformatting it's partition then just delete the windows stanza (paragraph/entry) in grub.

Deleting is nice and easy, it's just adding new stuff that's (more) difficult.

---

### Post by nvteighen on 2007-07-09
It seems very simple, then. I was fearing that editing menu.lst wouldn't be enough...

(If you're curious: I'll transform the nasty NTFS partition into a pretty /home partition)

Thank you all!

---

