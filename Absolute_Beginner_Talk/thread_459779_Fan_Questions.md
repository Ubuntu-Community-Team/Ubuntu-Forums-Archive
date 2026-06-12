---
title: "Fan Questions"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-05-31
I have my fan working almost the way I like it.
It turns on, which is a good thing, but it doesn't turn on soon enough.

My Current Computer Temp:
chris@laptop:~$ acpi -V
     Battery 1: discharging, 66%, rate information unavailable.
     Thermal 1: ok, 46.0 degrees C
  AC Adapter 1: off-line

Is this HOT for a laptop?
Also; I want the fans to start turning on about.. 25 C, and then really running at 35 C.
But my trip points file is blank! :(  (which can't be a good think I think I might have accidentally erased it)

chris@laptop:/proc/acpi/thermal_zone/THR1$ dir
cooling_mode  polling_frequency  state  temperature  trip_points

Whats the default information in trip_points, or a recommended one for laptops?
That hopefully will fix my fan problem.

[ ALSO: Is there a way to turn on my fan manually?[

---

### Post by Kobalt on 2007-05-31
46°C for a laptop CPU isn't hot in my opinion. Mine for example is usually 50-55°C. I do not attempt to modify its fan control, I'd rather use the frequency scalling not to get it too hot. 

If you want your fan to start at 35°C then it will start right after boot, as a laptop CPU is usually at this level of temperature after boot.

---

### Post by chris062689 on 2007-05-31
Hmmm
How can I do freq scaling?
Is it hard?
Does it keep my computer cool? :)

---

### Post by Kobalt on 2007-05-31
You can add a CPU frequency applet to one of your panel easily, and yes, if you set it to 'powersave' for example it will keep your CPU (but not your whole computer) cooler. And it's also very usefull to gain battery life...

Right-click on one of your panel and click 'Add to the panel...' Go to 'Settings and Systems' and double-click the CPU Freq applet. Now that you see it on your panel, open up the Terminal and enter this command line : ```
sudo dpkg-reconfigure gnome-applets
```It will ask you wether you'd like to run the CPU Freq applet with root privileges, answer 'Yes', and you're done.

You'll be able to change your CPU policy from a simple click on this applet.

---

### Post by chris062689 on 2007-05-31
Cool.
That helps kind of.
It really doesn't keep the heat down, but it saves on battery.
Can someone post their original original trip_points file please?
Mine is blank! :(

---

### Post by poppers1957 on 2007-05-31
Don't have that file, but some "cool" advice.  I have use laptops for shows and presentations.  They will burn out rather quickly if used a lot, I found out.  A trick I have done, and it has prolonged the life of my laptop is to get 4 1/2 by 1/2 by 1/2 inch pieces of rubber, use double back tape and secure one on each corner of the laptop bottom.  Much heat is generated on the bottom, and elevating it just a little bit allows the unit to stay somewhat cooler, also improving battery life.  Keep it off your lap, as high as you can, and off carpet, or anything that won't allow good air flow through the bottom.

---

### Post by silkstone on 2007-05-31
The cores on my laptop (T2300 dual core) settle down at around 45C with the fan running very slowly. The fan doesn't speed up unless they reach about 55C, and they've never risen above 60C.

I think the processor is rated at up to 80C and is supposed to have a thermal limiter which comes in at 70C.

---

### Post by chris062689 on 2007-05-31
Ok.
I want to prolong my laptop's life as long as possible

---

### Post by trippinnik on 2007-06-02
What's the processor?  45 C really isn't hot.  But you should check what the temp ratings for your CPU are.  My mobile PIII is supposed to max out at 60 C.  I believe a lot of the newer processors can go a lot higher.

---

### Post by Ripfox on 2007-06-03
I recently bought this: [http://www.provantage.com/targus-pa248u~7TGUA05E.htm](http://www.provantage.com/targus-pa248u~7TGUA05E.htm)

CPU - 39c
HDD - 38c

Almost CONSTANTLY...:D

---

### Post by trippinnik on 2007-06-03
Nice, I wishh mine ran that cool.  Even with a cooling pad (3 fans) it'll get up to 67 C if I am doing anything intensive.  But I just followed these two threads [http://ubuntuforums.org/showthread.php?p=2771646#post2771646](http://ubuntuforums.org/showthread.php?p=2771646#post2771646)
[http://ubuntuforums.org/showthread.php?t=442877&highlight=trip+points](http://ubuntuforums.org/showthread.php?t=442877&highlight=trip+points) and this [http://www.columbia.edu/~ariel/acpi/acpi_howto.html#trip_points](http://www.columbia.edu/~ariel/acpi/acpi_howto.html#trip_points).  Now it'll lower the clock automatically if it gets too hot.  The default had been set to 90 C which is way too hot for this laptop.

---

### Post by chris062689 on 2007-06-03
The only thing is, my trip_points seems to have been deleted.  (which is bad!)
Does anyone have one I could ues?

---

