---
title: "Dual Boot prime for XP."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wowbuntu000 on 2007-04-12
Hello.

I have dual boots (XP and Ubuntu).

How can I edit boot option?
I want to change delay [10 sec. to 3 sec],
and how to set the arrow indiciate Windows XP primary?


LIke this:

Ubuntu
Ubuntu (Safe)
Memtest
other operations:
**->Windows XP**

---

### Post by divague on 2007-04-12
just edit the the grub menu

$sudo gedit /boot/grub/menu.lst

for the time change the timeout option. In order to have windows XP first just move the windows boot lines (at the end of the file) and put them before ubuntu.

---

### Post by aysiu on 2007-04-12
You have to edit the /boot/grub/menu.lst file.

In [the terminal](http://www.psychocats.net/ubuntu/terminal), paste in this command: ```
sudo nano -B /boot/grub/menu.lst
``` Scroll through the file. There should be a line that says ```
timeout 10
``` Change that line to say ```
timeout 3
``` There should also be a line that says ```
default 0
``` Change that to say ```
default 4
``` Then save (Control-X, Y, Enter). That's it!

---

### Post by aysiu on 2007-04-12
> **divague said:**
> $sudo gedit /boot/grub/menu.lst Three things:
1. Graphical programs shouldn't use *sudo*. In this case, ```
gksudo gedit /boot/grub/menu.lst
``` is the proper way to launch Gedit as root. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2. One should **always** back up a system file before editing it.

3. The command invoking Gedit assumes the OP has Ubuntu (and not Xubuntu or Kubuntu). If the OP is running one of the latter, all she or he will get is ```
gedit: command not found
```

---

