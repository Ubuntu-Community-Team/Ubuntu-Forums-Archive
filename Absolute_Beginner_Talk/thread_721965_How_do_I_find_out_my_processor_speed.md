---
title: "How do I find out my processor speed?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-11
Hi,

I know my Dell Laptop will scale in Windows XP when on battery.  I have also been able to use CPUID to check my processor speed.

Is there something similar to that in Ubuntu?  

I want to see if my processor runs at different speeds when plugged in or on battery.  

Thanks,
Rich

---

### Post by smo0th on 2008-03-11
use 
cat /proc/cpuinfo | grep "MHz"

and speed will be displayed for as many cores as you have.

---

### Post by RichTJ99 on 2008-03-11
rich@rich-laptop:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz         : 1000.000
cpu MHz         : 1000.000
rich@rich-laptop:~$ 


Does that mean my 2.0ghz C2D processor is running at 1000 mhz?  

This is when plugged in, it is the same on battery.

---

### Post by Matt Yun on 2008-03-11
Ubuntu provides an taskbar applet to display the current CPU frequency.  

Right-click on your taskbar, then select **Add to Panel**.  Scroll down to **System & Hardware** then select **CPU Frequency Scaling Monitor**.  You now have a little widget that displays the current frequency.

---

### Post by RichTJ99 on 2008-03-11
Thanks, that was helpful. I like having that widget so I can watch the processor speeds.

 I launched a number of things at the same time & got:

rich@rich-laptop:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz         : 2000.000
cpu MHz         : 2000.000
rich@rich-laptop:~$ 


So, I guess its stuck at half speed.  Is there a way to force this Laptop C2D processor to run at higher speeds?

---

### Post by uberlube on 2008-03-11
If you like that, you may also be interested in conky. It's great.

---

### Post by jordanmthomas on 2008-03-11
> **RichTJ99 said:**
> Thanks, that was helpful. I like having that widget so I can watch the processor speeds.

 I launched a number of things at the same time & got:

rich@rich-laptop:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz         : 2000.000
cpu MHz         : 2000.000
rich@rich-laptop:~$ 


So, I guess its stuck at half speed.  Is there a way to force this Laptop C2D processor to run at higher speeds?

The reason it's "stuck at half speed" is to save power.  There's no need to run your cores at 2 GHz when that much power isn't needed.  When CPU usage increases, the speed is kicked up a notch or two.  If you really want to have your CPU going at full speed all the time, you can set your processor governor to performance mode rather than the default (probably ondemand)
```
cpufreq-selector -g performance
```

Also, you can use that applet you've added to your panel to change the governor (speed settings) your processor is using.
```
sudo dpkg-reconfigure gnome-applets
``` and answer yes to the question it asks.  Then, re-add the applet to your panel (or log out / in) and you will have options to enable controlling the speed of your CPU.

EDIT:
After reading your original post it seems you already understand scaling, so you can ignore my first paragraph.

---

### Post by Cha1n5aW on 2008-03-11
I'm not sure how to control the processor/cpu throttling in ubuntu, I'm sure it's possible, just no clue how myself.  My CPU seems to throttle properly on its own, not often does it actually run at full speed.

- Shawn

---

### Post by oskar2000 on 2008-03-11
I wouldn't force it to run higher. If it needs more power it will scale up immediately . You'll just waste electricity if you force it to run higher all the time.

---

### Post by smanandhar on 2008-03-11
$>cat /proc/cpuinfo | grep "cpu MHz"

This will show your CPU speed in MHz

---

