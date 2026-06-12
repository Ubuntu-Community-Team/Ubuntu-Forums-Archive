---
title: "Long delay when booting linux-only on core 2 duo macbook"
date: 2007-04-14
forum: Apple Intel Users
---

### Post by Rasputin_III on 2007-04-14
First off, I have not tried this with any of the development releases of Feisty--I am making an assumption that the experience will be similar to that of Edgy.

This laptop (a black core 2 duo macbook) will be running Feisty exclusively.  If the apple OS is installed anywhere, it will be on an external drive.

In following hints from multiple macbook howtos, I have tried a couple of variations of installation--specifically using the os x boot cd to handle initial partitioning vs. previously zeroing out the entire drive and following the "normal" (mbr) installation.

Both methods went smoothly, but there were two side effects: booting the system always resulted in a long delay (20 seconds or so) before the grub menu showed up; and if a bootable cd was in the drive, that was what was started (still after the 20 second delay).

This suggests that there is some kind of fallback BIOS emulation outside of boot camp--and that this will be a problem to anyone single booting ubuntu until there is some kind of native efi and gpt support included.

Thoughts?  Has anyone else ran into this?

Ras

---

### Post by Ganonzote on 2007-04-14
I have the same problem, i think this is caused because the macbook first try to boot using a GPT table, but it isn't, after about 30 seconds it boots from the mbr table, i think this delay will desapear if i could create a gpt table but I don't know how to do this.

You can know if you have a GPT table installing refit and runing  gptsync.

---

### Post by Rasputin_III on 2007-04-14
That's what I suspected--but I wonder if Feisty+1 (or beyond) will support native efi/gpt support such that it can create and deal with that kind of partitioning from the installer.

---

### Post by cyberdork33 on 2007-04-14
there is a gptsync package for ubuntu... You can sync the tables with it. IDK if it will speed the system boot up, but at least you could try it.

---

### Post by teymour on 2007-04-17
I have the same problem as you. I could not solve it but I found a solution to manually reduce the delay : 
press ALT key on boot and then select the hard drive icon

---

### Post by teymour on 2007-04-17
BTW, I removed EFI partition thinking it could help. Feisty works fine,  but delay stays.

---

### Post by ronocdh on 2007-04-17
I apologize if I'm philosophically out of line in suggesting this, but try installing OS X on a very minimal partition, and using rEFIt. This would solve the boot problem in that EFI would be being used and understood; I believe you can set up rEFIt to make Ubuntu the default OS, and on the GRUB screen you can remove delay.

More importantly, OS X will be necessary for firmware upgrades--for instance, to enable N capability in your wireless card, if I'm not mistaken. =/

---

### Post by Rasputin_III on 2007-04-18
Thanks for the suggestions and discussion...  As far as keeping os x, I may keep it on an external drive for updates and such--but I don't want it on the laptop at all (long story)...

The alt button thing may work as a stopgap, but I may try to see if partd (I assume is similar in functionality as gpartd--if not the back end) can create, and the system boot with a gpt label...
(I got the idea here: [http://www.coraid.com/support/linux/contrib/chernow/gpt.html](http://www.coraid.com/support/linux/contrib/chernow/gpt.html))
Although the situation is completely different.

If all else fails, I can keep hitting ALT or get a cup of coffee.  <grin>

Thanks,

Ras

---

