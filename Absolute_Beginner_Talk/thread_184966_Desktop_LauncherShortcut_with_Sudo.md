---
title: "Desktop Launcher/Shortcut with Sudo?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Scrif on 2006-05-30
I have installed Ethereal via the Synaptic PM. It did not create an icon in my Apllications menu (I thought it would??) so now I have created a desktop Icon/Launcher to run Ethereal. The program starts however when I try to start a capture, I get a message about not having privilege.

If I go to the USR/BIN dir and run "sudo ethereal", it works.

Is there a way to apply SUDO to a launcher/icon?

---

### Post by Perfect Storm on 2006-05-30
Try with gksudo infront of ethereal.


```
gksudo ethereal
```



```
smeg
```
To open the menu editor.

---

### Post by johnc4510 on 2006-05-30
yes, right click on a panel where you want the icon. select add to panel. Choose custom launcher. name it ethereal and in the command line put sudo ethereal
Note: It might need gksudo ethereal. I can't remember for sure.

---

### Post by Scrif on 2006-05-30
Thanks for the help.

making launcher cmd line look like "/usr/bin/gksudo ethereal" worked

p.s. Any reason why Ethereal didnt create its own icon in Application menu by default?

---

### Post by Super King on 2006-05-30
It should have, it did for me (in Breezy anyway).

---

### Post by Perfect Storm on 2006-05-31
Did you try to kill the panel first to see if it show up?

---

