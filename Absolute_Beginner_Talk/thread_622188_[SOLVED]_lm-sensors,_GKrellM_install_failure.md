---
title: "[SOLVED] lm-sensors, GKrellM install failure"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-24
I used synaptic to install lm-sensors. next i did sudo sensors-detect and answered all the questions. Now, how do I get to use the information? Also, the config wrote to /etc/modules a few lines, all with #s in front of them? Do I remove the #s?

Is there a gui front end for these?

---

### Post by linuxwizard on 2007-11-24
You don't want to change anything that was add to /etc/modules.  Make sure you reboot computer very important this is one step I have seen people forgets to do. If you are going to use Gkrellm right click on Gkrellm > configuration > on right side of Gkrellm > Builtins > sensors > this is where you can setup you fans, Temps, voltage to show up in Gkrellm. No gui front end.

---

### Post by Mark_in_Hollywood on 2007-11-24
> **linuxwizard said:**
> You don't want to change anything that was add to /etc/modules.  Make sure you reboot computer very important this is one step I have seen people forgets to do. If you are going to use Gkrellm right click on Gkrellm > configuration > on right side of Gkrellm > Builtins > sensors > this is where you can setup you fans, Temps, voltage to show up in Gkrellm. No gui front end.

OK, I've rebooted, but NOWHERE do I find any icon to:

right click on Gkrellm > configuration > on right side of Gkrellm > Builtins > sensors >

where is this program located?

---

### Post by linuxwizard on 2007-11-24
You do have Gkrellm installed ? If so you might have to add it to your Application menu. Once you open Gkrellm it will show on your desktop >right click on Gkrellm > configuration > on right side of Gkrellm > Builtins > sensors >

---

### Post by Mark_in_Hollywood on 2007-11-24
> **linuxwizard said:**
> You do have Gkrellm installed ? If so you might have to add it to your Application menu. Once you open Gkrellm it will show on your desktop >right click on Gkrellm > configuration > on right side of Gkrellm > Builtins > sensors >

Gkrellm shows as installed via Synaptic. Applications/Add/Remove, once loaded, does not show Gkrellm or lm-sensors. Yikes!

Would Synaptic have installed the right GTK? Dependencies?

---

### Post by linuxwizard on 2007-11-24
You will have to add Gkrellm to your Application menu if you don't see it listed. It should be under System Tools.

This is your Application Menu. 
[https://help.ubuntu.com/7.10/user-guide/C/applications-menu.html](https://help.ubuntu.com/7.10/user-guide/C/applications-menu.html)

lm sensors will not show in Application Menu.

---

### Post by Xavieran on 2007-11-24
type in gkrellm from a terminal-that might start it.

if it starts you can make GKrellM start up automatically at startup by adding an entry in System>Preferences>Sessions

---

### Post by Mark_in_Hollywood on 2007-11-24
Problem Solved.

Thanks, all.

---

