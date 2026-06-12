---
title: "Too many Feisty fawn Partitions"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-10
Upon booting up my computer it shows the boot menu of which partions I would like to boot ( XP or F.F.)  Well about 4 Feisty Fawns are showing ( prbly due to having problems with the installation having to start over during install process) so is there a way to delete these off the boot menu?

---

### Post by Vadi on 2007-09-10
You have four entries there, 2 for each kernel (you'll notice the numbers are a bit different). And for each entry, there's the normal boot, and a recover boot. So everything is fine, mine's the same.

That said, I think Tomosaraus... I probably got his name wrong, but he's on the forums here somewhere made an app called GrubED, that allows you to edit the grub entry with a gui. Look it up.

---

### Post by fiskking on 2007-09-10
Thanks Vadi for the help!

---

### Post by Vadi on 2007-09-10
Oh, here's the link: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104), and it's Tomosaur. Oops.

Oh, and those -aren't- different fiesty patritions. Just grub entries.

---

### Post by bwhitaker on 2007-09-10
> **Vadi said:**
> 
Oh, and those -aren't- different fiesty patritions. Just grub entries.
Right, Different Kernels usually, and as said previously rescue modes for each kernel,  It's a normal practice of installing new kernels in linux rather than replacing them to upgrade.  That way if somehting is wrong with the new kernel you have your old kernel to fall back on.

---

### Post by flatwombat on 2007-09-10
Of course, if you're happy with your kernel and want to clean up the menu a bit, simply put comments (#) in front of the kernels and lines that you don't want to display.  It won't remove the kernel, but it will remove the entry from the menu.  To be absolutely safe, print off the menu.lst before editing.

If you've printed it and ever have to access those extra kernels, stop the boot menu & use the 'e' for edit key and your printed list for a guide.

For instance, I am booting 8 distros, most with multiple kernels, so my normal 'default' boot would have been "26"!!!!  However, after printing, I kept one entry for each distro and now boot default "5".

---

### Post by fiskking on 2007-09-12
I have a question for the last post:

1.  How do you stop the boot menu (is it pressing ´e´ button) ?

2.  What command is it to print the menu.lst ( but first how to access this file within the           terminal)?

---

