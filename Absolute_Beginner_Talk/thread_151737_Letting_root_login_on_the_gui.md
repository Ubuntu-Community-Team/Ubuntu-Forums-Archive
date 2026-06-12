---
title: "Letting root login on the gui"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-03-28
I changed root's password, so i can use the root account in other usernames. Unfortunately i cant log into gnome as root. How can i change that?

---

### Post by NeghVar on 2006-03-28
System> Administartion> Login Screen Set up

Security tab, then check the allow root to log in gdm, note this is for gnome. Also there are securioty risks with taking this action.

---

### Post by AndrewCaul on 2006-03-28
Are you aware of the potential security risks involved? It's not very difficult to just use sudo when you need to be root.

---

### Post by dermotti on 2006-03-28
I don't belive in sudo. I have yet to see a compelling reason to use it, unless multiple people are adminstering the machine.

---

### Post by aysiu on 2006-03-28
[QUOTE=dermotti]I don't belive in sudo. I have yet to see a compelling reason to use it, unless multiple people are adminstering the machine.[/QUOTE] How about it's easier than logging out of user, logging in as root, making changes, logging out of root, and then logging back in again as user?

Create a simple launcher for yourself (Gnome) *gksudo nautilus* or (KDE) *kdesu konqueror* if you prefer to make root changes through the GUI.

---

### Post by gr0kzer0 on 2006-03-28
I'm well aware of the risks involved with root - that i might kill my installation, or that when i get online some malicious cracker might "own" my box. But i'm an inveterate fiddler, i tamper and explore and want to know all the nooks and crannies in my computer. The root acc being disabled by default was a red rag to me, demanding to be reenabled. I do use "sudo" mostly, prob turn root off.

---

### Post by aysiu on 2006-03-28
[QUOTE=gr0kzer0]I'm well aware of the risks involved with root - that i might kill my installation, or that when i get online some malicious cracker might "own" my box. But i'm an inveterate fiddler, i tamper and explore and want to know all the nooks and crannies in my computer. The root acc being disabled by default was a red rag to me, demanding to be reenabled. I do use "sudo" mostly, prob turn root off.[/QUOTE] The *gksudo nautilus* or *kdesu konqueror* launchers let you do this, believe it or not.

---

### Post by NeghVar on 2006-03-28
o well if he wants to use root then hey its his call, i just threw in the warning incase he didnt no about root and the risks

---

