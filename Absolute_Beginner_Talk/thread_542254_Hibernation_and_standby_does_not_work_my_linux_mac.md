---
title: "Hibernation and standby does not work my linux machines"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Gruelius on 2007-09-03
Hey everyone,
Ive got two machines. The kubuntu one in my sig with a Nforce 2 and another simmilar pc which has a Nforce 3 150 board.

Ive been looking around and ive found a fixing thread for laptops but im not sure if this applies to PC's. Id like to get the suspend to ram feature working as my powerbill was massive last week!

Thanks
Julius

---

### Post by almacen on 2007-09-03
Maybe I am being a beginner, but when you say it is not working, do you mean it is not in the menues next to "Shut Down", etc or something else?
If it is not in the menues, then you might have to enable it as I had to do on my pc (to be honest, cant remember where, but easily find-able, as I did it! lol)
If it gives an error, I guess share with people, so they can help you out.

---

### Post by Gruelius on 2007-09-05
Its in the menu's. The problem is the pc doesnt wake up, just hangs. Ive looked around the log directory and havent found anything of significance.

---

### Post by jw5801 on 2007-09-05
Yeah manufacturers aren't the best when it comes to this sort of thing. The harware is supposed to conform to a standard, which is what the Linux HAL scripts are written for, but it often doesn't. It's always made so that it'll conform to Microsoft's requirement though, the power of a monopoly I guess!

Give [the laptop thread](http://ubuntuforums.org/showthread.php?t=471855) a shot and see what happens. It's worth a shot and it's not like it's hard to uninstall the packages again if it doesn't work! Laptops aren't completely separate entities to your desktop PC it's still all the same internals, so you've got about as much chance of getting a different script to work on you desktop as you do on a laptop.

---

