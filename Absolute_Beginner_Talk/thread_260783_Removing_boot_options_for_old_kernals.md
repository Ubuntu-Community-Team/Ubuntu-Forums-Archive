---
title: "Removing boot options for old kernals?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by radicaldreamer on 2006-09-19
I have beenusing ubuntu for about a year now, and my boot menu has at least 8-10 kernals i can boot. I know there is a config file for the boot loader, but i need to know where.

---

### Post by whizbaby on 2006-09-19
/boot/grub/menu.lst

---

### Post by radicaldreamer on 2006-09-19
Got it, sudo vi on the file and edited to make me happy :)

Also, is there a performance difference between the 386 and 686 versions of the kernal? If so is it much?

---

### Post by bodhi.zazen on 2006-09-19
> **radicaldreamer said:**
> Got it, sudo vi on the file and edited to make me happy :)

Also, is there a performance difference between the 386 and 686 versions of the kernal? If so is it much?

Yes and define "much". the i686 kernel is easy to install and there is no downside, so I would just use it.

Do not let the French throw you. The menus are all English.

---

### Post by kiwi_bloke on 2006-09-19
When you delete entries from menu.lst you don't actually delete the actual kernel files. They still take up disk space. That's why I use the Synaptic Package Manager because it tidies everything up.
For example: to delete the last kernel I searched in Synaptic for 15-26-386" (the appropriate numbers at the end of the kernel name). You can then select the appropriate box to remove what you don't want. The file menu.lst will be automatically adjusted so no worries there.

---

### Post by radicaldreamer on 2006-09-19
> **bodhi.zazen said:**
> Yes and define "much". the i686 kernel is easy to install and there is no downside, so I would just use it.


I mean is it 1% or 10%, basically just wanting to know what kind of real world difference it makes, I am going to use it regardless because there has to be SOME benefit, but I am just curious

---

### Post by xyz on 2006-09-19
When I download/install one with "sudo aptitude", I remove it the same way (with remove) obviously.

---

### Post by bodhi.zazen on 2006-09-19
Look here: [http://ubuntuforums.org/archive/index.php/t-121248.html](http://ubuntuforums.org/archive/index.php/t-121248.html)

---

