---
title: "[SOLVED] Gnome commander as root"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-22
Can someone please tell me if there is a way to use gnome commander in the root mode??

Thanks

---

### Post by taurus on 2007-01-22
<Alt>F2 -> gksudo nautilus

---

### Post by squrl on 2007-01-22
Thanks Taurus.  Don't you ever sleep??

---

### Post by taurus on 2007-01-22
Sleep!  What's that?  :biggrin:

---

### Post by squrl on 2007-01-22
Somehow that doesnt make gnome commander run in root mode.

---

### Post by taurus on 2007-01-22
What exactly are you trying to do?  If I have a better understanding, perhaps I can give you a precise command or a link.  Otherwise, try to put a sudo in front of a command from a terminal.

---

### Post by rocknrolf77 on 2007-01-22
Are you talking about nautilus or gnome-commander?

If it's gnome-commander I guess you should type ```
gksudo gnome-commander
```

Or check the box "run in terrminal" in the run dialog.

---

### Post by squrl on 2007-01-22
I wanted to use gnome commander for some of the commands like copy and move to save some typing but it wont do that unless it is in root mode.

---

### Post by taurus on 2007-01-22
For copying and moving, gksudo nautilus should do just fine though!  Otherwise, run

```
sudo cp **filename** **destination**
sudo mv **filename** **destination**
```

---

### Post by louieb on 2007-01-22
I use gnome-commander too. rocknrolf77 has it right. I just tried it.
Alt+F2   >  gksudo  gnome-commander

---

