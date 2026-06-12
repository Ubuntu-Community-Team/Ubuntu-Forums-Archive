---
title: "[SOLVED] How does Ubuntu handle RAM, cache and swap?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-11-25
Hello,

I am wondering how I can speed up my system. I use a HP Pavilion laptop (dv2109nr) with a processor that's around 2GHz, 1GB of RAM, a swap file of 2GB on my disk, 15GB for the / partition and another 15GB for the /home partition. I am very happy with the overall behavior of my PC and I usually don't run a million apps at the same time (old Windows habit I suppose!).

When I was considering making changes (like adding RAM) I realized that I knew absolutely nothing about how Ubuntu handles memory.

So my questions are:

[COLOR="Blue"][B]1. Can the system be faster than it is now? Do I need to edit a config file somewhere and how?

2. If the whole /usr directory was loaded in RAM, would that make a difference? How can this be done? Is this a stable/recommended solution?

3. Is there a way to set Ubuntu to use RAM first, then only swap; or is it activated by default?

4. My CPU gets very hot for some reason. Is there a way to cool it down (i.e. to put it in an 'idle' state)?[/B][/COLOR]

Thank you for your answers! :)

---

### Post by weresheep on 2007-11-25
Hello,

> 1. Can the system be faster than it is now? Do I need to edit a config file somewhere and how?

No, not really. Unless you are having a specific problem, Ubuntu will make good use of all available resources within your computer.

> 2. If the whole /usr directory was loaded in RAM, would that make a difference? How can this be done? Is this a stable/recommended solution?

The Linux kernel is a very smart piece of software and is sort of doing this already. Memory that is not currently being used by programs is used by the kernel to cache disk access (access to programs and files). If you look at 'top' or run 'free' you will likely see that a large portion of your RAM is being used for 'buffers' and 'cached'.

For example...

```

gavin@strathconon:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        470         32          0          2        214
-/+ buffers/cache:        253        250
Swap:         1474         33       1440

```

One advantage of this approach is that if a program suddenly requires a large amount of RAM, the kernel can quickly free some disk cache and make the RAM available. If you were to load /usr into RAM then that RAM would be permanently unavailable to the rest of the system regardless of whether it was being used or not.

The kernel knows what it is doing and its best to leave it alone :) 

> 3. Is there a way to set Ubuntu to use RAM first, then only swap; or is it activated by default?

The swap partition is enabled by default but the Linux kernel generally only starts to page out to disk (use the swap partition) when available physical memory is contended. Again, the best advice is to let the kernel do its thing.

> 4. My CPU gets very hot for some reason. Is there a way to cool it down (i.e. to put it in an 'idle' state)?

You can't really put a processor into an idle mode. Its only idle if there is no process in a runnable state. Under normal web / email usage though, a processor will be mostly idle.

Generally when a laptop processor is idle its frequency can be scaled down, making it run slower and cooler. I think there is an GNOME panel applet that can monitor frequency scaling (right click on GNOME panel and select "Add to Panel...") , so you could check to see if Ubuntu is actually scaling your processor or if there is something wrong.

Hope that helps.
-weresheep

---

### Post by scorp123 on 2007-11-25
> **the8thstar said:**
>  I am wondering how I can speed up my system.  Why would you need to do that? Is anything particularly slow or something like that? If not I'd suggest you let it be. "Don't fix it if it ain't broken" as they say.

> **the8thstar said:**
>  I use a HP Pavilion laptop (dv2109nr)  dv2108ea here.

> **the8thstar said:**
>  with a processor that's around 2GHz  1.6 GHz here and very happy.

> **the8thstar said:**
>  1GB of RAM, a swap file of 2GB on my disk, 15GB for the / partition and another 15GB for the /home partition.  1 GB RAM, 130 MB for /boot, 2 GB for /, 6 GB for /usr, 4 GB for /opt, 2 GB for /var, 130 GB for /home and finally 2 GB for swap. Proper "UNIX-style" partitioning can help the performance a great deal, e.g. separating the partitions that get plenty of read accesses from the partitions that have plenty of write accesses. Totally old-school, I know. But that's how I learned it.

> **the8thstar said:**
>  When I was considering making changes (like adding RAM) I realized that I knew absolutely nothing about how Ubuntu handles memory.  Adding RAM is always a good idea. But you don't really need to worry as to "how Linux handles memory". The answer to that is very simple: "As efficient as possible" (especially true when compared to Windows which does a really poor job at this). Unused RAM gets used as additional disk buffer and cache so no RAM is wasted. You can see that if you type the command "free" into a terminal. It may look like all your RAM is full ... take a look at the lines where it says "+/- buffers/cache". That's where your unused RAM went. So mostly you don't need to tinker with that at all. It just works. And any bit of RAM you can give to your system is put to "good use" by the kernel, exactly what you'd expect from a good operating system.

