---
title: "Change Boot Loader Preferences"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by LPJuice on 2007-01-22
I'm not familiar with LINUX commands, kernels, or anything else. I installed it  on a secondary partition after I installed Windows on the primary partition. Other people (not computer literate at all) also use this machine and I want the default boot to go to Windows. According to Windows, the default is windows and it shows no other bootable OS. According to the ubuntu bootloader, ubuntu is default with windows as a secondary choice. Can I keep the ubuntu bootloader but change the default boot OS to windows, or use the windows bootloader and have it default to windows but show ubuntu as a selectable option???

---

### Post by Shatrat on 2007-01-23
Yes.
Use the following in a termina.
gksudo gedit /boot/grub/menu.lst

Look for a line that says 
default 0
Change that to 
default #
where # is the number of the entry which is for windows, making sure you start counting at 0

Or...you could just cut and paste the windows boot entry from the bottom of the list to the top of the list I guess.

---

### Post by LPJuice on 2007-01-23
Nice. It worked. Thanks a million man.

One more Q just for kicks. Anyone know of a good tutorial/FAQ where I can learn commands in a logical order so I can use the terminal. Right now I don't understand the syntax or file system.

Sincerely,
Ubuntu n00b :(

---

### Post by Shatrat on 2007-01-23
This one is decent.
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)
There's a lot more great info to be found at that site.

The most important command is ```
fortune
```.

---

