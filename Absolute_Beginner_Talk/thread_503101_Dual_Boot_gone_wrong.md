---
title: "Dual Boot gone wrong"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-17
I have been unable to boot into xp for some time now but this has not been a problem as I have used Ubuntu only. I now need to print out photos on my canon Mp170 and having tried everything including turboprint I cannot get a satisfactory photo print.

I am considering getting a Hp C4180 as a replacement but as a final effort before spending on a new printer, I am going to try to revive my missing xp on boot up. the system is visible on my hard drive.

This is the only serious problem on my pc, a Compaq Presario, I have searched the various threads regarding this and they have either failed or been inappropriate for the task OR I, as a relative newbie, have been unable to follow the instructions.

Is there any straightforward way of overcoming this situation or is a HP C4180 the answer.

---

### Post by wolfen69 on 2007-07-17
is reinstalling xp out of the question?

---

### Post by Benbow on 2007-07-17
No, I could reinstall xp but would prefer not to have to reinstall Ubuntu, and there are some files on xp which I would wish to keep.

---

### Post by oilchangeguy on 2007-07-17
> **wolfen69 said:**
> is reinstalling xp out of the question?

if the user did, they would/should reinstall ubuntu. windows first, then ubuntu. otherwise it can be a problem to get grub back, as the windows reinstall will overwrite grub.

---

### Post by Error1312 on 2007-07-17
This topic helped me out when my bootloader was messed up: [http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by davidjmayo on 2007-07-17
Sorry to state the obvious but would you by any chance have decided before, you didn't need XP anymore, and maybe removed or commented it out from the grub menu

---

### Post by ugm6hr on 2007-07-17
A bit more info would be useful:
Does an entry for XP appear in GRUB?
Does the XP partition appear on GParted, and what partition is it on?
Maybe post your /boot/grub/menu.lst

---

