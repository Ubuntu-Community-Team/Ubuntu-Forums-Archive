---
title: "don't know what i did..."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by chris32680 on 2007-08-30
ok, i have two hd's in my pc, the first with xp and the second with ubuntu.

i stumbled across this 'how to' for speeding up some things...
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

and now i've somehow removed the xp boot option from the grub boot selection screen.

i *think* the problem happened when i tried to do the part at the very end for 'boot profile'.

anyone know how i can undo it ? :)

i did save copies of every file i edited...

thanks a ton

---

### Post by chris32680 on 2007-08-30
figured it out...

i guess it removed the xp entry from the menu.lst file.

so on another note...

has anyone done any of the recommendations from that link i posted or have any feelings on them one way or another?

thanks

---

### Post by dpar on 2007-08-30
try > sudo cp /boot/grub/whatever you named your backup /boot/grub/menu.lst

Edit:  right on, you solved it.....never mind what I said:)

---

### Post by chris32680 on 2007-08-30
thanks for the reply either way, dpar.

i appreciate it.

---

