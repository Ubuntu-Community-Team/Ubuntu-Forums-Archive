---
title: "root file system"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by juantovarm on 2007-04-23
I moved to kubuntu 7.04 today, excellent piece of software, but i seem to have a problem. When booting it took ages for the bar at grub splash screen to start moving, so i went to /boot/grub/menu.lst and deleted the "quiet" so i could see what was going on. This came out:

waiting for root file system

It just sits there for about 2 minutes until it decides to move. I also installed "kde" from using Adept. Any clues?

---

### Post by Ecthelion on 2007-04-26
I had this problem when I started using edgy...

It went away after a kernel upgrade. 
The reason was that I had a new SATA 2 disk for which there were no good drivers (or that's my guess).
(it worked but I also had that 2 minute wait problem)

Do you have a new SATA2 disk or somthing?

---

### Post by juantovarm on 2007-04-26
I figured out the problem, it was my good old lite-on cd burning rom unit. Worked perfectly with all the other ubuntu releases but not with Feisty :confused:

---