> **the8thstar said:**
>  1. Can the system be faster than it is now? Do I need to edit a config file somewhere and how?  Why do you ask that? Do you perceive the system as being too slow? There are a few minor tweaks you could try out (e.g. play around with the **vm.swappiness** parameter as described e.g. here: [http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/2/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/2/) ) but chances are you won't notice any big differences.

> **the8thstar said:**
>  2. If the whole /usr directory was loaded in RAM, would that make a difference? How can this be done? Is this a stable/recommended solution?  Why would you want to do *that* :confused: ..... It would be better to read + learn about proper UNIX-style partitioning and have /usr on a separate partition. That should speed-up things. What you suggest is quite unusual and I'd say it's *not* recommended.

> **the8thstar said:**
>  3. Is there a way to set Ubuntu to use RAM first, then only swap; or is it activated by default?  That's more or less the default behaviour. Swap is never ever used unless really really needed. But this can be further fine-tuned if you want. See the URL above.

> **the8thstar said:**
>  4. My CPU gets very hot for some reason. Is there a way to cool it down (i.e. to put it in an 'idle' state)?  Can you please add a "CPU scaling monitor" to your panel and observe that a little? It's normal that a CPU gets hot over time, but the question is: How hot is "hot"? My CPU is most of the time running at 800 MHz (the system automatically scales it down to that slow speed) and only if I really do something demanding it will go full-speed (1.6 GHz in my case). It also depends on what CPU policy is set. On my system it defaults to "ondemand"; but I have seen systems where it defaults to "performance" and the CPU there is always running at max. speed and therefore gets very very hot in no time. In that case you'd need to edit some config files to change that.

---

### Post by the8thstar on 2007-12-30
Thank you guys for your replies. The reasons I was asking these questions is simple: I like to tweak things. I'm always on the lookout for the simplest program that will create the best benefit to the OS. Old Windows habit I guess... :)

---

### Post by oldos2er on 2007-12-30
You can google for tweaks, there are lots of them out there. Just be careful when altering system files--it's a good idea to make backups first.

 If you want a faster distro, try Vector standard 5.9.

---

### Post by blueridgedog on 2007-12-30
> **scorp123 said:**
>  1 GB RAM, 130 MB for /boot, 2 GB for /, 6 GB for /usr, 4 GB for /opt, 2 GB for /var, 130 GB for /home and finally 2 GB for swap. Proper "UNIX-style" partitioning can help the performance a great deal, e.g. separating the partitions that get plenty of read accesses from the partitions that have plenty of write accesses. Totally old-school, I know. But that's how I learned it.


Do you think there is a performance increase even though those mount points are on the same spindle on you laptop?

I too learned it that way, but that was when we have separate spindles that could speed things up.  Even though I am an old school guy, I have given in to a simple setup of /, swap and potentially /home if you have a fat disk that you want to use for music/video etc. (and only if you have a second fat disk, if you have one disk then I go with / and swap).

---

### Post by scorp123 on 2007-12-30
> **blueridgedog said:**
>  Do you think there is a performance increase even though those mount points are on the same spindle on you laptop?  I know for sure that there is a performance decrease if I don't do it like that. e.g. I have here a very old Sony VAIO C1VFK "PictureBook" laptop. Transmeta "Crusoe" CPU, 667 MHz (ha! what a joke!! It sure feels like being on an old P2 with 200 MHz ... this CPU is sooooo slooooow!), 192 MB RAM (only 176 MB RAM are usable, the rest is used as "shared memory" by the ATI graphics chip), 15 GB disk ... If I put everything on a single "/" partition this laptop is unbearably slooooooow. It will make you want to jump out of the window. "UNIX-style" partitioning indeed helps this stupid slow little laptop gain considerable performance, so that it's almost usable, e.g. as "chat station" where a simple chat client could run as sole task. Guessing from this I'd assume that other PC's too may profit from proper partitioning, even if it's hardly noticeable unless the PC in question is such a slow junk system like this ancient Sony VAIO laptop here.

> **blueridgedog said:**
>  I too learned it that way  I stick to this "old school" setup. Just for the purpose of "safety" if nothing else. Having everything on one single "/" partition means that one single corruption on the filesystem could mean serious trouble for your entire installation, whereas having stuff spread out and on separate partitions means that if there is a corruption somewhere somehow, that only one single filesystem (e.g. "/var") would be affected and the others not. This greately increases your chances of being able to repair this corruption "on the fly" without the need of any special "rescue CD's" or live CD's of any sort.

As I said ... this "old school style" of partitioning is how I learned it, and I will stick to that. This kind of setup has proven itself again and again over the years.

---

