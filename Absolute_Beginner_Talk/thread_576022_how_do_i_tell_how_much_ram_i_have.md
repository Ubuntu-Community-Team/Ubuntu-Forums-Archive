---
title: "how do i tell how much ram i have?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by 005david on 2007-10-14
and how do i tell what kind of ram?

somebody gave me a 256mb DIMM from a computer they took apart (and the old monitor) and i don't know if it will fit (do i have an open slot) or how much i already have.  help?   

(and i want to know without taking the case off...)

---

### Post by kc5hwb on 2007-10-14
System -> Administration -> system monitor

---

### Post by 005david on 2007-10-14
please post even if you know how to help with only one problem...  i mean...  seeing system info shouldn't be too hard...

---

### Post by 005david on 2007-10-14
> **kc5hwb said:**
> System -> Administration -> system monitorthanks.

---

### Post by nick_h on 2007-10-14
```
sudo lshw | less
```
may give you more information.

---

### Post by avik on 2007-10-14
Note that the amount given is not including the swap space.  For example, I have 1GB RAM, and System Monitor says I have 876MB.  That means the other nearly 150MB are for the swap.  Usually, the amount of RAM you have is a power of two (512MB, 1GB, 2GB, etc.), unless you installed your own RAM.

---

### Post by Squizzle on 2007-10-14
You're saying swap affects your displayed RAM size? I find that difficult to believe. I don't know much of these things but I thought that swap was a partition on your disc that acts as extra ram, like virtual memory in windows.

My 1GB of laptop RAM displays at 882.9 MBs for a different reason - ~128MBs of it has been robbed by the integrated graphics card.

---

### Post by avik on 2007-10-15
The 128MB of video RAM is separate, as far as I know.  It's just that, video RAM that's actually part of the graphics card.

I could be wrong, in which case, my advice still holds: the amount of RAM in the system monitor is not necessarily the same as your actually amount of RAM.

Sorry though.  I'm not the most knowledgeable when it comes to hardware.  I'm more of a software guy :)

---

### Post by santy_kushwaha on 2007-10-15
ya  system will help it to find or just check the pins in the ram

---

### Post by Squizzle on 2007-10-15
> **avik said:**
> The 128MB of video RAM is separate, as far as I know.  It's just that, video RAM that's actually part of the graphics card.

With **integrated** graphics, i.e. a graphics chipset built into the motherboard, there is no dedicated RAM. The chipset shares the RAM and reduces the amount available to the rest of the system.

---

### Post by erginemr on 2007-10-15
I believe your goal is to estimate the type of the ram slots that your computer has, without opening the case. If you are still using Windows as dual-boot, I would suggest using a freeware Windows program "Aida 32". (A Google search will get the job done.)

"Aida 32" and similar programs, which are so-called "system diagnosis software" will provide you with valuable information on your hardware, such as CPU, graphic card, empty memory slots, free memory and what not. 

In the linux world, you may try the linux software "hardinfo" by issuing the command "sudo aptitude install hardinfo" of finding a Debian (*.deb) installation package of it on the web for a more up-to-date version. Hardinfo is on par with the system diagnosis software of the Windows world and will probably reveal the type of memory slots your computer has.

---

