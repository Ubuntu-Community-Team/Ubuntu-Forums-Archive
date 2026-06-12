---
title: "Throttling Down CPU"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2006-08-16
Hey All,
    I just put ubuntu on a new Dell XPS M1210 w/an intel centrino duo 1.66 GHz processor. I'm wondering if there are any applications that I can use to see the speed my processor is running at, and step it down in order to conserve battery life. Thanks for any suggestions you can provide.

---

### Post by kaffelars on 2006-08-16
There's a Gnome applet that does this. However, you need to be root to change the frequency in the applet. It's possible to change that though, so that ordinary users can change the throttling. I'll look it up when I get home :)

---

### Post by Klaidas on 2006-08-16
To see your CPU working you can go to System -> Administaration -> System monitor

But what I prefer is commandline application ```
top
```
It show more that you need to know ;)

---

### Post by smurphv2 on 2006-08-16
to clarify, I'm looking for an application that will allow me to set the clock speed of the CPU, or have it dynamical change within a given range based on the current load.

---

### Post by Iarwain ben-adar on 2006-08-16
Hi,

in Kubuntu, there is a program called Kpowersave.
It can set your cpu to half it's speed, if you are not using your pc cpu intensive (and automaticaly sets is full speed when needed)

Don't know about a Gnome app though...


Iarwain

---

### Post by Frank Golden on 2006-08-16
> **Iarwain ben-adar said:**
> Hi,

in Kubuntu, there is a program called Kpowersave.
It can set your cpu to half it's speed, if you are not using your pc cpu intensive (and automaticaly sets is full speed when needed)

Don't know about a Gnome app though...


Iarwain
To begin if you are using the kernel that came with Ubuntu
you need to use Synaptic Package Manager to change to the 686smp
kernel. This will allow Ubuntu to see both cores. Make sure
you have powernowd installed. Again in Synaptics (use search feature). This will by default automatically throttle the processors when load is low and run at full power when needed.
All this assumes you are using Ubuntu (not Kubuntu or Xbuntu).
You can then right click the panel at the top of your
screen and choose "Add to panel". From the menu choose "CPU freqency scaling monitor" and click add twice. You will now have two icons in your
panel right click each one and use the dropdown to set one to "0" and the
othe to "1". You will now have visual indications of each processors
status. Powernowd will automatically scale your proc frequencies to match
demand and show you this graphically in realtime. You can also use the "Add to panel" tool to add system monitor to your panel. Use Synaptic to install 
computertemp (again use search feature). Use "Add to panel" to add "computer temperature monitor" tool to panel. Your computer should have
ACPI most new ones do. This tool will use the temp sensors that ACPI uses
to keep tabs on your processor temps.

---

### Post by smurphv2 on 2006-08-17
Thanks Frank, that seems to have worked. Thanks everyone else as well for their suggestions.

---

### Post by tribaal on 2006-08-17
Another nice little applet I like using is ```
emitfreq-applet
``` (from universe).
This shows your core's temperature (via acpi), and lets you scale your CPU's frequency with a right click. Really nifty.

Hope this helps.

- trib'

---

### Post by Frank Golden on 2006-08-17
> **tribaal said:**
> Another nice little applet I like using is ```
emitfreq-applet
``` (from universe).
This shows your core's temperature (via acpi), and lets you scale your CPU's frequency with a right click. Really nifty.

Hope this helps.

- trib'
Is this Kubuntu app. Don't see in Ubuntu Synaptic.
Or with sudo apt-get install emitfreq-applet, says package doesn't exist.

---

### Post by justynbutler on 2006-08-31
Hi, the correct spelling of this applet is emifreq-applet, try that. No it's not for KDE, it's Gnome 2.

Justyn

---

### Post by pharcyde on 2006-09-02
I'm not sure how comfortable you are with the command line but you can always use the cpu scaling options built directly into the kernel with the following modules.

speedstep-centrino
cpufreq_conservative
cpufreq_powersave
cpufreq_userspace     
cpufreq_ondemand
cpufreq_stats         

There are loads of options associated with these that can do frequency scaling automatically at certain cpu loads, what steppings to take, what frequencies are available, etc.

Have a look at this link for more information. [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by galileon on 2007-02-10
that did the trick for me, cheers!

---

### Post by ponx on 2007-04-07
Hmm, I have just installed the emifreq-applet, but I can't find it on my system..!?

How do I run it..?

ponx

---

### Post by galileon on 2007-04-07
right click on the taskbar, select add item to panel and look for CPU Frequency Scaling Monitor

---

### Post by Izkata on 2007-04-17
No, emifreq-applet is named "CpuFreq Monitor", and is at the bottom of the list (under "Utility").

---

