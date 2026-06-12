---
title: "[SOLVED] boot loader after vista/xp installation?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2008-02-28
i have currently on my computer Vista and ubuntu(gutsy gibbon) . i will format vista and i want to install XP also . 

i understand that for some people this sounds stupid but i am not asking for judgement but for help. i was wondering if my grub loader would still appear and if not what should i do to be able to still access my ubuntu installation . 

thanks

---

### Post by S15_88 on 2008-02-28
when you install XP on a seperate partition next time you boot all three OS's will show up on the GRUB menu.

Thanks, ALain

---

### Post by neoragexxx on 2008-02-28
that's great to hear! what about vista ? 

btw i already read the thread about using the live cd afterwards to rewrite/reinstall grub but i'd prefer an alternative solution/avoid that because i don't remember where i have my cd stored !

---

### Post by S15_88 on 2008-02-28
i'm not 100% sure whether you'll have to reinstall grub, i've always installed XP/Vista first then ubuntu and used the partitioner on the live cd install.  

i'm going to take a guess and say that you won't lose grub but google around!

one thing that might happen is that when you install XP u will have to chage the hardrive location ex.  (hd0,0) to (hd0,1) or something like that.

EDIT: did it for you haha there ya go ->
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")
[http://linuxexpert.wordpress.com/2007/11/29/dual-boot-xp-after-ubuntu/]("http://linuxexpert.wordpress.com/2007/11/29/dual-boot-xp-after-ubuntu/")
[http://ubuntuforums.org/archive/index.php/t-389251.html]("http://ubuntuforums.org/archive/index.php/t-389251.html")

Hope That Helps,
Thanks, ALain

---

### Post by neoragexxx on 2008-02-28
thanks for the spoonfeeding :) i'll try it and let you know

---

### Post by sillyxone on 2008-02-28
As I understand, Windows XP installer never care about other OS, so every time you install Windows XP, it will always write to Master Boot Record (the same effect as running fixmbr)

Thus, usually install XP first, then Ubuntu since Ubuntu can install the Grub menu for other OSes. If you install XP using the installer CD (not restoring from image), I'm pretty sure it will wipe out Grub.

---

### Post by neoragexxx on 2008-02-28
i understand this but uninstalling ubuntu  right now or the near future is not an option !!

---

### Post by logos34 on 2008-02-28
installing windows will overwrite grub on the mbr--no way around it.

If you don't have the live cd you could use [Super Grub disk]("http://supergrub.forjamari.linex.org/") to boot back into ubuntu after installing xp, then restore grub.  Or make a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy") beforehand.

---

### Post by neoragexxx on 2008-02-28
ok thanks for the reply man . i have acronis os selector.. which might find ubuntu also afterwards. if that fails i'll find/borrow the live-cd from someone

---

