---
title: "Skip Grub Menu and Reduce Touchpad Sensitivity"
date: 2011-04-26
forum: Apple Hardware Users
---

### Post by gast0r on 2011-04-26
I've just installed the Natty beta 2 along side OSX on my Macbook Pro 5.3. Everything running smoothly however I'd prefer the Grub menu didn't show every time I booted up, I already have Refit for that. Is there any way to skip it?

Also, the trackpad is really sensitive and I had to disable using touch as a button because of it, which is kinda' annoying. Any help would be great.

---

### Post by gast0r on 2011-05-01
bump

---

### Post by labaom on 2011-05-01
This will help you here. [http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/)

To make it disappear set it to 0. However, I suggest you make it 1 just in case you have to select something from the menu if something were to go wrong.

---

### Post by gast0r on 2011-05-01
> **labaom said:**
> This will help you here. [http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/)

To make it disappear set it to 0. However, I suggest you make it 1 just in case you have to select something from the menu if something were to go wrong.

When I open 'sudo gedit /boot/grub/menu.lst' I just get a blank text file, so this doesn't really help.

---

