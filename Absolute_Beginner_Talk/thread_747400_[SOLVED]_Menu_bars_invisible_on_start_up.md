---
title: "[SOLVED] Menu bars invisible on start up"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by bzzzzz on 2008-04-06
I've been playing around trying to install AWN (avant window navigator) and after installing and uninstalling it several times I've got a bit fed up.  I've spent the weekend reading round the forums and although I'm getting closer I think I've hit a wall and am ready to give up.

My problem is that when I boot up neither menu bars are visible unless I login using the safety version of ubuntu.  I think they are present because if I press alt-F2 and type **gnome-panel &** into a terminal, it says that the panel is already running.

Incidentally I don't know how to remove avant-window-navigator from the machine.  It appears in both the applications menu and the AWN manager is present in the system preferences menu.  However if I try and run the program in a terminal it just says "Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

I've looked around at installing compiz but I'm not exactly certain how to do this and I'd rather just quit for now and try and get the computer running normally before going any further.

---

### Post by Frak on 2008-04-06
It seems as if you don't have the right hardware drivers installed for your system (Error: Screen isn't composited). This is a theory, but you could see if its the issue by running

```
jockey-gtk
```

In the terminal or by pressing alt+f2 if you can't access the menus.

Install the drivers if it asks, then reboot and see if the error is resolved.

---

### Post by bzzzzz on 2008-04-06
on typing **jockey-gtk** into the terminal
all i get is this 

bash: jockey-gtk: command not found

---

### Post by Frak on 2008-04-06
Do you by any chance know what video card you have?

---

### Post by bzzzzz on 2008-04-06
In the device manager that I can access when I boot up xp (I'm running ubuntu through wubi) it says under display adapters

Intel(R) 82852/82855 GM/GME Graphics Controller

---

### Post by bzzzzz on 2008-04-11
I sorted this out for myself.

I'm not sure what I did, but it is working now.  

Basically I just uninstalled and installed loads of different things from different websites and it just started working.

Critically I believe I uninstalled and reinstalled all my drivers for compiz

---

### Post by Desmo UK on 2008-04-11
Mine has started doing similar tonight. Going to dump compiz and see if it works OK again, then re-install compiz.

---

