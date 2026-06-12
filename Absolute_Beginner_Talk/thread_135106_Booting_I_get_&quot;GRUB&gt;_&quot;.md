---
title: "Booting I get &quot;GRUB&gt;_&quot;"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-02-23
Hello everybody.

What do I type in here?

Don Cole

---

### Post by mr_mop on 2006-02-23
What did you do before you got to that?

---

### Post by Iowan on 2006-02-23
Doesn't seem like a good thing.  You *should* breeze (pardon the pun) right through grub on your way to a startup.

---

### Post by don cole on 2006-02-23
Before I got that it was booting ok.

Oh, I was changing some enviromental variables in my w2k partion.

Don Cole

---

### Post by cotcot on 2006-02-23
The grub bootloader does not find stage 1.5. Stage 1.5 is located in /boot/grub. You can try to manually boot or a grub-install (see "grub manual" for that). If it does not work there is another reason why grub does not find stage 1.5..

---

