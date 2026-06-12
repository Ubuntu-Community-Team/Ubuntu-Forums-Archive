---
title: "HowTo: connect bluetooth on startup"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-19
i connect to my bluetooth mouse using the command "sudo hidd --search" , but i should run this command every time i login to the system, once upon a time before i entered to the desktop on the login screen the mouse connected by itself , i dont know how that happened but it is a behavior i would like to accomplish, any idea to auto connect on boot ???

---

### Post by Inxsible on 2007-06-22
One thing you can do is add that command to a script and make sure the scipt is executed on boot

---

### Post by akkad on 2007-06-22
alright but how to do it, am still fresh with ubuntu.

---

### Post by bclark on 2007-06-22
> **akkad said:**
> alright but how to do it, am still fresh with ubuntu.

if you want any scripts to run at start up call them from
~/.bashrc

just open ~/.bashrc in gedit and put 'sudo hidd --search' in there and then run
source ~/.bashrc to enable the changes you've made

---

