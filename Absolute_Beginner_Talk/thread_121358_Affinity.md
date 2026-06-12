---
title: "Affinity"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2006-01-25
When i get my new pc in a couple of days it will be a duel core amd and in XP i heard that there is a feature called affinity in the task manager to assign tasks to the second core, is there such a feature in ubuntu? if so where is it?

cheers

---

### Post by d1337 on 2006-01-25
I think, **but do not know for sure**, that you will want to use an SMP kernel for this machine.  This kernel is available from synaptic and is probably linux-image-2.6.12-10-686-smp (likely the most stable release).  As far as assigning tasks to the second core, I think it takes care of it for you.  After your stock install, you'll want to add the smp kernel and make sure that you boot from it.  **If all goes well**, you can delete the stock kernel (2.6.12-10-386) after you are running from the smp kernel.  From what I know (which isn't much), smp works on both dual processors and dual core processors.  I run an smp kernel on my server/space heater which is a 2 X Pentium III 1.5gigahertz.
Now, since I don't know how this works on dual core, I'd like to ask a favor (unless someone beats you to it).  I'd like to see the output of
```
cat /proc/cpuinfo
```
from a functioning dual core processor...just for grins.

d1337

**EDIT**-Ouch...I have schooled myself.  There is another kernel, Linux 2.6.12-rc2-mm3, which may be what you would need for a dual core processor for full functionality.  I'll have to do some more studying.

---

### Post by Yes_It's_Me on 2006-01-25
hmmmmm, anyone else shore on this?

---

### Post by Yes_It's_Me on 2006-01-25
bump

---

### Post by el3ktro on 2006-01-26
Besides that I've never heart about such a feature, why would you want that? I think it's better to trust the OS to assign tasks to the two or more CPUs in the right way. If you have two cores, all tasks should be "balanced" so that both CPU cores have about the equal workload. There's no practical need to change this manually imho - except you're a dev and want to optimize multitasking/-threading capabilities etc.

Tom

---

### Post by Yes_It's_Me on 2006-01-27
Oh, so can ubuntu do it automatically?

---

### Post by el3ktro on 2006-01-27
[QUOTE=Yes_It's_Me]Oh, so can ubuntu do it automatically?[/QUOTE]

Ehm, of course it can .... I mean what do you think two processors are for? It would be kind of useless if you had to tell each program on which of the two CPUs or cores it should run. The OS chooses the best strategy automatically.

Tom

---

### Post by Caseyjp on 2006-04-19
Setting the affinity is DAMN important for games or applications that NEED to use one cpu.  An example of this EVE-Online which is very cpu graphics intensive.  On the SMP kernel the processes divide amongst the cpus and the frame rate in game goes nuts.  It jumps to high numbers and then flakes out and goes to extremely low numbers.  There are probably other applications written for the single cpu, but there IS A REASON the affinity setting is in windows, and it is for EXACTLY this type of issue.

---

