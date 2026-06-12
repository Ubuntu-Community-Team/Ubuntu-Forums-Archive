---
title: "Removing Splash Screen From The Grub"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by b_chris on 2007-05-23
Hello, whenever I remove Quiet and Splash from the menu file and rebuild it, they magically appear back in the menu file.

Is there anyway I can stop this from happening??

---

### Post by chili555 on 2007-05-23
May I assume you are removing these lines as you interrupt the boot process and edit the lines? To make the changes permanent, *sudo gedit /boot/grub/menu.lst* and remove the words 'quiet' and 'splash.' Save and close gedit. When you boot, the splash will be gone.

---

### Post by b_chris on 2007-05-23
Hey Chilli, I'm editing the grub with sudo gedit /boot/grub/menu.lst then, once I've saved an closed I'm updating it with sudo update-grub.

But it always returns to it's original state.... wierd.


regards.

---

### Post by chili555 on 2007-05-23
> I'm updating it with sudo update-grub.Not necessary. Please edit menu.lst and simply reboot.

---

### Post by b_chris on 2007-05-23
Thanks agian Chilli.....


Reagrds.

---

### Post by confused57 on 2007-05-23
It might have something to do with this line in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)

---

