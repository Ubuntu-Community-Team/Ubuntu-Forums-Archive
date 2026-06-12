---
title: "[SOLVED] Conserve Battery Life"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-24
There are very few things I miss about windows. One of the things I miss is the better battery life. I could easily get 3 1/2 to 4 hours in windows on one battery charge.
Now in ubuntu I only get 2 1/3 maybe 3 if I'm lucky.


Does anybody have any idea why this is?

What are a few things I can do that will increase my battery life (besides the obvious, lower display brightness and disable wireless)

---

### Post by neurostu on 2008-03-24
*

---

### Post by smartboyathome on 2008-03-24
Dude, don't type that, that will erase your entire disk.

Also, try installing powertop, it will tell you which processes to disable to maximize battery life. And don't run Compiz Fusion, it decreases battery life durastically.

---

### Post by heikaman on 2008-03-24
hi...
turn on CPU frequency-scaling if your CPU supports it “frequency-scaling if you don't know is modulating the CPU frequency either on demand, or dynamically according to the CPU load” this will save the battery time.
your CPU supports  frequency-scaling if you find the “cpufreq” directory in  /sys/devices/system/cpu/cpu#/
if its supported, you can find more information on how to change the frequency in any recent kernel documentation, for instance linux-2.6.24/Documentation/cpu-freq/

---

### Post by neurostu on 2008-03-24
Ok well I knew that guy was totally joking about the command that got removed... Oh well sarcasm doesn't carry well through posts.

---

### Post by neurostu on 2008-03-24
So i have the cpufreq dir but how do I turn on CPU Frequency scaling?

---

### Post by p_quarles on 2008-03-24
> **neurostu said:**
> Ok well I knew that guy was totally joking about the command that got removed... Oh well sarcasm doesn't carry well through posts.
Doesn't really matter. As the "malicious commands" announcement states, posting that command gets you instantly banned. The person who posted that is no longer welcome here. Glad you didn't take it seriously, but there are many other new users who would.

---

### Post by neurostu on 2008-03-24
Ok so to turn on CPU Scaling frequency I did the following:

```

sudo dpkg-reconfigure gnome-applets

```
I clicked OK then I selected YES.

Then I added the CPU frequency monitor to my desktop panel, no simply clicking on it will allow me to set the desired frequency by hand!!

---

### Post by neurostu on 2008-03-24
p_quarles, Thanks for the reminder. Sometime I forget how I've learned, and how niave I was when I began. Thanks again.

---

### Post by smartboyathome on 2008-03-24
> **neurostu said:**
> Ok so to turn on CPU Scaling frequency I did the following:

```

sudo dpkg-reconfigure gnome-applets

```
I clicked OK then I selected YES.

Then I added the CPU frequency monitor to my desktop panel, no simply clicking on it will allow me to set the desired frequency by hand!!

Thanks for that, I hadn't known about it. :D

---

### Post by heikaman on 2008-03-24
it's ok but you don't have to set it by hand  if you choose the ondemand or conservative governor "the governor controls the CPU frequency-scaling policy" it will automatically adjust the CPU frequency for you, although in your case setting the frequency statically to the lowest frequency possible would maximize the battery, please read the documentation file I mentioned to know more about governors :)

also you can disable the trackerd daemon, it consumes a lot of CPU cycles “ for a while not all the time” in general only enable daemons that you use.

---

