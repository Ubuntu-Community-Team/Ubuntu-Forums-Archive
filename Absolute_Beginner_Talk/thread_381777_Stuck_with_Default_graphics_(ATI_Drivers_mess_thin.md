---
title: "Stuck with Default graphics (ATI Drivers mess things up)"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by jmattos on 2007-03-11
Hi all

Has anyone experienced this? I think I'm stuck with the default drivers because whenever I install the ATI drivers

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I've tried both ways now, using the built in drivers, and the binaries supplied by ATI.

the problem is that after booting (which looks so much better) after about 5 minutes teh screen goes blank, and I have to restart the computer.

can anyone help me?

---

### Post by overdrank on 2007-03-11
> **jmattos said:**
> Hi all

Has anyone experienced this? I think I'm stuck with the default drivers because whenever I install the ATI drivers

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I've tried both ways now, using the built in drivers, and the binaries supplied by ATI.

the problem is that after booting (which looks so much better) after about 5 minutes teh screen goes blank, and I have to restart the computer.

can anyone help me?

Witch ati card are you using?

---

### Post by masteryurez on 2007-03-11
[http://www.getautomatix.com](http://www.getautomatix.com)

Goto "Installation" and install automatix2.

After that write this code:
```
sudo apt-get install automatix2bleeder
```

Goto Program > System Tools > Automatix2Bleeder

Start the program and go to "Graphic Card Driver" 

Install the ATI-driver and restart X on your computer.
Ctrl+Alt+Backspace (Close all open program first)

Log in again and your ATI-driver will hopefully work!

Good Luck Ubuntu user

---

### Post by jmattos on 2007-03-11
> **paul capps said:**
> Witch ati card are you using?

I've got an ATI Radeon x1800 PCI-E

---

### Post by jmattos on 2007-03-11
> **masteryurez said:**
> [http://www.getautomatix.com](http://www.getautomatix.com)

Goto "Installation" and install automatix2.

After that write this code:
```
sudo apt-get install automatix2bleeder
```

Goto Program > System Tools > Automatix2Bleeder

Start the program and go to "Graphic Card Driver" 

Install the ATI-driver and restart X on your computer.
Ctrl+Alt+Backspace (Close all open program first)

Log in again and your ATI-driver will hopefully work!

Good Luck Ubuntu user

Hmm the only problem is that I only see "NVidia Card Driver" in the list :( nothing about ATI drivers

---

### Post by jmattos on 2007-03-12
Does anyone else know why my screen might be going blank after 5-10 minutes? It's not the screensaver, and it doesnt happen when I use the default drivers that Ubuntu installs when I install it (Mesa).

Help!

---

### Post by jmattos on 2007-03-18
> **jmattos said:**
> Does anyone else know why my screen might be going blank after 5-10 minutes? It's not the screensaver, and it doesnt happen when I use the default drivers that Ubuntu installs when I install it (Mesa).

Help!

anyone?

---

