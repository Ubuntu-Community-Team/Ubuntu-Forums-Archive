---
title: "What are bogomips?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-16
Hi,
In a console;
```
 cat /proc/cpuinfo processor

```
> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.70GHz
stepping        : 9
cpu MHz         : 2693.630
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
**bogomips        : 222.29**


It's a while back I read somewhere that setting bogomips right has its importance. If anybody can help on that, I'd greatly appriciate it!

---

### Post by Najand on 2006-09-16
It is a unit for measurement of CPU speed; It is like to count how many million times per second a processor can do absolutely nothing. Thiis unit is used to calibrate an internal busy-loop when kernel boots.

---

### Post by xyz on 2006-09-16
Thanks [b]  	
Najand[/b]
So I logically guess from what you said that it should be "set" right,right?
How would I go about that? How would I know "good bogomips setting" from "bad bogomips setting" for my:
Toshiba Satellite A 40
2,7G Intel Celeron
512 RAM 80 G HD

---

### Post by Najand on 2006-09-16
I don't know what do you want to "set", because it is just a number and it just depends to your Processor and the kernel you are using; but I can tell you a refernce it may help you... 
[BogoMips mini-Howto]("http://www.clifton.nl/index.html?bogomips.html")

---

### Post by Johan! on 2006-09-16
[http://en.wikipedia.org/wiki/Bogomips](http://en.wikipedia.org/wiki/Bogomips)

---

### Post by xyz on 2006-09-16
I said "set" because I don't really know what other word to use!
I read, a long while back, that this number 'bogomips : 222.29' needs to be "set" right...that,for instance, it shouldn't be 'bogomips: 2887.56'.

I'm sorry I'm not able to explain this right! I just seem to recall that that this number *has to be a precise number* for the computer to run right! And therefore how to calculate what that number should be for my particular box?
I don't know if this is any clearer!! Thanks for the link. I'll check it out.

---

### Post by Najand on 2006-09-16
> **Johan! said:**
> [http://en.wikipedia.org/wiki/Bogomips](http://en.wikipedia.org/wiki/Bogomips)

Thanks... Wikipedia is getting better day by day... Have a look at wikipedia; although it has a similar definition I told you....

---

### Post by xyz on 2006-09-16
I found this so far to start evaluating "bogomips setting":

```
sudo aptitude install sysutils
```
> Miscellaneous small system utilities - dummy package
This package previously incorporated various small utilities:
 * bogomips - Shows the current bogomips rating
 * memtest - From userspace, test system memory for errors,
   aka memtester. This is _not_ memtest86+ or memtest86.
 * procinfo - Displays system information from /proc, this also
   includes lsdev for displaying information about installed hardware
   and socklist for displaying a list of open sockets
 * tofromdos - Converts DOS <-> Unix text files via fromdos/dos2unix /
   todos/unix2dos, aka tofrodos

However, they have been split out into separate packages, so sysutils
is just a dummy package depending on these utilities (except for bogomips
which was dropped) to faciliate upgrades and eventually it will be
completely removed.
But it's a _dummy package..._! Anyone knows of an alternative?

**Why to pay attention to BogoMips**
> [i]#

To see whether it is in the proper range for the particular processor, its clock frequency, and the potentially present cache. Many CPUs are prone to faulty setups of

    *

      memory cache setting (write-back is wrong for BogoMips, often reported lower than 5; write-through is ok)
    *

      turbo-buttons (should be ON)
    *

      BIOS-software emulated fake cache (change it for real cache)
    *

      similar cache and clock related things, sometimes also BIOS-software related

#

To see whether your system is faster than mine. Of course this is completely wrong, unreliable, ill-founded, and utterly useless, but all benchmarks suffer from this same problem. So why not use it? This inherent stupidity has never before stopped people from using benchmarks, has it? :-) [/i]

---

### Post by joeb86 on 2006-09-16
Ok, I think you're leading yourself up the garden path a bit here. Bogomips is really a joke - it isn't a good benchmark, and tells you very little. The kernel just churns it out at bootup to set up some timing thing that makes little difference to anything. You don't need to set it. You don't need to know about it. 

However, it does seem a little low for your processor - mine is 1200, and thats on a 1.2 GHz Pentium M. This is nothing to do with Bogomips, though, it may be to do with your processor setup. If you think your machine is running too slowly, it might be worth your while to run a proper benchmarking tool, and look at what modules you have loading. I imagine there is a howto on benchmarking, which should be your first port of call for program recommendation and comparisons. 

So, bogomips is not a setting, its the result of a test that means very little.

---

### Post by xyz on 2006-09-17
Thanksjoeb86 for having taken the time to tell me I was wasting mine!

---

