---
title: "installign kubuntu, what about grub?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-29
I have an asus s96j notebook with an hitachi 80 gb sata harddrive. 

I installed ubuntu and grub works but ubuntu freezes at mount root filesystem and I have not been able to figure out the problem. 

1) Will intalling kubuntu over ubuntu possibly fix the problem or will it be the same since i hear they are practically the same thing underneath, just a different desktop environment (kde instead of gnome). 

2) Do i just format and install kubuntu on the partition where ubuntu used to be and keep the same swap file?

3) Do i need to do anything to grub or will it automatically replace the ubuntu with kubuntu?

---

### Post by Jagot on 2006-07-29
1) To be hoenst I would think the same thing would happen, but you can always give it a go.  I have had this issue myself so I'm afraid I can't offer any advice as to what is causing it.

2) Yep.

3) No - you do not need to do anything - Kubuntu will take care of it.

---

### Post by mlind on 2006-07-29
1) possibly, if you do a fresh install, which overwrites the current grub, but there are easier ways for this

2) yes. but you will also lose your $HOME which stores all the user preferences. You should make a backup of $HOME and think about providing /home a separate partition.

3) if you do a fresh install then no actions are needed. If you install kubuntu using APT, then grub won't be touched

boot process freezes because root partition is not found. Have you tried troubleshooting grub settings if /boot/grub/menu.lst contains correct root partition for your kernel?

---

### Post by noodles12 on 2006-07-29
> **mlind said:**
> 1) possibly, if you do a fresh install, which overwrites the current grub, but there are easier ways for this

2) yes. but you will also lose your $HOME which stores all the user preferences. You should make a backup of $HOME and think about providing /home a separate partition.

3) if you do a fresh install then no actions are needed. If you install kubuntu using APT, then grub won't be touched

boot process freezes because root partition is not found. Have you tried troubleshooting grub settings if /boot/grub/menu.lst contains correct root partition for your kernel?

i looked in the /boot/grub/menu.lst using the live cd and it was blank >.< i don't think im looking in the right place.

---

