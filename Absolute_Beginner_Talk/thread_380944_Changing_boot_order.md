---
title: "Changing boot order"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-03-10
I'm running a Vista/ubuntu system and would like to know the best way to change the boot order so that if I don't have to manually start in Vista.  Basically, I want the machine to boot to Vista if I'm not there waiting for the boot screen.
Is it better to do so in Ubuntu or in Vista?
Thanks

---

### Post by drs305 on 2007-03-10
If you are using Grub to start the machine, you can edit the menu list  /boot/grub/menu.lst

The order on my machine usually goes Ubuntu, Ubuntu Recovery, then Windows. You can use a text editor and move them around. (Make a backup, of course). You can also edit the timeout before it automatically boots to the first option. The default is 10 seconds.

---

### Post by chalex on 2007-03-10
[http://www.gnu.org/software/grub/manual/grub.html#default](http://www.gnu.org/software/grub/manual/grub.html#default)

---

### Post by dpar on 2007-03-10
See post #9 on this tread   [http://www.ubuntuforums.org/showthread.php?t=223799&highlight=grub+boot+order](http://www.ubuntuforums.org/showthread.php?t=223799&highlight=grub+boot+order)
Its the same thing chalex said, but explained differently:)

---

### Post by pcostanza on 2007-03-10
Thanks for all the quick replies.  I'll git er done I'm sure with that help.
I'm also going to look at Easy BCD or VistaBootloader though I hear both do not see the Ubuntu partition.  I'm thinking the easy way is the text editor.

Thanks again.

---

### Post by rusty4r on 2007-03-10
You should take a look at Herman's Grub page. Every thing you could possibly need about Grub. IMHO it should be like mandatory reading. hehe
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

