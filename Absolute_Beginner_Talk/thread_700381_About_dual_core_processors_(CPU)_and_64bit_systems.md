---
title: "About dual core processors (CPU) and 64bit systems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by jis on 2008-02-18
Can Linux take benefit of dual core CPUs? Can you tell processes which core to use? Are all dual core processores able to run 64bit Ubuntu and does a dual core processor become virtual one core processor if used by 64 bit OS? Does using 64bit OS make your computer faster?

---

### Post by meindian523 on 2008-02-18
1]Yes,I'm doing that right now using a Pentium D 2.80 GHz.
2]I dunno,but must be possible.
3]Depends on whether your dual core supports 64 bit addressing and processing.Pentium D does.
4]If you have a 64-bit enabled PC,it doesn't make it faster on it's own but performance is much better compared to using the 32 bit version because of more efficient usage of resources and capabilities.

---

### Post by hyper_ch on 2008-02-18
Intel Core 2 Duo --> 64Bit
Intel Core Duo --> 32Bit
AMD X2 64 --> 64Bit

So, you have to have a 64bit kernel to run a 64bit OS. And linux can use dual-core.

---

### Post by jis on 2008-02-18
> **meindian523 said:**
> 1]Yes,I'm doing that right now using a Pentium D 2.80 GHz.
2]I dunno,but must be possible.
3]Depends on whether your dual core supports 64 bit addressing and processing.Pentium D does.
4]If you have a 64-bit enabled PC,it doesn't make it faster on it's own but performance is much better compared to using the 32 bit version because of more efficient usage of resources and capabilities.

1) But how do you know if it is using only one core or both?
3) Do you mean e.g. Intel 64 technology? I assume it is the same as Intel Extended Memory 64 Technology?

Checked this: 
[http://www.intel.com/products/processor_number/index.htm](http://www.intel.com/products/processor_number/index.htm)
and the demo
[http://www.intel.com/products/processor_number/flash/demo.html](http://www.intel.com/products/processor_number/flash/demo.html)

If I remember right, AMD has that technology even in single core processors called Athlon 64.

4) How does it make more efficient usage of resources and capabilities? I know you can have more RAM when using 64 bit addressing..

---

### Post by meindian523 on 2008-02-18
> **jis said:**
> 1) But how do you know if it is using only one core or both?
3) Do you mean e.g. Intel 64 technology? I assume it is the same as Intel Extended Memory 64 Technology?

Look up in the System Monitor,also during bootup,I see it recognizing two CPUs #0 and #1.
> Checked this: 
[http://www.intel.com/products/processor_number/index.htm](http://www.intel.com/products/processor_number/index.htm)
and the demo
[http://www.intel.com/products/processor_number/flash/demo.html](http://www.intel.com/products/processor_number/flash/demo.html)

If I remember right, AMD has that technology even in single core processors called Athlon 64.

4) How does it make more efficient usage of resources and capabilities? I know you can have more RAM when using 64 bit addressing..

I'm not sure about AMD.Please refer the stickies in the 64 bit for the answers for better usage of capabilities and resources..And 64 bit is NOT just more RAM as the stickies will make clear.Look here specifically:

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by meindian523 on 2008-02-18
And it's not necessary that only dual-cores can have 64 bit addressing or 64 bit instruction sets.So,Athlon 64 might well be having a 64 bit instruction set.I'm not sure though,since the last time I bought a PC,I had not yet been introduced to *nix and therefore my hardware knowledge was a big zero.I didn't even know that a processor manufacturing company called AMD existed which provided much cheaper CPUs than Intel!

---

### Post by jis on 2008-02-18
Is there some benefit of using dual-core processor whose both cores work at speed X, rather than using a single core processor that works at speed 2X?

---

### Post by smartboyathome on 2008-02-18
AMD Athlon 64 is a 64 bit processor. I am on a 64 bit ubuntu install using it right now.

---

### Post by smartboyathome on 2008-02-18
> **jis said:**
> Is there some benefit of using dual-core processor whose both cores work at speed X, rather than using a single core processor that works at speed 2X?

It is more efficient, since the cores are using less power.

---

### Post by jis on 2008-02-18
> **smartboyathome said:**
> It is more efficient, since the cores are using less power.

So dual-core consumes less electricity to give the same processing speed :)

---

### Post by sandysandy on 2008-02-18
> **smartboyathome said:**
> It is more efficient, since the cores are using less power.

is it only the power efficiency or speed efficiency also.

thanks

---

### Post by jis on 2008-02-18
> **sandysandy said:**
> is it only the power efficiency or speed efficiency also.
thanks

I suppose you can get more computing power by two cores, if software can use the cores efficiently.

---

### Post by meindian523 on 2008-02-18
Not necessarily that the cores use less power,the Pentium D which is basically 2 Pentium 4s stuck together(Prescott architecture) has a severe heating problem while the Core 2 Duos(Conroe architecture) save that power,hence the taglines in the ads primarily advertise 40% more processing power,40% less power usage(or 40% more power efficiency,I forget which).

---

### Post by meindian523 on 2008-02-18
> **jis said:**
> I suppose you can get more computing power by two cores, if software can use the cores efficiently.

and that's a hell big problem to code,that is to split up a process into x threads and distribute it to x cores and then re-merge the results of each of those x splits to get a working program which works faster than if it were running on only 1 core,that's what I've heard till now,any newer gossip round the place which I may be ignorant of?

---

### Post by Paqman on 2008-02-18
> **jis said:**
> I suppose you can get more computing power by two cores, if software can use the cores efficiently.

That's an important point. Two cores at 3MHz are not normally twice as fast as single 3MHz.

Basically, if your software isn't written to take advantage of a second core, it won't run any faster. OSes have been designed for multiple processors for a while, but a lot of applications aren't. On top of that, some computing tasks just aren't suited to multithreading, and can't really be written to execute faster even if there's another core available.

---

### Post by Seq on 2008-02-18
> **Paqman said:**
> That's an important point. Two cores at 3MHz are not normally twice as fast as single 3MHz.

Basically, if your software isn't written to take advantage of a second core, it won't run any faster. OSes have been designed for multiple processors for a while, but a lot of applications aren't. On top of that, some computing tasks just aren't suited to multithreading, and can't really be written to execute faster even if there's another core available.

That said, with a single-threaded process misbehaving and hitting 100% processor utilization you still have a useable system and can kill that process. Or you can have two misbehaving processes.

Just because specific applications don't take advantage of SMP does not mean it is useless.

---

### Post by jis on 2008-02-18
Seq, but can't Linux restrict percentage of processor utilization of one process even in a single core CPU?

---

### Post by Seq on 2008-02-18
> **jis said:**
> Seq, but can't Linux restrict percentage of processor utilization of one process even in a single core CPU?

Sure, there are things like [CPU Limit]("http://cpulimit.sourceforge.net/"), but if you knew beforehand that some process was going to run system performance into the ground... Also, schedulers can have a lot of positive effects to help stop a runaway process from quashing productivity. I was just throwing in my two cents.

---

### Post by jis on 2008-02-18
Seq, thanks for the software hint. It is relatively simple program and you have to run one instance for every process you aim to limit. I can imagine more sophisticated priority control could be done.

---

