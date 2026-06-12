---
title: "Gonna try ubuntu again..."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Anticitizen2 on 2007-07-28
I tried to install ubuntu 7.04 in a dual boot alongside my windows xp installation a few months ago.  the problem was, the GRUB didnt recognize my XP installation. In spite of the excellent advice i got from this forum, i couldnt fix the problem and had to reformat my computer.  Now, i want to try again.  I have the LiveCD version of the installer.  is there anything i can do too ensure beforehand that windows xp  will be recognized so i dont hae to go through another reformat?

---

### Post by Happy_Man on 2007-07-28
> **Anticitizen2 said:**
> I tried to install ubuntu 7.04 in a dual boot alongside my windows xp installation a few months ago.  the problem was, the GRUB didnt recognize my XP installation. In spite of the excellent advice i got from this forum, i couldnt fix the problem and had to reformat my computer.  Now, i want to try again.  I have the LiveCD version of the installer.  is there anything i can do too ensure beforehand that windows xp  will be recognized so i dont hae to go through another reformat?
Check at the final screen before you install, that XP is recognized. If you are using two hard drives, make djustments accordingly. So long as you doublecheck, you should be fine.

---

### Post by por100pre1 on 2007-07-28
Try this:

1. When installing use the "Guided -use the largest free space option"

2. At the 7th step (the last one) click the advanced button and select to install GRUB where Ubuntu is actually to be installed. If you are use only one HD it should be hd0,1 (that means first disk, second partition).

3. After finishing installing log into Windows (Ubuntu and GRUB will appear missing) and install EasyBCD to add Ubuntu to the Windows bootloader...

I did it this way and it worked fine to me. Hope this helps. :)

---

### Post by Anticitizen2 on 2007-07-28
thanks for the quick responses, im gonna give it a shot this evening i think.  hopefully i wont be back with problems...lol.

---

### Post by ugm6hr on 2007-07-28
> **por100pre1 said:**
> 3. After finishing installing log into Windows (Ubuntu and GRUB will appear missing) and install EasyBCD to add Ubuntu to the Windows bootloader...


I think EasyBCD requires Vista - has anyone got it to work with XP?

---

### Post by xc3RnbFO8P on 2007-07-28
I just want to add :** Dont forget to defrag!**

---

