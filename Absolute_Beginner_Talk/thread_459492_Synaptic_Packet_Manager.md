---
title: "Synaptic Packet Manager"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jimmydee on 2007-05-30
My Synaptic Packet Manager stopped working. It gives an error message, and when I try to do what it says , in the terminal, I get another message that says I need root privileges. What can I do?

---

### Post by TheMono on 2007-05-30
To launch it in the terminal, type 'gksudo synaptic' to tell it to run with root privileges.

[edit: Sorry, I just realised what you were saying. Just type the word 'sudo' before whatever command it tells you to use. Then enter your password, and it will run with root privileges]

---

### Post by TheMono on 2007-05-30
As an addendum to that, when you go to type in your password, it will not show up any numbers or letters or stars or anything. Don't worry, it is going in.

---

### Post by alienexplorers on 2007-05-30
If you are getting a message stating to run something with dpkg as the start, go to terminal and type in sudo dpkg --configure -a

---

