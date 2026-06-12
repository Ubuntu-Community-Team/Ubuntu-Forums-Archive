---
title: "How do I get a system profile (not a device manager)?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-24
Hi all,

Is there a utility in Ubuntu similar to Mac's system profiler that gives a breakdown of system status by specific sub-system, but all in one place? What I mean is, is there somewhere I can find out how many cycles my battery has on it, and then in the same utility check my network settings or my bluetooth device status for example?

I realize that Linux isn't OS X, and I don't want it to be, but is there a "one-stop shopping" location for system profile info besides the device manager which shows which devices are present, but not the active status of the devices?

Thanks,

Kent

---

### Post by TFX360 on 2006-08-24
Carbon Fish,


If there is I've never heard of it, but it sounds a tad like webmin. Google that! Or click [here.]("http://www.webmin.com/")

Kind regards,


TFX

---

### Post by Carbonfish on 2006-08-24
Thanks TFX,

I looked at webmin and think it might be a bit more than I'm looking for. I am looking more for a system specific utility (unless I didn't look carefully enough at the basic webmin info.)

I'll keep looking around.

Thanks again,

Kent

---

### Post by Frank Golden on 2006-08-24
> **Carbonfish said:**
> Hi all,

Is there a utility in Ubuntu similar to Mac's system profiler that gives a breakdown of system status by specific sub-system, but all in one place? What I mean is, is there somewhere I can find out how many cycles my battery has on it, and then in the same utility check my network settings or my bluetooth device status for example?

I realize that Linux isn't OS X, and I don't want it to be, but is there a "one-stop shopping" location for system profile info besides the device manager which shows which devices are present, but not the active status of the devices?

Thanks,

Kent
SysInfo, Install from Synaptic. Search from within Synaptic for it.

---

### Post by TFX360 on 2006-08-24
Hmm, I'll try that to, for phun! Thanks Frank Golden!

---

### Post by Carbonfish on 2006-08-24
> **TFX360 said:**
> Hmm, I'll try that too, for phun! Thanks Frank Golden!

Yeah, what he said.  ;) 

Kent

---

### Post by tzulberti on 2006-08-24
Maybe you should trie gkrellm

---

### Post by Frank Golden on 2006-08-25
> **tzulberti said:**
> Maybe you should trie gkrellm
Interesting. Kinda like System Monitor on steroids. Check out this screen shot of my desk top.

[http://i30.photobucket.com/albums/c338/fjgold/Screenshot-4.png](http://i30.photobucket.com/albums/c338/fjgold/Screenshot-4.png)

If you notice at the top right in the panel are 2 freq monitor icons,
a system monitor icon and a temperature icon. The 2 frequency icons
tell me at a glance in real time what each CPU frequency is.
I have a Core Duo processor. Powernowd dynamically controls each processor
according to demand. The system monitor icon tells me what percentage of processor usage is and when clicked on tells me what processes are running etc. The temperature icon tells my what my processor temperatures are.
It uses ACPI which this laptop supports to sense temp.
The frequency icons and the system monitor are available by right clicking
a blank area of the panel and choosing add to panel. You need to place two
of the frequency icons to the panel if you have a dual core proc and have
the 686smp kernel installed, if you want to monitor both your procs.
If setup for dual processors you can right click each icon and from properties choose processor 0 or 1. The temp monitor you have to install
using Synaptic. Do a search in Synaptic for computertemp and install.
It will be in menu when you right click a blank space in your panel
and choose add to panel. You can configure it by right clicking icon
and choosing preferences.
Not an all in one solution but works well for me.

---

### Post by Carbonfish on 2006-08-25
Pretty cool, but I don't suppose that it might also tell me how many mAh my battery has left (used), or give me it's cycle count?


The processor temp. and usage *are* really useful though.

Cool.

KC

---

### Post by Frank Golden on 2006-08-25
> **Carbonfish said:**
> Pretty cool, but I don't suppose that it might also tell me how many mAh my battery has left (used), or give me it's cycle count?


The processor temp. and usage *are* really useful though.

Cool.

KC
You know I haven't seen any thing with that level of detail.
Power management has a option to place an icon in system tray (notification area) to monitor battery status. It doesn't give the detail you are looking for.

---

### Post by Carbonfish on 2006-08-25
> **Frank Golden said:**
>  It doesn't give the detail you are looking for.


Yeah, well I guess that I'm just a bit spoiled. Thanks for the suggestions and for looking around though.  :mrgreen: 

Kent

---

