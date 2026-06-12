---
title: "Can I undo an install?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-04
I have a thinkpad.
I'm going to install ubuntu on it. It will probably install grub too.
Can I undo everything just the way it was (except with now a left over partition probably) including removing grub..

All in one shot?

thanks

---

### Post by K.Mandla on 2007-09-04
Not ... really. You could try the live CD, which lets you try out the Ubuntu environment before you install it. Is that an option for you?

Usually when you install you're overwriting anything that was on the hard drive. You can, if you want, delete the partition and effectively remove everything you installed in one fell swoop, but I'm not sure if that's what you're after.

Is there a Windows partition on there? Can you tell us why you might need to revert to something else?

---

### Post by systemintheglitch on 2007-09-05
Suppose I install a dual boot.
I want to get rid of the ubuntu partition (wipe it clean) and also get rid of grub boot loader.

Can I do this?

---

### Post by [Alsharifi] on 2007-09-05
u can format/delete the ubuntu partion,resize ur windows partion and ubuntu will be gone.

on the other hand,i dont think u can completely get rid of GRUB.....u can prob. Hide it and have your system boot up sr8t to windoze ?

---

### Post by santiagoward2000 on 2007-09-05
I couldn't get rid of GRUB on my laptop. I'd erased all Linux partitions, resized my NTFS partition and yet it tried to run GRUB, but couldn't find it.
Honestly, now I don't worry about it. I've reconsidered, and left Ubuntu installed. It even became my primary OS! :lolflag:

---

### Post by systemintheglitch on 2007-09-05
Wait,

In the worst case, if it cant find grub what will happen?

---

### Post by K.Mandla on 2007-09-05
Nothing. The machine won't boot, but it's a simple matter to use the Windows installation disc to reinstall the master boot record. 

Generally if you install Windows, then Ubuntu, Grub overwrites the Windows bootloader. That's okay. But if you delete the Ubuntu partition afterward, then Grub can't find the information it needs to boot. So you get funny "Grub error 22" messages ... or something like that (I forget the actual number).

At that point, if you pop the Windows installation disc back in, boot from it, then reinstall the master boot record with fixmbr, your Windows machine is back to normal. Is that what you're asking?

---

