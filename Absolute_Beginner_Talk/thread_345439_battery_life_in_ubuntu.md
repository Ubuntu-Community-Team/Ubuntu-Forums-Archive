---
title: "battery life in ubuntu"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-24
I normally get about 3 hrs with wifi on on my Dell 700m w/ extended battery in Windows XP. I am loving Ubuntu but I only get around 1.5 hrs of battery life. I was wondering why this is, and how I can get more juice out? How many hrs of battery w/ wifi do you guys get?

---

### Post by Kobalt on 2007-01-24
Hello,

I own a HP dv6120 and I usually get around a couple hours of battery life with wifi activated, could be up to 2h30... 
First you can right click on your battery monitor in your notification area to set up a few things about battery life there... Then, one thing that is very useful is to load the CPU Frequency applet in one of your panel, and set the "Powersave" governor on. You can also reduce the brightness of your screen and disable bluetooth if you have it... 
Any other tips I don't know, but I might be interested in :)

---

### Post by CCBalla10 on 2007-01-24
also when your laptop is running on battery, try dimming the screen a little.  Gave me another 10-15 minutes....

---

### Post by Henry Rayker on 2007-01-24
try doing a ```
gksudo gedit /etc/default/acpi-support
``` and change the ENABLE_LAPTOP_MODE=false line to ENABLE_LAPTOP_MODE=true

then run ```
sudo etc/init.d/acpi-support reload
```

Give it about 15 seconds and it should kick in. You can do a ```
cat /proc/sys/vm/laptop-mode
``` to check (0 means it is not in laptop mode, a non-zero means that it is in laptop mode)

---

### Post by McLogic on 2007-01-26
I have the 700m and got 5 hours with a new batt (~2 with a 2-year-old batt). I don't notice a lot of diff between windows/Ubuntu batt life. I have the CPU scaling set to keep the Mhz down to 600 most of the time. This is using the powernowd deamon.

Get directions from this file:
/etc/init.d/powernowd

And put your config in this file:
/etc/default/powernowd

I have this in the file. It holds the CPU freq low and changes it 5 times a second.
OPTIONS="-m 2 -p 200"

See what the options mean in Terminal:
$ man powernowd

---

