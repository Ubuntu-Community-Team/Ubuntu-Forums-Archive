---
title: "Xubuntu Synaptic Package Manager"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bqm3043 on 2008-04-04
I'm new to Xubuntu. When a package in installed from Synaptic Package Manager, the new program doesn't show up in the menu anywhere. Only programs installed with add/remove show up in the menu. How do I get the installed programs to show up in the XFCE menu, after being installed with Synaptic Package Manager?

---

### Post by kesman on 2008-04-04
Many applications don't have menu entry, you will probable have to make one yourself. The executables are usually in /usr/bin . Before anything, run the application from terminal. 
For example if you installed "xmms", then you would only type xmms in terminal to launch it.

---

### Post by kellemes on 2008-04-04
> **bqm3043 said:**
> I'm new to Xubuntu. When a package in installed from Synaptic Package Manager, the new program doesn't show up in the menu anywhere. Only programs installed with add/remove show up in the menu. How do I get the installed programs to show up in the XFCE menu, after being installed with Synaptic Package Manager?

Don't forget a lot of applications are run from terminal and normally don't add an entry to your menu..
Graphical applications should add an entry indeed.
Not sure how XFCE (your window manager) handles this.. maybe you need to logout/login to get the entries? Don't know.

---

