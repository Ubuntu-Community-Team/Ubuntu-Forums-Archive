---
title: "ubuntu won't shut down"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by faultedperfection on 2007-01-27
Hi, I have a new problem, Ubuntu will not shut down, or restart. Everytime I try it just hangs and nothing happens, I can't use the keyboard or mouse, and it forces me to use the power button on the computer.

Any suggestions?

Thanks

---

### Post by phossal on 2007-01-27
What was the last thing you configured?

---

### Post by phossal on 2007-01-27
When restarting, at what point does it hang? Does it make it to GRUB?

---

### Post by faultedperfection on 2007-01-27
i installed 3ddesk, and configured the keyboard shortcut to be the "windows" key

---

### Post by faultedperfection on 2007-01-27
it will boot all the way up into ubuntu, the problem is is that when I click the restart button, or shut down button, it just hangs on the desktop, allowing me to do nothing

---

### Post by r4ik on 2007-01-27
Try sudo reboot from the command line 
The screen will go black and ask you to login ignore it.
Should work.
Undo the changes you made and see if that helps.

---

### Post by PrinceArithon on 2007-01-27
Another thing you can do is go to your terminal and type:

sudo init 6

This will restart the system, or you can type in:

sudo init 0

This will shutdown your system

---

### Post by guysmiley25 on 2007-01-27
I had that problem and [this]("http://www.ubuntuforums.org/showpost.php?p=1722087&postcount=13") fixed it for me.

---

