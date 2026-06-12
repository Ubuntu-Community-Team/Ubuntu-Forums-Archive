---
title: "32 Bit System - 8GB Memory ~ What's Going On?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by rlelek on 2008-02-19
When my company bought a server, It came with 8 Processors, and 8 GB of RAM.
I just don't understand why they gave it 8GB when a 32 bit system only recognizes 3.5-4.0GB natively

Can anyone explain this to me?

I am 99% certain this is NOT a 64 bit system, the processors are Intel Xeons.


Thanks,
Ryan

---

### Post by timbounceback on 2008-02-19
well, for a start i would have a look at /proc/cpuinfo and see if there's anything interesting there

---

### Post by rlelek on 2008-02-19
What about memory mirroring

How would that have an effect on this system?

---

### Post by Origin415 on 2008-02-19
Xeons are 64-bit, at least any xeons made in the past couple years, since 2004.

You can pretty much bet on any currently produced processor being 64-bit.

---

### Post by rlelek on 2008-02-19
Ok, I just got a request for the output of

```
cat /proc/cpuinfo
```

and I'll post with updates!
The server was made around 2004, our company can't afford a brand new one, right now anyway.


Thanks everyone!

---

### Post by tribaal on 2008-02-19
Maybe have a quick look at the link in my sig - a part of the article explains the "mysterious" memory limit of ~4Gb.
I suppose you installed the regular Ubuntu distribution (not the server-specific one?), as I recall the 32bits kernel doesn't have large memory support.

Xeons are absolutely 64bits-capable processors. I highly suggest you install a 64bits version of Ubuntu since the only downside (no java plugin for firefox) will most certainly not matter on a server :)

And you get a slightly faster crunsher out of it too ;)

Hope this helps :)

- Trib'

---

### Post by rlelek on 2008-02-19
Output of "cat /proc/cpuinfo":

ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5398.53
clflush size : 64

processor : 1
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.42
clflush size : 64

processor : 2
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 1
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.47
clflush size : 64

processor : 3
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 1
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.48
clflush size : 64

processor : 4
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 2
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.46
clflush size : 64

processor : 5
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 2
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.47
clflush size : 64

processor : 6
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 3
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.42
clflush size : 64

processor : 7
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping : 6
cpu MHz : 2694.662
cache size : 2048 KB
physical id : 3
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips : 5389.51
clflush size : 64

---

### Post by rlelek on 2008-02-19
> **tribaal said:**
> Maybe have a quick look at the link in my sig - a part of the article explains the "mysterious" memory limit of ~4Gb.
I suppose you installed the regular Ubuntu distribution (not the server-specific one?), as I recall the 32bits kernel doesn't have large memory support.

Xeons are absolutely 64bits-capable processors. I highly suggest you install a 64bits version of Ubuntu since the only downside (no java plugin for firefox) will most certainly not matter on a server :)

And you get a slightly faster crunsher out of it too ;)

Hope this helps :)

- Trib'

I Never Knew That!!!

I thought Intels were x86 unless stated otherwise.
Thanks for that, and all your help everyone!!

---

### Post by tribaal on 2008-02-19
My bad, judging from your cpuinfo, your Xeons are *not* 64bits capable (the flag for x64 is "lm")

:(

Did you install the ubuntu server edition? I think the x86 server kernel has the high memory flag compiled in...

If in doubt, just post the output of "uname -r"

- Trib'

---

### Post by Origin415 on 2008-02-19
Well your instinct was right, those are 32-bit processors.

---

### Post by rlelek on 2008-02-19
"uname -r" yields 

"2.6.20-12-generic"


And no, I have only been running a live cd due to the HDs not arriving yet.

So since I turned memory mirroring on, my machine is faster, but what does it mean other than that? I figure if i mirrored half, I would still have the max of 4GB while putting the other 4GB to some use. Am I correct? I really have no idea about all of this, but I just use some good old common sense.

Thanks

---

### Post by tribaal on 2008-02-19
Well the easy fix is to install the server edition of ubuntu - it has highmem built-in.

However the default install is a text-only operating system (only command-line, but it's quite easy to install a desktop on top of that if you feel like it), and it can be a little disorienting if you're a newcomer to the GNU/linux world...

I guess you can also install the server kernel on a desktop install, either way.

---

### Post by rlelek on 2008-02-19
Alright, I'm not so much a newcomer, I use linux off and on and have been for the past 2 or so years. I read a few books, but it is much harder to implement them. Also, they never cover anything like this. So i'll grab my phrasebook and step right on in to the full-time Linux world!

(I'll do a server install when i get the disks in)

Still, what does memory mirroring do? Is it like RAID 1 for memory?

---

### Post by tribaal on 2008-02-19
> 
Still, what does memory mirroring do? Is it like RAID 1 for memory?

That would be exactly it according to [this pdf]("http://64.233.183.104/search?q=cache:ffvNlxlklswJ:www.dell.com/downloads/global/power/ps3q05-20050176-Patel-OE.pdf+memory+mirroring&hl=en&ct=clnk&cd=1&client=firefox-a").

I would personally turn this option off to address the full 8Gb of memory (since a bad memory chip is somewhat infrequent, and the servers never have enough RAM ;) )
Running a memtest on a production machine before putting it online is however always a good idea ;)

Hope this helped :)

- Trib'

---

