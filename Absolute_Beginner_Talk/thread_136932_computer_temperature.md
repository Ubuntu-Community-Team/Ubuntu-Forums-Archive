---
title: "computer temperature"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-27
Hey, I was wondering if any of you could tell me how I could find out how hot my computer is running.

I appreciate it!

Thanks,
Donald

---

### Post by xhie on 2006-02-27
I use gkrellm, it sits happily on my desktop and prints out nice system monitor graphs. I'm sure theres some easier way though that I just cant think of.

---

### Post by towsonu2003 on 2006-02-27
check under /proc

in terminal, use cd to navigate (as in cd /proc) and cat to look into files (as in cat /proc/cpuinfo). The file you are looking for will be labeled st like temp thp thermal or something. this is how it is in my computer at least...

---

### Post by Sutekh on 2006-02-27
I chucked a **Hardware Sensor Applet** on a panel.  You can get it by right-clicking a panel and **Add to Panel**

You'll have to
```
sudo apt-get install lm-sensors
```
then```
sensors-detect
```
To get it running.

---

### Post by Madpilot on 2006-02-27
[https://wiki.ubuntu.com/SensorInstallHowto](https://wiki.ubuntu.com/SensorInstallHowto) will take you through it, although the script mentioned there isn't really needed - as Sutekh said, just running "sensors-detect" is good enough.

To read the sensors, you'll need a desktop applet - ksensors, xsensors or something else. I happen to use ksensors, even though I run Ubuntu w/ Gnome.

---

