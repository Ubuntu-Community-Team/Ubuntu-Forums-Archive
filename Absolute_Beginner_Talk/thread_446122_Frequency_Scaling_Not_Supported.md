---
title: "Frequency Scaling Not Supported"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-16
My Frequency Scaling for my Celeron 800MHz processor is not working with ubuntu, causing my processor to always be at 100% and causes major heat issues. Any way to fix it?

---

### Post by tgm4883 on 2007-05-16
just a thought, but does your processor support frequency scaling?

---

### Post by annda on 2007-05-16
does your cpu just overheat or did you (unuecsessfully) to enable scaling? if so, how?

do you get any output when you try to find the scaling options available?
```
cat /sys/devices/system/cpu/*/cpufreq/scaling_available_governors
```

---

### Post by xthund3rh3adx on 2007-05-16
no, i just noticed that it was always at 100% and began to investigate.

i tried to enter that code and got this:

```

cat: /sys/devices/system/cpu/*/cpufreq/scaling_available_governors: No such file or directory

```

---

### Post by xthund3rh3adx on 2007-05-16
my bad, i forgot to replace the "*" with cpu0, but even as i did the same thing occured

---

### Post by annda on 2007-05-16
i'm not sure the celeron cpu's do frequency scaling, but you can try installing cpufrequtils...

---

### Post by xthund3rh3adx on 2007-05-16
do you have any install links for that please?

sidenote: Celeron must have frequency scaling, because when Windows Me was installed (its first OS), it didnt stay at 100% like it does with Ubuntu

---

### Post by tgm4883 on 2007-05-16
What is at 100%? The frequency or the load?

---

### Post by zek725 on 2007-05-19
Mine also says that **Frequency Scaling Not supported** after *powernowd*. I guess I can remove **powernowd**?

---

### Post by joe.turion64x2 on 2007-05-19
> **zek725 said:**
> Mine also says that **Frequency Scaling Not supported** after *powernowd*. I guess I can remove **powernowd**?
I believe Powernow is a technology for AMD processors only.

---

### Post by joe.turion64x2 on 2007-05-19
Perhaps you can post more information about your processor to find out if it truly supports cpu scaling.

---

### Post by zek725 on 2007-05-19
> **joe.turion64x2 said:**
> I believe Powernow is a technology for AMD processors only.

I believe that answers my question. Thanks.  :) Getting rid of **powernowd**...

---

### Post by zek725 on 2007-05-19
> **joe.turion64x2 said:**
> Perhaps you can post more information about your processor to find out if it truly supports cpu scaling.

