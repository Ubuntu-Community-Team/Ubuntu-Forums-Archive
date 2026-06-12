---
title: "Find Out CPU and RAM capacity, also SWAP"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Requiem on 2006-09-10
Dumb question first, how can i find my cpu and ram capacity from the gui? or bash?

Second, how much swap should I have?

---

### Post by bulldog on 2006-09-10
Type 'top' in a terminal and you get some info.

Basicly is the rule that your swap must be twice the installed RAM.

But if you have 1GB of RAM then you can safely make a swap partition of 1GB.

Hope this is what your'e looking for anyway.

Normally someone knows what kind of CPU and installed RAM he has.

---

### Post by Requiem on 2006-09-10
Normally someone knows what kind of CPU and installed RAM he has.

Oh yes, that's true and I knew it but i've got several old machines and often forget their specs. Anyway, isn't there a gui form to know this? I mean for the real newbies?

//After a quick inspection

top reports cpu usage but not the CPU's full capacity, it did report total ram and saw in kb

It matches Gnome system monitor's report on ram and swap, I MiB.
(Ok sorry I missed it).

I still can't find cpu capacity, went to device manager and found my cpu, labeled as CPU0 (that's 1zero', anyway this has got only one cpu the number is not important).

Device manager doesn't tell me anything about the cpu... I'm still loking around for this.

---

### Post by bulldog on 2006-09-10
I'm sure there is but I don't have it nor know the name of such an app.

Sorry,can't help you here.

---

### Post by Najand on 2006-09-10
Try:
```
cat /proc/cpuinfo
```
to get some information about your cpu..

---

### Post by Marsolin on 2006-09-10
What do you mean by CPU capacity?  From a utilization standpoint, it will always be 100%, regardless of the number of CPU's or cores.

In Kubuntu you can load KInfoCenter from the System menu.  The Processor item will display the same info you would get from typing "cat /proc/cpuinfo" in the terminal.

Likewise the Memory selection in KInfoCenter would give you everything you need to know about the amount and usage of memory in your system.

I don't know what the equivalent areas are for Gnome.

---

