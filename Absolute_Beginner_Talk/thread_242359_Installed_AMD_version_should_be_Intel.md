---
title: "Installed AMD version should be Intel"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by jdh23 on 2006-08-23
I installed AMD version of Dapper on a new computer that turned out to be a new Pentium.  All worked fine so I didn't worry.  Last night I chose "Hibernate" and this morning I could not get it to "wake up".  When I tried to reboot nothing happened.  The motherboard screen came up and offered "Press Del" to enter Setup.

Pressing "Del" just changed a line on the screen to "Entering Setup..." but nothing happens.

The computer now will not boot even with a Windows cd.  The cd light comes on for 2 seconds and then goes off and the computer sits there unchanged, just the built-in motherboard screen.

Does this sound like a problem caused by installing the wrong version Ubuntu?

Any help would be MOST appreciated. TIA
--John

---

### Post by nrwilk on 2006-08-23
I'm not really sure what you mean by "AMD version of Dapper."  The only thing I can think of that you are talking about a 64bit version.  But, the thing is that if you installed ubuntu64 on a machine with a 32bit processor, it never would have worked.  There are no kernels specific to a particular brand of chip (except SPARC kernels, but this doesn't apply to you).  The different versions of ubuntu are optimised for different kinds of chips, but not different manufacturers.  For example, regular ubuntu 32-bit should run on any intel-compatible processor.  That means Intel and AMD, 32-bit and 64-bit.

So, why is it that you think you installed the wrong version?

The sleep problem is very common.  Sleep, or in the linux world called "suspend-to-ram," is one of the features that is not very widely supported yet.  It's due to the fact that most hardware is manufactured to work specifically with Windows.  Because these hardware manufacturers don't make their driver code available to Linux developers, the Linux devs have to tinker and fiddle and hack their way into a working solution.  Some manufacturers are better than others about this.


I'm not sure how the sleep issue would have borked your system as you describe.  Neither of my ubuntu systems will suspend correctly, but after a hard reboot they both startup normally.

Sorry I couldn't help more, but I hope this helps in some way.

nrwilk

---

### Post by jdh23 on 2006-08-23
Ah, you're right, it was the "64-bit PC (AMD64) desktop CD" which I confused as AMD specific.

So, it did work for a couple of days.  Hard reboots worked ok.  It was only this morning, after I chose "Hibernate" from the quit menu last night, that it fails to reboot.

Does anyone know how to get at the bios if pressing "Del" doesn't work.  Oh what a mess...

--John

---

### Post by Habbit on 2006-08-23
This can sound quite drastic, but if the BIOS insists on running on corrupt CMOS settings, the only way out may be clearing it (=;  you will lose all your settings).

To do so, you will have to refer to your motherboard's manual :rolleyes:. Most of them have a jumper named "Clear CMOS", which you will have to keep short for a few seconds (usually 10 or 15), or even boot once with it shorted. Other (newer) boards sadly lack this jumper, forcing you to remove the onboard battery (usually a little silver round one), keep it out for some 30 secs and insert it again. This procedure is, however, way riskier: make sure you don't invert the battery polarities when reinserting it or there could be an explosion (and don't think "oh, that won't happen", I suffered it).

Hope you get it working, an AMD64 processor is a really tough beast.

---

### Post by jdh23 on 2006-08-24
Finally managed to boot by turning off the power supply switch on the back of the computer.  Afterwards everything worked fine.

---

### Post by nrwilk on 2006-08-24
> **jdh23 said:**
> Finally managed to boot by turning off the power supply switch on the back of the computer.  Afterwards everything worked fine.

Great! I hope you don't have any more major problems like this.  :)

nrwilk

---