**cat /proc/cpuinfo** returns
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 601.412
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1204.27
clflush size    : 32 
```

---

### Post by joe.turion64x2 on 2007-05-19
> **zek725 said:**
> **cat /proc/cpuinfo** returns
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 601.412
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1204.27
clflush size    : 32 
```
Check this [http://tuxmobil.org/Mobile-Guide.db/mobile-guide-p2c1s1-cpu.html](http://tuxmobil.org/Mobile-Guide.db/mobile-guide-p2c1s1-cpu.html)

I think that unless yours is a mobile Pentium III you won't benefit from CPU Scaling.

By the way the technology that would allow your processor to scale its speed is called SpeedStep.

Joe.

---

### Post by zek725 on 2007-05-19
> **joe.turion64x2 said:**
> Check this [http://tuxmobil.org/Mobile-Guide.db/mobile-guide-p2c1s1-cpu.html](http://tuxmobil.org/Mobile-Guide.db/mobile-guide-p2c1s1-cpu.html)

I think that unless yours is a mobile Pentium III you won't benefit from CPU Scaling.

By the way the technology that would allow your processor to scale its speed is called SpeedStep.

Joe.

I guess I really have to get rid of **powernowd.** Mine is not a Mobile CPU. Thanks for the info. This just happened to be after the upgrade to Feisty.

---

### Post by joe.turion64x2 on 2007-05-19
> **zek725 said:**
> I guess I really have to get rid of **powernowd.** Mine is not a Mobile CPU. Thanks for the info. This just happened to be after the upgrade to Feisty.
You're welcome, good luck.

---

### Post by kaede on 2007-05-19
actually my processor is intel pentium 4 mobile. frequency scaling works quite well whem im using powernowd. but when i try to remove it. the scaling not workin anymore. anyone know what kind of power management should i use within pentium 4 mobile? i do encounter some temperature issue with feisty, does it maybe related with frequency scalling ?

---

### Post by kaede on 2007-05-19
my cat /proc/cpuinfo output look like this

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
stepping        : 4
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
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
bogomips        : 2402.67
clflush size    : 64

```

from the line stepping = 4. does that mean my processor supporting for 4 mode of scalling?

---

### Post by kaede on 2007-06-02
any idea? anyone :D

---

### Post by tedrampart on 2007-06-03
looks like your system supports scaling.

I am having this error as well, but I'm running an intel C2D T7200 in my laptop.  I'm not sure what the deal is.  I'd be interested in a result as well.

---

### Post by Lucifiel on 2007-06-03
Install htop.

> sudo apt-get install htop

Then find out what's chewing all that cpu.

---

### Post by tedrampart on 2007-06-03
I sorted my problem out by typing:

```
 sudo modprobe acpi-cpufreq 
```

though it might not work for you, since we have different cpus

---

### Post by Enverex on 2007-06-03
> **joe.turion64x2 said:**
> I believe Powernow is a technology for AMD processors only.

*sighs* Guys, STOP uninstalling powernowd. Yes, PowerNow is an AMD term for their frequency scaling but the Linux program "powernowd" is a deamon for ANY processor that supports frequency scaling. If you uninstall it then you won't have access to any sort of automatic scaling.

---

### Post by cwidger on 2007-06-06
I had this problem on my laptop but found the solution:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Celeron(R) CPU 2.00GHz
stepping        : 7
cpu MHz         : 1000.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
bogomips        : 3991.32
clflush size    : 64


modprobe p4-clockmod
echo "p4-clockmod" >> /etc/modules

That should do it.

---

### Post by revertex on 2007-06-18
> **Enverex said:**
> *sighs* Guys, STOP uninstalling powernowd. Yes, PowerNow is an AMD term for their frequency scaling but the Linux program "powernowd" is a deamon for ANY processor that supports frequency scaling. If you uninstall it then you won't have access to any sort of automatic scaling.

Are you sure?

take a look here,

[http://ubuntuforums.org/showthread.php?t=248867&highlight=cpufreq](http://ubuntuforums.org/showthread.php?t=248867&highlight=cpufreq)

It seems that powernowd is now deprecated, i'm using ondemand kernel module and works as expected.

---

### Post by Enverex on 2007-06-18
I wouldn't recommend that guide, modules like speedstep-centrino don't even exist in the newer Ubuntu kernels (not sure what replaced it, if anything).

---

### Post by jcdx on 2007-06-19
Hi! 

Frequency scaling is supported. The problem is in the new kernels 2.6.20 . I tried a kanotix Live CD with kernel 2.6.18 and the acpi works fine. Also powernow works (scales between 800 or 1600 MHz) on the AMD X2. 

I really think this is a problem of the kernel. May be they fix it in a newer kernel version. I tried to build my own kernel with 2.6.21.4 but the acpi stuff does not work there. 

Regards, 
jcdx

---

### Post by joe.turion64x2 on 2007-06-19
> **jcdx said:**
> Hi! 

Frequency scaling is supported. The problem is in the new kernels 2.6.20 . I tried a kanotix Live CD with kernel 2.6.18 and the acpi works fine. Also powernow works (scales between 800 or 1600 MHz) on the AMD X2. 

I really think this is a problem of the kernel. May be they fix it in a newer kernel version. I tried to build my own kernel with 2.6.21.4 but the acpi stuff does not work there. 

Regards, 
jcdx
Perhaps in Ubuntu it is a problem (I can not check the kernel version installed right now) but not in Fedora. Right now I have:
> Linux localhost.localdomain 2.6.20-1.2952.fc6 #1 SMP Wed May 16 18:59:18 EDT 2007 i686 athlon i386 GNU/Linux

with everything (including CPU scaling) working like a charm.
Joe.

---

### Post by jcdx on 2007-06-19
> **joe.turion64x2 said:**
> Perhaps in Ubuntu it is a problem (I can not check the kernel version installed right now) but not in Fedora. Right now I have:

with everything (including CPU scaling) working like a charm.
Joe.

Ok, good to know. Could you please write (at some time) the kernel version and what powernow version you use? Or if you use cpufreq?

Thanks,
jcdx

---

### Post by joe.turion64x2 on 2007-06-19
> **jcdx said:**
> Ok, good to know. Could you please write (at some time) the kernel version and what powernow version you use? Or if you use cpufreq?

Thanks,
jcdx
Sure, as soon as I boot into Ubuntu again I'll let you know.
Joe.

---

### Post by Seq on 2007-06-19
> **Enverex said:**
> I wouldn't recommend that guide, modules like speedstep-centrino don't even exist in the newer Ubuntu kernels (not sure what replaced it, if anything).

Centrino scaling is handled by the generic acpi module I believe.

Personally, I think Ubuntu should ditch powernowd (although init.d/powernowd.early loads the proper scaling modules, it would have to be replaced) in favour of using gnome-power-manager. g-p-m actually has a graphical option for what in-kernel governor to use. All of this is hidden per default, but the options are available (a gconf key will make them visible in the UI). I do this on feisty and gutsy for both my laptop and desktop.

The only problem with g-p-m would be alternatives for xubuntu/kubuntu/etc.

---

