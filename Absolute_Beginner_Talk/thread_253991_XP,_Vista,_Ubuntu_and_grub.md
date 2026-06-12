---
title: "XP, Vista, Ubuntu and grub"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2006-09-09
Hi!

Another problem with booting.

I can boot to all 3 systems, however if I want to boot to XP, which I use most, I have to select: in grub "windows system", then in Vista boot manager "older windows system" and then in XP boot manager "windows xp" (the other choice is recovery console).

It's a bit too much for me :)

Is there a way to get rid of Vista boot manager completely and use only grub? So I could select XP, Vista and Ubuntu directly from grub?

---

### Post by moore.bryan on 2006-09-09
*you should be able to edit /boot/grub/menu.lst for that.  do you know which partitions contain which os's?*

---

### Post by g0nzo on 2006-09-09
Yeah, I know.
sda1 - XP
sda6 - Vista
sda8 - Kubuntu.

In menu.lst I've got for Windows:
title		Microsoft Windows Systems
root		(hd0,0)
savedefault
makeactive
chainloader	+1

However it starts Vista boot manager...

---

### Post by bodhi.zazen on 2006-09-09
Try this:
> 
[quote]title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

title Vista
root (hd0,5)
savedefault
makeactive
chainloader +1

The only other potential problem I see is Vista is on sda6. This is a logical partition and windows likes to be on a primary partition. Try vista on sda1, sda2, or sda3 with Ubuntu (all ubunt partitions ie root, /home if you use one, swap, etc) in your logical partion

---

### Post by g0nzo on 2006-09-09
> Try this: ...

But isn't this XP config exactly the same as I have it now? root (hd0,0) will (very likely) start Vista boot manager, not XP directly.

---

### Post by bodhi.zazen on 2006-09-09
If it is I apologize, I thought you were having problems with vista, which I changed.

If it is not working, ?post on microsoft forums to see if they will help you boot. I would think not, but perhaps.

---

### Post by g0nzo on 2006-09-09
Thanks anyway. I know that it's not problem with Ubuntu or grub, rather with Vista boot manager, but maybe someone knows how to solve this. Probably many people are in similar situation.

Maybe it's possible to boot XP directly from grub (without going into Vista boot manager) or maybe it's possible to remove Vista boot manager and select Vista from XP boot menu?

Anyway, any suggestion are welcome :)

---

### Post by Tomosaur on 2006-09-09
I don't think you guys understand the problem - he wants to disable the Windows boot managers. I think you can do this from within windows.
Control Panel > System > Error Reporting (I think)  for WinXP, but I've never used Vista.

---

### Post by bodhi.zazen on 2006-09-09
> **Tomosaur said:**
> I don't think you guys understand the problem - he wants to disable the Windows boot managers. I think you can do this from within windows.
Control Panel > System > Error Reporting (I think)  for WinXP, but I've never used Vista.

No, I understand the problem. That is why I directed him to the Microsoft forums.

---

