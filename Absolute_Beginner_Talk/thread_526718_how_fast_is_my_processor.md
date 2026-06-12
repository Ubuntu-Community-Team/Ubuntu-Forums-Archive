---
title: "how fast is my processor"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-08-15
Is there a command line tool to identify how fast my processor is in my machine?

---

### Post by chriscando on 2007-08-15
```
cat /proc/cpuinfo
```

---

### Post by Bushfire on 2007-08-15
Check the boot messages.

```

$ dmesg | grep hz

```

My clockspeed shows up, but YMMV.

EDIT:
chriscando's way is better. :D

---

### Post by Ripfox on 2007-08-15
processor       : 0
cpu             : 745/755
temperature     : 32-34 C (uncalibrated)
clock           : 400.000000MHz
revision        : 50.2 (pvr 0008 3202)
bogomips        : 49.79
timebase        : 24967326
platform        : PowerMac
machine         : PowerMac2,2
motherboard     : PowerMac2,2 MacRISC2 MacRISC Power Macintosh
detected as     : 66 (iMac FireWire)
pmac flags      : 00000014
L2 cache        : 512K unified

Nice!

Thanks.

---

### Post by isaacj87 on 2007-08-15
> **Bushfire said:**
> Check the boot messages.

```

$ dmesg | grep hz

```

My clockspeed shows up, but YMMV.

EDIT:
chriscando's way is better. :D

What exactly does that command do? I tried it in terminal and it did not produce an output...It doesn't modify anything does it?

---

### Post by Hobo Joe on 2007-08-15
Mine won't show the temperature... :(

But I know my comp supports it becuase I have an app in Windows that shows the CPU and motherboard temperature.

---

### Post by creedog on 2007-08-15
> **isaacj87 said:**
> What exactly does that command do? I tried it in terminal and it did not produce an output...It doesn't modify anything does it?

no it does not......

dmesg is a command that recalls the conents of the messages log durring your boot up. You are then sending the output of that command --which is a bunch of text to the grep command which searchers for the expression gz and then prints every line that has that expression.\


to get a look at the output of dmesg do this

demsg | less


then q to quit

---

### Post by creedog on 2007-08-15
do it like so

```
dmesg | grep -i hz
```

the -i option tells grep to ignore case and return upper and lower case, eventhough you specified lowercase....

---

### Post by logos34 on 2007-08-15
for notebook users there's also a cpu frequency scaling monitor applet for the desktop panel (right-click>add to panel)

---

