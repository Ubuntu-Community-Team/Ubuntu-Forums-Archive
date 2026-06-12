---
title: "heat monitoring utility"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by ADH on 2006-09-16
Is there a Linux utility to monitor CPU and system temperature?

---

### Post by oyvindaa on 2006-09-16
There's a nice program called gkrellm.

You can locate it via the search utility in Synaptic.

You'll also need to install gkrellmd (the daemon).

Try locating it and installing it and I'll tell you what to do from there if you want me to.

---

### Post by ADH on 2006-09-16
I downloaded it (I think I got the right file.)  How do I install it?  It's a tar.gz file.

---

### Post by oyvindaa on 2006-09-16
No mate, you don't get tar.gz files from Synaptic.

Go to (in the Ubuntu menu): System --> Administration --> Synaptic 

Type in your password and then Synaptic opens up, and you can search for gkrellm and gkrellmd. Right click on both and mark them for installation. Next, you click on Apply or Use or whatever it is in the english version.

It'll install itself mate.

---

### Post by fragos on 2006-09-16
There are a few steps to this.  You will need to install lm-sensors, libsensors3 and a program to display the output.  gkrellm is a good choice but I prefered to install sensors-applet.  This will give you "Hardware Sensors Monitor" for the applet toolbar.  The display is simpler and doesn't require a window on your desktop.  Both work well, it's just personal choice.

---

