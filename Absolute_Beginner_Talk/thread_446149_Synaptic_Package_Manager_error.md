---
title: "Synaptic Package Manager error"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Gizmo356 on 2007-05-16
Hey guys I got this error when I tried to run the Synaptic Package Manager by using the right click menu

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I ran dpkg --configure -a in the Terminal and it gave me this error requested operation requires superuser privilege.

What should I do?

I also get this error when I click the Synaptic Package Manager icon it gives me this error "It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So I ran sudo apt-get install -f in the terminal and I got this error dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

So anyone know what I should do?

---

### Post by celticbhoy on 2007-05-16
To start with run dpkg --configure -a as :-

sudo dpkg --configure -a

then see where you get.

---

### Post by Gizmo356 on 2007-05-16
> **celticbhoy said:**
> To start with run dpkg --configure -a as :-

sudo dpkg --configure -a

then see where you get.

Thanks a-lot man that fixed it:)

---

