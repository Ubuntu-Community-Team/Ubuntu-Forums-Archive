---
title: "Ubuntu 7.04 - the Feisty Fawn  very slow"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-06-25
my free memory is as follows.

desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        483424     424184      59240          0      12108     234960
-/+ buffers/cache:     177116     306308
Swap:       666656          0     666656

 pl. advise how to increase the speed.   ubuntu is very slow.   thanks

---

### Post by anaconda on 2007-06-25
memory doesn't seem to be your problem, since you have plenty of free memory. 59M+234M=293M free + 666M swap

If your processor is slow you might want to turn the desktop effects off, or change to a lighter window manager. eg. xfce, or fluxbox (=lightest), and run lighter programs.

---

### Post by drpas2k on 2007-06-25
This is my processor particulars.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 1
model name      : Intel(R) Pentium(R) 4 CPU 1.50GHz
stepping        : 2
cpu MHz         : 1500.151
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
bogomips        : 3002.84
clflush size    : 64

pl. advise. thanks

---

### Post by Seisen on 2007-06-25
I would recommend using Xubuntu instead of Ubuntu because its a litle easier on the processor.

---

### Post by drpas2k on 2007-06-25
How to uninstall ubuntu and to install xubuntu. thanks

---

### Post by Seisen on 2007-06-25
Here is the command to install Xubuntu 

```
sudo aptitude install xubuntu-desktop
```

After that finishes reboot into Xubuntu and do this

```
sudo aptitude remove ubuntu-desktop
```

---

### Post by anaconda on 2007-06-25
hmm.. 1,5GHz should be enough to run ubuntu! How slow is it? what programs do you run when it is slow? Do you run some really heavy programs?


but ofcourse xubuntu will be lot faster.

---

### Post by drpas2k on 2007-06-25
Mine is dual boot system. 

I have upgraded ubuntu 7.4 to low latency and then I have added ubuntu studio.

 I am new to linux. .I am unable to add desktop effects and I do not play any games. 

Simply I am browsing. I have got so many sound & video programs due to ubuntu studio. I donot know how to

 use them also .

shoul;d I uninstall ubuntu studio.will it help.  pl advise. thanks

---

### Post by anaconda on 2007-06-25
I dont think having ubuntu studio installed will slow it down. If it is running then it propably slows other programs down., not when it isn't.

One more idea. Have you got an nvidia display card? if you have and you havn't installed the restricted drivers, then the graphics will be quite slow. (the machine isn't slow, but eg. scrolling text file with the whellmouse can be jerky etc..)

If so install the restricted drivers..

---

