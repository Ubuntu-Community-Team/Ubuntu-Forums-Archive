---
title: "adding system to grub"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-03-16
Well I have two 160g HD's and hda0 has XP and Ubuntu on it. My hda1 has some backup storage on it, but I am planning on addin Vista on it. Once I install it how would I add it to Grub?

I know that it might just boot to Vista once it installs and I might have to add Grub back on. But i just want to know how. Just in case...

---

### Post by Zelut on 2006-03-16
The grub bootup list is found in /boot/grub/menu.lst.  When you install any Microsoft product it will wipe everything else from the MBR so you will have to restore grub in order to use Ubuntu (or anything else) again.

Take a look thru the menu.lst file to see how/where to edit.  It has a lot of information in there that should give you what you need.

If you do need to restore grub there are plenty of tips on that already existing.

---

### Post by CookieOrc on 2006-03-16
[QUOTE=kuyaedz]When you install any Microsoft product it will wipe everything else from the MBR so you will have to restore grub in order to use Ubuntu (or anything else) again.
QUOTE]
 
Yea, I found that one out the hard way. I know how to restore grub, I just was wondering if anyone had any tips. Just because I do not feel like screwin up my system yet another time.

And when I have to restore it again do you think it will pick up both systems?

---

### Post by Zelut on 2006-03-16
Well since Linux plays well with others it will detect any other system available.  Whether it be other partitions of Linux, Windows, etc.  Grub should detect and list all of them (in my experience) when you restore grub to the MBR.

---

### Post by CookieOrc on 2006-03-16
Well I just got My vista Cd so I guess I will just report back once I have broken my computer again... Thank you for your help.

---

