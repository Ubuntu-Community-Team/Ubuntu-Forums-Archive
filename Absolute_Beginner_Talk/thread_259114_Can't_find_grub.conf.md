---
title: "Can't find grub.conf"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by nanthony on 2006-09-16
Ok, I did something that was, all things considered, probably not the brightest thing ever.  I installed Ubuntu, then Windows XP (long, sad story why, don't ask).  Well, I know Ubuntu was working, and XP was working as well.  I finally got Grub re-installed, sort of.  At this point my laptop boots directly into Ubuntu, no stops at Grub to select one OS or the other.

Now, I assume that, for some reason, grub.conf is lacking the entry for Windows XP, but here's where things get fun.  I can't find grub.conf.  It wasn't in /boot/grub.  I tried to create grub.conf there, but to no availe, still booting straight into Ubuntu.

When I insatlled Grub so that it worked, I did it by booting the Ubuntu live CD and performing the following (I think this is right, at least):

>sudo grub
>root hd(0,0)
>setup (hd0)
>quit

I then restarted, and was in Ubuntu.  I think that the way my hard drive is  partitioned is so that the 1st is the Ubuntu install, 2nd is the Linux swap, 3rd is XP (NTFS).

Right now, I'm at a loss for what to try, any help would be greatly appreciated.  Thanks,
                                       NAH

---

### Post by xhaan on 2006-09-16
I think maybe you want to look for menu.lst instead of grub.conf
/boot/grub/menu.lst

:)

---

### Post by wieman01 on 2006-09-16
Ahem... You're looking for the wrong file:

**/boot/grub/menu.lst**

This is the one you need to edit.

---

### Post by nanthony on 2006-09-16
Well, that would make a difference now, wouldn't it.....I'll file that one under "Things that make me go 'D'oh!'"

---

