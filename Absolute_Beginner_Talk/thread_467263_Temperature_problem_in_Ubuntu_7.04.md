---
title: "Temperature problem in Ubuntu 7.04"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-06-07
I've been checking around, but have note found a solution yet to my problem. I have a Compaq Evo N610c laptop with Ubuntu 7.04, but the CPU temp is through the roof from boot! I have GNOME sensor-applet installed, and it shows a temp of 70 to 75 degrees Celsius, and that is going to kill my CPU in a short while I think.

Some info:

laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
stepping        : 7
cpu MHz         : 1200.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
bogomips        : 2394.75
clflush size    : 64

Anyone?

---

### Post by Hobo Joe on 2007-06-07
This all I've found so far:

> I had problems with my Dell 700m running what seemed to be hot (50-55 degrees C) when idling, and going closer to 60C when running stuff . This temp was derived from both gkrellm and emifreq-applet.

Using the rcconf tool, I found that both the acpid and apmd power management daemons were running. This is probably by design to ensure compatibility.

Disabling acpid and rebooting didn't make an impact on temperature (though it did disable battery detection)

Disabling apmd and rebooting made a LOT of difference - I now run at 45-50C when doing 'light' activity (IM, email, web-surfing), depending on how my processor speed is cycled at the time. My fans are also coming on a lot more consistently as well.

I'd recommend downloading rcconf via synaptic and using the tool to disable whichever power management daemon you're not using (most likely apmd) and seeing if that helps with temp issues.
Ok i installed rccconf tool and im not sure how to use it or start it. maybe u can give me a small how-to? would be great :D

Here's the link: [http://ubuntuforums.org/archive/index.php/t-32422.html](http://ubuntuforums.org/archive/index.php/t-32422.html)

---

### Post by NeoLithium on 2007-06-07
Also check out [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features) 
as well.  Frequency scaling helps keep the temperature down as well.

---

### Post by lodravah on 2007-06-07
Hmm. I installed rcconf, but can't find any of the powermanagment-deamons.. The tool listed "apport", "gdm", hplip and usplash.. Have never used this tool before. You?

---

### Post by Hobo Joe on 2007-06-07
Can't say I have, but hey! There's a first time for everything!

---

### Post by lodravah on 2007-06-07
When looking through /var/log I see this message: "apm overridden by acpi." I also see a message at boot but I'm unable to read it properly, but it says something about IRQ and ACPI, I'll try to isolate it. This helps anyone?

---

### Post by lodravah on 2007-06-07
The boot message reads "11.58365 ACPI: Resource is  not an IRQ entry" and also the same message with different numbers (10), which I think describes antoher IRQ. helps?

---

### Post by hasimir44 on 2007-06-10
> Frequency scaling helps keep the temperature down as well.

is this like underclocking? can someone give a brief explanation (the link is only howto, no explanation)? 

thanks

---

### Post by Rocket2DMn on 2007-06-10
I think he might be referring to the processor speedstepping where the processor actually drops its clock speed when it doesn't need to run fast.  This saves on power.  A lot of processors used in mobile computers have this feature.

---

### Post by huygens on 2007-06-12
> **hasimir44 said:**
> is this like underclocking? can someone give a brief explanation (the link is only howto, no explanation)?

It is kind of underclocking. Most mobile processors since a few generation are using such technics. For example, my Centrino 1.6GHz runs most of the time at 600MHz, and when the load rise, the frequency rises too up to 1.6GHz.
If you want to digg a bit in the arcane of CPU throttling, I would recommend this article: [http://www.berthon.eu/wiki/foss:wikishelf:gpm:hacking](http://www.berthon.eu/wiki/foss:wikishelf:gpm:hacking)
It has a few pointers to other resources as well for further explanation.

And I confirm the recommendation of NeoLithium, frequency scaling (or CPU throttling) might help improve your temperature problem, of course, this is possible if your processor supports it.
There is a how-to for Debian OS, but it is also applicable to Ubuntu: [http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

---

### Post by CrispyFried on 2007-06-12
the pentium 4 m is rated to 100 C. while I dont really like 70-75 either it is rated for it. my celeron m (also rated to 100 C) runs around 70  C pretty much at anything but idle.

---

### Post by huygens on 2007-06-13
Just another idea. Before my previous motherboard died, I had an AMD Athlon XP 1600 with the default fan from AMD. The temperature was about 60°C and up to 75°C on load (and in summer).
As the fan was really noisy, I have replaced it by a newer one. The noise was much reduced :-) and best of all the temperature too! It was about 30°C with up to 45-50°C on full load (the fan was then running faster too and making a bit more noise, but still less than the original one).
So if you cannot make your CPU cool down by software, you could perhaps change your fan. It costed only around 10 €... So I guess the investment is interesting.

---

