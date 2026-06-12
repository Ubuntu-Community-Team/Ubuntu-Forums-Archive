---
title: "How to uninstall?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-10-01
Hello i wounder how to uninstall lets say cedega and other apps?

---

### Post by Mr Frosti on 2006-10-01
The way to uninstall applications depends on the way that you installed them. For example, if you installed a .deb, or package, you can uninstall this package by opening up "Synaptic Package Manager" and searching for it, and then uninstalling. 

If you compiled and installed the application by hand, you are at the mercy of any included uninstallation scripts. Alternately you can search for the installed files and remove them individually, though I do not recommend this.

It is always best to stick with packages when possible.

---

### Post by christhemonkey on 2006-10-01
Go into synaptic package manager (and/or "add remove programs") and click the application and select uninstall or remove.

---

### Post by haxer on 2006-10-01
Ok hmm.. then im ****** thanks for the help btw

---

### Post by oedipuss on 2006-10-01
> **haxer said:**
> Hello i wounder how to uninstall lets say cedega and other apps?

Just remove the package , in synaptic. Find the package you want to uninstall in the list, right click it, and select 'mark for removal'.  There's an option for complete removal too, which deletes any configuration files the app may have created.

Or, if you installed the app by compiling it (typing ./configure, make and make install etc), go to the source code's directory from a terminal and type 'make uninstall'. If you don't know what I'm talking about, then you've most probably installed apps from packages, so you can ignore this paragraph :D

---

