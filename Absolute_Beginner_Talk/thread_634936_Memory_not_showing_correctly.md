---
title: "Memory not showing correctly??"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-12-08
I just installed 4 new 1GB sticks of RAM but the system monitor only shows 3.5 GB. Any Ideas?

---

### Post by meborc on 2007-12-08
you have to have 64 bit version of OS to support more ram then 4G ... i'm not sure if it is >4 or >=4 :D

---

### Post by mramsey on 2007-12-08
Ok so here is another question... I have a Pentium D processor which is dual core so would that support 64bit? if so can I just install over the 32 bit version or should I just do a fresh install?

---

### Post by overdrank on 2007-12-08
> **mramsey said:**
> Ok so here is another question... I have a Pentium D processor which is dual core so would that support 64bit? if so can I just install over the 32 bit version or should I just do a fresh install?

Hi and to make sure you can use this command ```
lshw | less 
```
And you should see something like this 
*-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.11.2
          size: 1GHz
          capacity: 1GHz
      [COLOR="Red"]    width: 64 bits
[/COLOR]
If you have 64 bits then you can install over the existing installation.

---

### Post by Moop on 2007-12-08
Your processor will support 64 bit. 

I would do a fresh install but you can check the 64 bit forum for upgrade info.

---

### Post by meborc on 2007-12-08
but be warned that some programs are difficult to get working under 64... like java and flash (bu it is possible, check out the 64bit section of the forums)

and the 0.5G memory "boost" :) will probably be unnoticable

---

### Post by mramsey on 2007-12-08
> **meborc said:**
> but be warned that some programs are difficult to get working under 64... like java and flash (bu it is possible, check out the 64bit section of the forums)

and the 0.5G memory "boost" :) will probably be unnoticable

Yeah, I know....the extra .5G has got to be worth an 80% boost in performance:)...It's just a psychological thing I guess.

Anyway```
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3549MB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe
 nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr
          configuration: id=1

```

Any real advantages to going with the 64bit version?

---

### Post by meborc on 2007-12-08
be sure to do some research into 64bit ubuntu computing before you make the jump... so you will land on your paws

---

### Post by SOULRiDER on 2007-12-08
I *THINK* you can recompile the kernel to add Big memory support, so there will be no need to have a 64bit OS installed..

---

### Post by rune0077 on 2007-12-08
> **mramsey said:**
> 
Any real advantages to going with the 64bit version?

That really depends on what you're doing with your computer. The disadvantages are, as already mentioned, that some software won't work on 64-bit (personally I have been able to run all my software, though a few programs required special patches to work properly, but that all depends on what software you plan on running I suppose).

As for advantages, some things run considerably faster on 64-bit, most doesn't though. If you find yourself ripping a lot of CD's and DVD's, and doing a lot of compiling, then you will find the 64-bit much faster than 32-bit. Otherwise, you might not even notice any difference. 

So, as said, do some research before switching...

---

