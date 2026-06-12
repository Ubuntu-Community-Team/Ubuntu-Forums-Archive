---
title: "CPU temp"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-02-27
has anyone got an idea on how i can watch my cpu's temp, i used to use everest in windows for this, so i went for the lm-sensors in linux but i rahter have a graphic one and not one that i need to load in shell. Is there an option like this hidden somewhere in linux?

---

### Post by Razorback on 2006-02-27
Try conky.  You can do lots of stuff with it.  Good samples are available.  Doesn't take a lot of resources either.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Madpilot on 2006-02-27
You can use ksensors or xsensors to talk to lm-sensors as well. Both live in your notification area, beside the clock, and have customizable displays.

EDIT to added: [https://wiki.ubuntu.com/SensorInstallHowto](https://wiki.ubuntu.com/SensorInstallHowto) has more information

---

### Post by bluevoodoo1 on 2006-02-27
I use conky but there's also gkrellm... [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

---

### Post by xhie on 2006-02-27
ya I use gkerellm, looks all cool hovering on my desktop with the invisible theme

---

### Post by taurus on 2006-02-27
No matter which GUI you plan to use, you still have to install lm-sensors first though...

---

### Post by TrendyDark on 2006-02-27
Thanks for the respones here, I've often wandered how to check out my CPU's temp in Linux. Do all these solutions support AMD64?

---

### Post by taurus on 2006-02-27
Oh yes, it does.  I have temps, fan, and voltages display in gkrellm right now.  :)

---

### Post by TrendyDark on 2006-02-27
Thanks a lot, I think I'll install gkrellm right now then :)

edit: just so you know, gkrellm is available via apt-get:

```
sudo apt-get install gkrellm
```

---

### Post by taurus on 2006-02-27
[QUOTE=TrendyDark]
edit: just so you know, gkrellm is available via apt-get:

```
sudo apt-get install gkrellm
```[/QUOTE]
But of course...

---

### Post by ignorance on 2006-02-28
well i got gkrellm installed but i can't acces the temp of the cpu 

No sensors detected.

and i know i got sensors in there somewhere

---

### Post by pointym5 on 2006-03-01
[QUOTE=ignorance]well i got gkrellm installed but i can't acces the temp of the cpu 

No sensors detected.

and i know i got sensors in there somewhere[/QUOTE]

I had sensors running Hoary on my AMD64 machine, but they're gone with Breezy.  I've run sensors-detect, and it finds some modules to load, but still the "sensors" program reports nothing.

---

### Post by ignorance on 2006-03-01
well i got mine working

just install lm-sensors, run sensors-detect and answer yes to every question.

---

### Post by theturner on 2006-03-01
sensors-applet integrates nicely with your GNOME panel.

---

