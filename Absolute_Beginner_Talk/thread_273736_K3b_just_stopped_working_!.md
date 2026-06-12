---
title: "K3b just stopped working !"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-08
I even uninstalled reinstalled it, restored a Ubuntu image, and when I click on it ,nothing happens :(

---

### Post by maniacmusician on 2006-10-08
does it display an error when you run it from the terminal/Konsole?

---

### Post by Drakkor on 2006-10-08
Funny,but it does actually come up after about 5 minutes.....
How to start in terminal ?

---

### Post by ComplexNumber on 2006-10-08
> **Drakkor said:**
> Funny,but it does actually come up after about 5 minutes.....
How to start in terminal ?
type in 'k3b' into the terminal.

---

### Post by Drakkor on 2006-10-08
drakkor@drakkor:~$ k3b
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
drakkor@drakkor:~$

---

### Post by MarkoSK on 2006-10-29
got just the same thing....and now k3b doesn't burn anything anymore....!!: ???

---

### Post by MarkoSK on 2006-10-29
aperantly i fixed this problem---
all i did was:

sudo apt-get --reinstall install kdelibs

and

sudo apt-get --reinstall install kde

and after that everything works fine again :D

---

