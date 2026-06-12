---
title: "[SOLVED] cpu temp and fan ?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2008-02-27
This is weird, was just reading a post on cpu temps and for comparison I brought up my gkrellm for comparison, it read 104F but the other post was giving Celsius numbers so I switched it over and when I hit apply my fan shut off? It's always spinning, switching back and forth turns it on and off? Why would changing a temp. readout from Fahrenheit to Celsius stop the fan?

---

### Post by herbster on 2008-02-27
So you have lm-sensors installed, right? What's the output of "sensors" ?

---

### Post by chris.a.barker on 2008-02-27
It must be gobblins inside the terminal :)

---

### Post by zabien1970 on 2008-02-27
Oops, a little more searching and I discovered that gkrellm not only monitors the temps it also controls the fan speeds, I never realized the settings were in Celsius so being set at 40C for low and 45C for high and displaying temp in Fahrenheit averaging over 100 thew were always on high,

---

