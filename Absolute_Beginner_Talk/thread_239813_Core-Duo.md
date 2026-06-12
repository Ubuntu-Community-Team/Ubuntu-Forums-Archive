---
title: "Core-Duo"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by canarsie on 2006-08-19
My computer runs off of the intel core-duo processer, but in the system monitor it onfy displays one processer.  How can I find out if it doesn't recognize the other CPU or just doesn't display it seperately and if it doesn't see it what should I do about it?

---

### Post by taurus on 2006-08-19
You need the i686-smp kernel, not the default kernel that comes with the installer, i386.

---

### Post by Frank Golden on 2006-08-19
> **taurus said:**
> You need the i686-smp kernel, not the default kernel that comes with the installer, i386.
To begin if you are using the kernel that came with Ubuntu
you need to use Synaptic Package Manager to change to the 686smp
kernel. This will allow Ubuntu to see both cores. Make sure
you have powernowd installed. Again in Synaptics (use search feature). This will by default automatically throttle the processors when load is low and run at full power when needed.
All this assumes you are using Ubuntu (not Kubuntu or Xbuntu).
You can then right click the panel at the top of your
screen and choose "Add to panel". From the menu choose "CPU freqency scaling monitor" and click add twice. You will now have two icons in your
panel right click each one and use the dropdown to set one to "0" and the
other to "1". You will now have visual indications of each processors
status. Powernowd will automatically scale your proc frequencies to match
demand and show you this graphically in realtime. You can also use the "Add to panel" tool to add system monitor to your panel. Use Synaptic to install 
computertemp (again use search feature). Use "Add to panel" to add "computer temperature monitor" tool to panel. Your computer should have
ACPI most new ones do. This tool will use the temp sensors that ACPI uses
to keep tabs on your processor temps.

---

