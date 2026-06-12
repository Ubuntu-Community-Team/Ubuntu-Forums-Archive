---
title: "Checking Processor Speed"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-06-25
Hey Guys,

Is there any way that I can check what speed my processor is running at?

It should be a 1.4Ghz but I've a feeling that it's running a lot slower than that.

Thanks.

---

### Post by hartz on 2007-06-25
Enter this command in a terminal:

```
cat /proc/cpuinfo
```

There are probably GUI tools which can do the same ...

---

### Post by Golyadkin on 2007-06-25
Or install [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") but that might be overkill :)

---

### Post by hartz on 2007-06-25
I've done a brief search through Synaptic, looking for the keywords "cpu" and "info" ...
I found the following two programs:

sysinfo
lshw-gtk

Of the two, sysinfo looks a bit nicer.

---

### Post by Catsworth on 2007-06-25
> **hartz said:**
> Enter this command in a terminal:

```
cat /proc/cpuinfo
```

There are probably GUI tools which can do the same ...

Thanks for that, seems to confirm my suspicion that this 1400 processor is only running at 600.

Is there any way that I can unleash the full potential of this mighty beast? </sarcasm>

---

### Post by Seisen on 2007-06-25
Your processor might be on its last legs, which would be why its running at 600 mhz.

---

### Post by Kangaroo on 2007-06-25
Who's the manufacturer of your Processor & Mainboard ? 
Which model ?

---

### Post by mjwhitfield on 2007-06-25
can you post the results of cat /proc/cpuinfo ?

---

### Post by Catsworth on 2007-06-25
```

cat /proc/cpuinfo > /home/Catsworth/desktop/cpuinfo.txt

```

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1400MHz
stepping	: 5
cpu MHz		: 600.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2
bogomips	: 1200.22

```

---

### Post by mjwhitfield on 2007-06-25
ok so this is from a site about a windows program, but interesting none the less.
Source: [http://www.diefer.de/speedswitchxp/index.html](http://www.diefer.de/speedswitchxp/index.html)

```
CPU policy		means ...
Max. performance	keeps the CPU at maximum speed (i.e. a Pentium-M 1.6 GHz runs at 1.6 GHz continously)
Battery optimized	keeps the CPU at the lower speed (i.e. a Pentium-M 1.6 GHz runs at 600 MHz continously)
Max. battery		Keeps the CPU at the lower speed and allows further throttling depending on remaining battery power
Dynamic switching	switches between the lower and maximum speed according to current CPU utilization (i.e. a Pentium-M 1.6GHz switches automatically between 600 MHz and 1.6 GHz)
```

Judging by that, there must be an option somewhere to allow you to change the default CPU profile.

---

### Post by analoog on 2007-06-25
its a mobile processor (for laptop). so it clocks down to safe energy.

---

### Post by mjwhitfield on 2007-06-25
Is there a way under linux to force it to run at 1600 all the time?  Can the OP try running a cpu intensive process and then cat /proc/cpuinfo while it's running to see if the speed goes to 1600?

---

### Post by Catsworth on 2007-06-25
> **analoog said:**
> its a mobile processor (for laptop). so it clocks down to safe energy.

That would make sense, why didn't I think of that?

> **mjwhitfield said:**
> Is there a way under linux to force it to run at 1600 all the time?  Can the OP try running a cpu intensive process and then cat /proc/cpuinfo while it's running to see if the speed goes to 1600?

Yes, he could.....  If I whack it with a load of intensive tasks it does indeed shoot up to closer to the 1400 mark.  So it looks like it's only running at slower speeds when it doesn't need to be running at faster ones.....

Excellent, and very clever.  Thanks guys :D

---

### Post by mjwhitfield on 2007-06-25
woohoo, the first time i've been helpful in a thread.

I'm glad it all works.

---

### Post by Seisen on 2007-06-25
analoog, I didn't know that about mobile processsors thanks for the information.

---

### Post by Catsworth on 2007-06-25
> **mjwhitfield said:**
> woohoo, the first time i've been helpful in a thread.

I'm glad it all works.

I'm sure it won't be the last time.

:D

---

### Post by mjwhitfield on 2007-06-25
is there a way to force them to run at full speed all the time? without causing 100% utilisation?

---

### Post by louistan3 on 2007-06-25
yes, there are ways to run the processor at full speed all the time...

if you try searching for "cpu frequency scaling"

you will find some ways to do this.. 

i believe there are a couple of ways to do this.. 

last time i tried this.. the easiest one i remember was giving super user permissions to the cpu-freq.applet..

but im unsure how to do it.. 

hope this helps :)

---

### Post by anaconda on 2007-06-25
> **mjwhitfield said:**
> is there a way to force them to run at full speed all the time? without causing 100% utilisation?

I think the energy-saving can be turned off from BIOS, but then your laptop would eat the battery much faster..

I would also be interested to know how can I get my laptop to run at full speed when I want it to.  I have a game, that runs half-speed when the processor is in half-speed mode..

Now I just start to watch a movie or do something as heavy to get to the full speed. Then I stop the movie, and start the game.....

---

