---
title: "Duo Core processor"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-08-31
Hi there!

My laptop has a Duo Core processor. Do I automagically gain benefits from this under Ubuntu? Or should I be configuring/recompiling to take advantage?

Or will the advantages not be worth the effort?

FYI, I spend my PC time programming Java in NetBeans, using Firefox and playing World of Warcraft. I intend to carry out all of these activities in Ubuntu.

Cheers
Jem

---

### Post by grimmson on 2006-09-01
See this [http://www.linuxquestions.org/questions/showthread.php?t=450758](http://www.linuxquestions.org/questions/showthread.php?t=450758)
smb kernel seems to be well worth it. Without it your only running a single core. Probably don't have to recompile unless you feeling fancy.

---

### Post by pertti on 2006-09-01
It's really easy and worth it. You just have to install the proper kernel image and reboot.

Install the linux-686-smp package using System > Administration > Synaptic, or from the command line using:

```
sudo apt-get install linux-686-smp
```

This package ensures that you will always have the latest kernel and appropiate modules for your Core Duo.

Then reboot. You will see a couple of more entries on the boot menu. The new one will be selected by default. You can check if both cores are detected in System > Administration > System Monitor (the Resources tab should show two processors). If everything goes well you can then uninstall the previous kernel image (for the default installation, package linux-386).

Hope this helps!

---

### Post by Frank Golden on 2006-09-01
> **pertti said:**
> It's really easy and worth it. You just have to install the proper kernel image and reboot.

Install the linux-686-smp package using System > Administration > Synaptic, or from the command line using:

```
sudo apt-get install linux-686-smp
```

This package ensures that you will always have the latest kernel and appropiate modules for your Core Duo.

Then reboot. You will see a couple of more entries on the boot menu. The new one will be selected by default. You can check if both cores are detected in System > Administration > System Monitor (the Resources tab should show two processors). If everything goes well you can then uninstall the previous kernel image (for the default installation, package linux-386).

Hope this helps!
You can monitor both processors by right clicking a blank
area of the panel and choosing add to panel.
In the menu there is an applet called "cpu frequency scaling
monitor", choose and add two of them. You can then right click each one in turn, choose properties and using a dropdown set one to processor 0 and the other to processor 1. By default
a program called powernowd controls processor(s) speed, keeping
both at a reduced level until more is needed. Mine for (a 1.66GHz Core Duo) most of the time runs at 1GHz until I do something that needs more then it ratchets up to full power. These little
utilities keep track of this activity.You can fine tune these apps here.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

There is also a item
in the same place (the panel add menu) called system monitor
that shows CPU usage as a percentage when you hover your mouse over it. It shows realtime CPU usage as a graph. When you click it, it functions like the old ctrl+alt+delete in XP.
You can view running processes and programs memory usage etc.

Lastly use Synaptic and search for a utility called computertemp or some thing like that. Install and you will have available another panel applet from the "add to panel" menu that is a configurable CPU temperature monitor. It uses a sensor on the Core Duo and ACPI to display you processor temps.

You must be running the 686smp kernel to use both procs.
If you aren't the two "frequency scaling monitor apps"
won't have the dropdown option in properties to assign an applet to each processor.

---

