---
title: "View CPU temp"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-17
ive recently overclocked my processor (dual core)
and wanna keep an eye on the temperature.

can you reccomend somthing?

---

### Post by Nikron on 2007-06-17
I use conky for that.  If you have acpi enabled, you should be able to see the temp at /proc/acpi/thermal_zone/THM/state

---

### Post by w4ett on 2007-06-17
there is a program in the repositories: Sensors to detect m/b and cpu temps....just:

sudo apt-get install lm-sensors

---

### Post by skymera on 2007-06-17
i tried lm-sensors....funnily enough, detected sod all.

---

### Post by w4ett on 2007-06-17
Some M/B's don't work with it, but i'ts worth a try....8)

---

### Post by 5-HT on 2007-06-17
> **skymera said:**
> i tried lm-sensors....funnily enough, detected sod all.
A kernel patch is available that provides temperature monitoring support for Intel Core/Core2/Solo processors for lm-sensors that monitors each core.

It's currently in -mm and may make it into 2.6.22 mainline. Arch currently uses the coretemp patch by default in their kernels and it's working great for me. The benefit of this patch over monitoring CPU temp via acpi is the multiple core support. If you want to give it a try, you'll need to patch your kernel.

[http://lkml.org/lkml/2007/3/10/115](http://lkml.org/lkml/2007/3/10/115)
[http://lkml.org/lkml/2007/5/2/544](http://lkml.org/lkml/2007/5/2/544)

---

### Post by skymera on 2007-06-17
i have Core 2

---

### Post by skymera on 2007-06-17
LM snesors dosent detect and those links you put, i dont understand.
sorry

---

### Post by 5-HT on 2007-06-17
> **skymera said:**
> i have Core 2

AFAIK, you'll need the coretemp module to monitor the CPU core temps with lm-sensors then. Alternatively, you can monitor from acpi (not individual cores though) or wait for 2.6.22 / use the current rc.

> **skymera said:**
> LM snesors dosent detect and those links you put, i dont understand.
sorry

lm-sensors doesn't detect your temps because you need to first patch your kernel for coretemp support, which will provide a module to allow lm-sensors to detect your CPU temps. If you are not comfortable with patching and compiling kernels, you can wait for 2.6.22 which may have coretemp support enabled by default. Alternatively you can try submitting a feature request for coretemp support. However, Ubuntu may already provide coretemp support (don't have it installed currently, will put it back on soon). You can try to load the coretemp module to see if you may already have the module.
```
sudo modprobe coretemp 
```
If you don't get an error, you can then just configure lm-sensors (please refer to lm-sensors documentation to see how to do that).
If you do get an error, then your current kernel does not have coretemp support.

Hope that helps

cheers,

---

### Post by skymera on 2007-06-17
i dont think im after each core.

im after a small utility to detect the processor temp.
i think theres surprisingly little :(

---

### Post by 5-HT on 2007-06-17
> **skymera said:**
> i dont think im after each core.

im after a small utility to detect the processor temp.
i think theres surprisingly little :(

You can just monitor from acpi then as Nikron suggested:
```
acpi -t
```or

```
cat /proc/acpi/thermal_zone/THM/temperature
```*the actual path on your system may be a little different (THM may be called something else)

---

### Post by skymera on 2007-06-17
not supported.
o well.
i guess i have to wait.

thanks anyway guys!!!

---

### Post by 5-HT on 2007-06-17
Sorry 'bout your problem. Can anyone else get a temp from acpi on a Core2 Duo?

---

### Post by skymera on 2007-06-17
i found this
[http://gnomefiles.org/app.php/BlueCombo](http://gnomefiles.org/app.php/BlueCombo)

cant get it to download :(

---

### Post by skymera on 2007-06-17
I FOUND IT!

```
 sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp 
```

im sitting nicely overcloked at cpu1: 44 degrees and cpu2: 40 degrees :D

---

### Post by thesoothsayer on 2007-06-20
> **5-HT said:**
> Sorry 'bout your problem. Can anyone else get a temp from acpi on a Core2 Duo?

I can. Running feisty fawn.

Linux kit-laptop-0 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

---

### Post by e30ernest on 2007-06-20
That can't be right?!?  I'm running at 100C on both processors?!?  I have to check more into this.

---

