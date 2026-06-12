---
title: "synaptic not working"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by heart_reaver on 2005-05-28
hi there

i have installed ubuntu version 4.10 
i am not able to run synaptic in termial, it ask to do it in gui.when started runing in gui it ask for password and i give root password but nothing happen, then i try user password then also noting happen.

i need to update gcc to install other packages.

---

### Post by Kamping_Kaiser on 2005-05-28
[QUOTE=heart_reaver]hi there

i have installed ubuntu version 4.10 
i am not able to run synaptic in termial, it ask to do it in gui.when started runing in gui it ask for password and i give root password but nothing happen, then i try user password then also noting happen.

i need to update gcc to install other packages.[/QUOTE]

Synaptic is a graphical program. It will not run in  a shell. If you need somthing to run in a shell, there is 'aptitude' and the 'apt-' programs.

Just a question,
Do you have a root acount? just a user with sudo access?

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=heart_reaver]hi there

i have installed ubuntu version 4.10 
i am not able to run synaptic in termial, it ask to do it in gui.when started runing in gui it ask for password and i give root password but nothing happen, then i try user password then also noting happen.

i need to update gcc to install other packages.[/QUOTE]

try running this command, tell me what happens:

gksudo synaptic

---

