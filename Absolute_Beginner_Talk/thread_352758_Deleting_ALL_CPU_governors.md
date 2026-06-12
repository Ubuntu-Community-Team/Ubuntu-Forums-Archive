---
title: "Deleting ALL CPU governors"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by thecow on 2007-02-03
I figured out how to change my cpu speed around, but now it keeps reverting back to 2 ghz from 800 MHZ whenever it percieves it needs to.  I cant handle not being in control of my cpu speed at all times, and so was wondering how to get rid of all of the governors controlling my cpu

---

### Post by shareMenaPeace on 2007-02-03
Do you mean processes?

Checkout System -> Administration -> System Monitor

---

### Post by thecow on 2007-02-03
So I have the cpu frequency app in my top bar.  When I click on it, I can change the cpu speed.  So say I want to go from 2 GHZ to 1.33 GHZ or maybe to 800MHZ, it will change but then go back to 2GHZ when ubuntu thinks it needs more cpu power.  I want to disable this and have it always stay at the cpu speed I set it to.

---

### Post by shareMenaPeace on 2007-02-03
Checkout System -> Preferences -> Power Management 

Well i don't know a tool todo this but i guess linux/ubuntu manage this allready.

---

### Post by shareMenaPeace on 2007-02-03
Checkout this searchc for cpu 

[http://ubuntuforums.org/showthread.php?t=295751](http://ubuntuforums.org/showthread.php?t=295751)

And check this search for cpu + speed

[http://ubuntuforums.org/search.php?searchid=13921215](http://ubuntuforums.org/search.php?searchid=13921215)

---

### Post by kinematic on 2007-02-03
> **thecow said:**
> So I have the cpu frequency app in my top bar.  When I click on it, I can change the cpu speed.  So say I want to go from 2 GHZ to 1.33 GHZ or maybe to 800MHZ, it will change but then go back to 2GHZ when ubuntu thinks it needs more cpu power.  I want to disable this and have it always stay at the cpu speed I set it to.

maybe i'm missing something here but isn't that the point of the powernow daemon.....increasing the speed when the system needs it and lowering it when the cpu is idle :confused:

---

### Post by chalex on 2007-02-03
Which cpu do you have?  Maybe you could paste the output of `cat /proc/cpuinfo`

---

### Post by thecow on 2007-02-03
~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 8
cpu MHz         : 1330.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 2663.26

That is the output.  I dont know about any daemon, I just want to be able to set my cpu at a certain frequency and have it stay there.  Like the Centrino Hardware Control for Windows, seems like there should be an easy way to do it.

---

### Post by irish_flu on 2007-02-03
Is your BIOS doing anything with it, maybe?  It seems to me (might be remembering incorrectly, though) that some BIOS do that sort of management....

---

### Post by kinematic on 2007-02-03
> **thecow said:**
> I dont know about any daemon, I just want to be able to set my cpu at a certain frequency and have it stay there.  Like the Centrino Hardware Control for Windows, seems like there should be an easy way to do it.

the powernow daemon is the daemon that regulates the speed and i don't know of a way on linux to the set the speed at a level you want and have it stay there.
(and personally i don't see the point....the speed will be raised or lowered according to the workload by powernow)

---

### Post by kinematic on 2007-02-03
you could try googling for it ;)

---

### Post by thecow on 2007-02-03
Eh ive tried looking on google.  The point is that I should have control over my cpu, eh maybe ubuntu is just not customizable enough.  I guess Ill put my computer engineering degree to use, and hit up gentoo.

---

### Post by kinematic on 2007-02-03
scaling works the same on gentoo....wich i know by experience.

---

### Post by thecow on 2007-02-03
Well considering the point of gentoo is for customization at every level, Im sure Ill figure it out.  Thanks though

---

