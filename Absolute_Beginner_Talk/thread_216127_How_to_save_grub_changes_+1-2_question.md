---
title: "How to save grub changes? +1-2 question"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-15
How do I save grub changes?

I can get both win xp and Linux working, but the problem is... After I edit it with *e*, and hit ESC, it does not save them (from the grub boot menu)... I can only get it to work if I edit them (using E) then boot (using B) each and every time...

Question 2: I can get Windows XP to work if I have root (hd2,0) then a couple maps, but if I do that, windows xp has two options (like a other boot menu with tw win xps)... What is that?  <- This was one of the default Windows XP boot option grub added. Maybe the two boot options are linking it to (hd0,0)?

Then if I edit the boot menu to (hd0,0) it will not work unless I delete both the *map* commands first...

---

### Post by [S|G] on 2006-07-15
1: To make permanent changes in the grub menu, edit your /boot/grub/menu.lst. Set whatever options you need there.

2: You get another option, but AFTER you leave the grub boot menu? If that is so, then it's Windows boot manager. You can find it by right-clicking "my computer", properties and it's somewhere on the advanced tab if I'm not sure (it's been some time since I last used win). You can edit windows boot menu list and remove duplicate entries there.

---

### Post by IDontKnow9998 on 2006-07-15
Ah tnx... Grub is working perfectly now...  Downloading updates right now....

---

