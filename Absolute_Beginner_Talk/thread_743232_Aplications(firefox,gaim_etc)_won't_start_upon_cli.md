---
title: "Aplications(firefox,gaim etc) won't start upon clicking.(Gnome)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by cardinals_fan on 2008-04-02
> **Auston said:**
> Good Day,


Distro: opensuse 10.3
Gnome

After I do
#modprobe ndiswrapper
I can't start any applications, not even terminal.
Not with right clicking on the screen, not by clicking on panel.

If I reboot computer and start any thing it would start, but again when I do
#modprobe ndiswrapper
nothing would starts any more.
Applications what are already running keep running.

Any ideas?

Thank you.
I'm not sure what the problem is, but why are you typing 'modprobe ndiswrapper' so often?  What that command does (in geek speak) is insert the ndiswrapper module into the kernel.  What that does (in English) is set ndiswrapper to be loaded by the system's inner workings.  You shouldn't need to type it every time you start up.

---

