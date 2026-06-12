---
title: "Dualboot, without grub?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by chris.snafu on 2006-06-07
i installed ubutnu, and loved it, i had it on a second hard drive, cause when i tired to repartition a diff drive, it deleted my windows, Ubuntu worked this time, and i wanted to play a game with my friends.. so i restarted, and choose windows Xp Home in the grub boot manager... and it went to the loading screen, for a second, then a large amount of text in comand prompt format, then my computer started, and restarted the circle. so i reinstalled winxp, and reformated the ubuntu drive...

(sorry about my backround story)

My question is, can i install Ubuntu to that same drive... but no grub... so i can just boot that drive from my boot menu bios whatever, without the grub, cause i dont feel like reinstalling windows again...

thanks for the help up front though...

---

### Post by confused57 on 2006-06-07
This thread may offer you another option:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

or

[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

You would need the alternate install cd for link#2.

---

### Post by chris.snafu on 2006-06-07
ok, im kind of confused by those, because they are all slightly different then my problem, and i want to make sure...

so i have an idea..

1. disconnect master drive
2. load live cd and install ubuntu onto slave drive
3. turn off computer, reconnect master drive, start up computer


if i dont do anything when its loading, will it boot to XP? (or if i make the Ubuntu drive the master, and XP slave: will it boot to Ubuntu?)

then if i open the boot menu for my bios stuff, then choose the other drive... will it boot to Ubuntu? (or XP?)

without grub? or does grub boot ubuntu, even if its the only OS?

With this set up, im thinking, will it make the master boot, regaurdless, unless told otherwise? or will i have to change something?

please tell me if this will work, or what i will have to do to make it work

EDIT: ok, read the second one over again... and that looks like a good idea... 
so when i have the floppy in, it will let me boot to ubuntu, and if its out, then it will boot straight to windows?

---

### Post by confused57 on 2006-06-07
The first link I gave was for installing Ubuntu and Windows on separate drives, Ubuntu would be the master drive and Windows the slave drive...if that's what you want, I can help walk you through it.  This method does not affect your Windows drive in any way, you just need to make an entry in the grub/menu.lst on the Ubuntu drive to boot Windows at startup.

Sounds like you'd rather install Ubuntu to dualboot on the same drive as Windows, in that case, the second link should allow you to do this using the alternate install CD, you can't select where you want grub installed with the LiveCD installation.

---

