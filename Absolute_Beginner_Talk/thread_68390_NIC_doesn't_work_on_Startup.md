---
title: "NIC doesn't work on Startup"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-09-22
...but if I disable it, and re-enable it, then it picks up and works fine!
Anybody know why this happens or how I can fix it? not a major issue, but really annoying.

---

### Post by Jussi Kukkonen on 2005-09-23
Do you have a usb network card by any chance? 

It seems that the usb subsystem is loaded after the network interfaces are brought up... Which of course screws the network connection. I think this could be changed...

---

### Post by fordfan753 on 2005-09-23
[QUOTE=Jussi Kukkonen]Do you have a usb network card by any chance? 

It seems that the usb subsystem is loaded after the network interfaces are brought up... Which of course screws the network connection. I think this could be changed...[/QUOTE]

This could be changed with init scripting or BUM (Boot Up Manager), but this may not be your problem.

---

### Post by the_purulent on 2005-09-23
I do not have a usb card.  I have a dlink (530 I think ?) PCI Interface.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=the_purulent]I do not have a usb card.  I have a dlink (530 I think ?) PCI Interface.[/QUOTE]

Hmm, this is a strange problem, I haven't heard of anything like this happening before. When you first boot (before you deactivate, then reactivate it) type "sudo ifconfig" and post that here.

---

