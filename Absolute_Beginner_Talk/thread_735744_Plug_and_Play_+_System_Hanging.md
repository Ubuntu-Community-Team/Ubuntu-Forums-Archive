---
title: "Plug and Play + System Hanging"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by koresho on 2008-03-25
Hey everyone, I actually have two questions. 
I am running Ubuntu 8.04 Beta, not sure if this is a beta issue or not so mods move as necessary please.

I don't seem to have Plug and Play USB on my system- I had to reboot to get the kernel to see my Verizon Aircard and I have to reboot to get Ubuntu to recognize my wireless Logitech mouse.
Also, when the system hangs, in Windows you have the task manager that you can use to kill hanging apps... I am sure Ubuntu has something similar. How do I pull this up? Thanks so much.

---

### Post by zen_waters on 2008-03-26
as far as killing apps, try this:

open a terminal window:

type "ps -aux | more" that will show you the processes, depending on the process id number say of apache you might see httpd with a process id of 433

then you would type kill 433, which would terminate the app.

---

### Post by koresho on 2008-03-26
Problem with that is, when it is hung like that I can't open the console. I can't use the Alt+F2, I can't do anything. Usually I can't even move the mouse. Is there a key combination to always open the console? I figured out the best way to do anything about that so far is to do a Ctrl+Alt+Backspace which apparently logs me out, it kills all the processes and brings me to the login screen- much shorter than a full reboot. But I am hoping that I don't have to do that... considering that way I lose anything I am working on.

---

### Post by LowSky on 2008-03-26
there is a aplet you can add to you panel called Kill application.

right click on either gnome panel got to add aplet

---

### Post by koresho on 2008-03-26
That's helpful, but what I'm wondering is: what if the entire system is hung?
I'm really asking if there is an app or a command that would give the same (or better) functionality than Windows Task Manager

---

### Post by SunnyRabbiera on 2008-03-26
try control-alt-backspace, that will halt your current session and you can start over.
also there is a system monitor in ubuntu under system>administration>system monitor, it has a task manager under "processes"

---

### Post by bwang on 2008-03-26
If the entire system hangs try the "Magic SysRq Key"([http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))
If that doesn't work it means the kernel has crashed. Then you have to do a hard reboot.

---

### Post by koresho on 2008-03-28
Update: my hotplugging USB works again now. 
It was my HP webcam, making waves... cracked the case open and unplugged it (I have literally never used it anyway) and all my problems are solved. This is awesome. 

bwang: Thanks that was exactly what I was looking for! Alt+SysRq+e = SIGTERM every process except INIT. thanks!

---

