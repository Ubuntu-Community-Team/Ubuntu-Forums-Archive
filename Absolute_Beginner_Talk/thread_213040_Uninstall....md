---
title: "Uninstall..."
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by CounterBlow on 2006-07-10
Well I've decided to uninstall my Dapper Drake, however I'm not exactly sure how...

I'm currently dual booting Windows XP, and Dapper Drake, so I have GRUB, which I would also like to uninstall.  Also, I was trying to install XGL, and when I go onto Ubuntu, it looks like it's loading, but does nothing.

So I basically would like to uninstall everything on my computer (With my dual boot) and then just start over fresh with just windows.  If someone could help, it would be greatly appreciated.

---

### Post by Kilz on 2006-07-10
> **CounterBlow said:**
> Well I've decided to uninstall my Dapper Drake, however I'm not exactly sure how...

I'm currently dual booting Windows XP, and Dapper Drake, so I have GRUB, which I would also like to uninstall.  Also, I was trying to install XGL, and when I go onto Ubuntu, it looks like it's loading, but does nothing.

So I basically would like to uninstall everything on my computer (With my dual boot) and then just start over fresh with just windows.  If someone could help, it would be greatly appreciated.
If you want to start over fresh, get out your restore cd disk that came with your computer, put it in the cd drive, and reboot.

---

### Post by elemental666 on 2006-07-10
If you're willing to reinstall windows, then just boot to the windows cd and let it destroy and repartition the hard dirve.

If you want to save your current windows installation then, boot into windows, goto control panel -> admin tools -> computer management -> disk management and destroy the linux partitions.

You can then boot to the windows cd and tell it to repair the windows installation and that should put the MS Bootloader back.

You don't "uninstall" operationg systems, you destroy the partitions they are installed on.

---

### Post by Drakkor on 2006-07-10
To make this: "You can then boot to the windows cd and tell it to repair the windows installation and that should put the MS Bootloader back" more clear
Boot from the windows cd select "R" for repair , at the prompt type fixmbr 
that will erase grub and let you boot straight into windows.

---

### Post by elemental666 on 2006-07-11
Thanks mate, its amazing how quickly you can forget the specifics...

---

