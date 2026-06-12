---
title: "Now Boot Up Manager Is installed..."
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-10-31
Now Boot Up Manager Is installed how do I stop Grub from automatically booting into ubuntu after 5 seconds?

---

### Post by Kyral on 2005-10-31
[QUOTE=lavarock09]Now Boot Up Manager Is installed how do I stop Grub from automatically booting into ubuntu after 5 seconds?[/QUOTE]
I don't think BUM is supposed to give you a GUI control to GRUB. Its more to manage services ( like sshd, postfix, hotplug) that start at boot.

But I can answer your question!

Pop open a terminal and execute 

```
sudo gedit /boot/grub/menu.lst
```

Find the part that says something like "timeout" and change the number to the however many seconds you want the computer to wait before booting into the default (in this case Ubuntu). Also comment out (by putting a # in front) the part that says "hiddenmenu". This will force the GRUB boot list thing to appear when booting. Then it will wait however many seconds you specified before booting into Ubuntu.

Then just save the file. Make sure to backup the other one in case something happens (It shouldn't but better safe than sorry) with

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

### Post by 23meg on 2005-10-31
You don't need BUM for that; commenting out the "timeout" option in your /boot/grub/menu.lst should work.

(edit: Kyral beat me to it..)

---

### Post by Kyral on 2005-10-31
[QUOTE=23meg]You don't need BUM for that; commenting out the "timeout" option in your /boot/grub/menu.lst should work.

(edit: Kyral beat me to it..)[/QUOTE]
pwned ;P

---

