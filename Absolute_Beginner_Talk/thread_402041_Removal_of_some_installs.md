---
title: "Removal of some installs"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Damo1976 on 2007-04-05
Hi,

Thanks to the help of the people on this forum I have managed to install and migrate over to Linux entirely.
I haven't even bothered booting into Windows for ages.

However, I have a few questions.
When I boot up I now have about 6 different Ubuntu versions to choose from
i.e. 1.2.3.3   -  1.2.3.3 generic    1.2.4.4  - 386   1.2.4.4 - generic .  SMP versions too  etc
(not the actual kernal numbers obviously)

Here is another funny thing.  I have an ATI X1800 graphics card in my laptop which has casued many problems, and it only alows 3d acceleration in one of the versions (the 4 one from the top), which means I can't just tun it on and wander off whilst its booting, also its messy.  

How do I get rid of all the extra versions of the kernal?

Also, on another point, how stable is the beta version of feisty?  Should I wait until the proper release date?  It seems they have done a lot of development on the ATI card issue - which has been by far my biggest stumbling block.

Thanks
Damo 1976

---

### Post by eljalill on 2007-04-05
You can find the kernels as packages in sypatics, where you can also uninstall the ones you don't want.
But if for some reason, you want to keep them, you can also just disable them in your menu.lst in /boot/grub (commen them out with #), or, less risky still, you can set the default in the same file to the one you want to be booting. 

One of the first lines in that menu.lst is
default [number] . Set the number to the entry in the list, you want to have as default (like if you want the 4th entry set it to 4 I think) I am not sure, how it starts counting: with 1 or with 0, but that should be a small issue to find out.

Best of luck.

---

### Post by Gina on 2007-04-05
0 I believe.

---

### Post by brennydoogles on 2007-04-05
I recently decided to change my GRUB menu as well, and the thread I made should help if all you want to do is change what is VISIBLE (this won't remove anything in your setup, but in mine it involved removing entries for an older installation that I was no longer using) without causing problems later with Kernel updates. You can find this thread [here]("http://ubuntuforums.org/showthread.php?t=399993").

---

