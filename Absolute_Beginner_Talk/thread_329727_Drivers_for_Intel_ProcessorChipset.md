---
title: "Drivers for Intel Processor/Chipset"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2007-01-02
I would like to have drivers for intel processor and 945gm chipset in order to improve performance. It's obvious, by comparing the power to Windows, that Ubuntu is not using all of what the processor and chipset can provide.

I went to the Intel website, and there was nothing for the processor. I believe there's the smp kernels (i searched "smp kernel" up in synaptic), but I'm not sure which one to choose. They all support AMD or up to the Pentium 4, and nothing beyond that. I have a Core Duo T2300 @1.66ghz, and would like to make sure that both cores are used to the full potential.

As for the 945GM graphics, intel directed me to intellinuxgraphics.org, which seems to confuse me more than anything.

Please give me any info you have on which kernel I should get (for the processor), and provide me with info regarding the chipset (which is most commonly used on all newer notebook computers)

---

### Post by maxamillion on 2007-01-02
If you are running Edgy (6.10) you don't need a kernel specific to the processor, they have been replaced by the -generic kernel because it is able to dynamically load what optimizations are needed for you particular processor.

> t's obvious, by comparing the power to Windows, that Ubuntu is not using all of what the processor and chipset can provide.

I really don't understand what you mean by this.... I assume you are having performance issues with Gnome or some other piece of software, but I can almost guarantee that Ubuntu is outperforming windows hands down (the only reason it wouldn't be is if there is something wrong with your system's software).

---

### Post by geo_bio on 2007-01-02
> **maxamillion said:**
> If you are running Edgy (6.10) you don't need a kernel specific to the processor, they have been replaced by the -generic kernel because it is able to dynamically load what optimizations are needed for you particular processor.


I really don't understand what you mean by this.... I assume you are having performance issues with Gnome or some other piece of software, but I can almost guarantee that Ubuntu is outperforming windows hands down (the only reason it wouldn't be is if there is something wrong with your system's software).

.... what if? I'm running Drapper 6.06 since I know that there's more problems in 6.10 and not really much benefits that I *need*.

Therefore I can't just use generic, and need to know which one to choose.
So maybe it isn't the processor, but the graphics. I downloaded one from intel, but have no clue what to do with it. It says to type "make MAKE=make" after I got into the folder "cd /home/geo/Desktop/xc"... but then it says that "make" is not a valid command (I'm using the default terminal.

---

