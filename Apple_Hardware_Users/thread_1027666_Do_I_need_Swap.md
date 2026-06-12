---
title: "Do I need Swap?"
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by PhysMeistro on 2009-01-01
Hi all.  Just tri-booted my iMac7,1 with OS X, Ubuntu, and Vista (thanks to tons of help from this forum), and as such didn't make a swap partition.  (Wasn't aware that I could do more than 4 partitions.)  So now I have no swap space.  My question is whether I need swap space.  I have 4GB of RAM, which seems like plenty, but on the other hand, I installed Ubuntu for physics research, and will likely be running some pretty intensive calculations on this machine.  Should I create a swap file?  And if so, how big should it be?

And finally, if I should make a swap file, can someone point me to a thread on the subject, as I'm completely new to Ubuntu?

Thanks in advance.

---

### Post by mkvnmtr on 2009-01-01
It kind of depends on what you are going to do as to how big it should be. On my last install My swap was formed as 2GB. I have 1.25 GB of ram and have never used my swap partition. I shrunk my partition to 1 GB and if I need it it is there. You can delete it and the system will run but it is not a good idea normally. When you say you might need it I would think if you are running more than 1 Gb of ram you can get away with a 2 GB swap. But you have to think ablyt what your max memory usage might be.

---

### Post by Cracauer on 2009-01-01
You should always have swap.

If you don't have swap, then two things happen:

1) the OS cannot page out copy-on-write or anonymous pages that belong to inactive junk.

and

2) consequently the OS is forced to drop readonly mapped pages that belong to active processes.

People who advise you to run without swapspace if you have "enough" RAM fall into two categories:

A) they don't understand what happens to readonly mapped resident pages when memory gets low.

or

B) they willingly run only a single application, such as a game, on a OS with memory management policies that are unsiutable for doing that, and then have a lot of junk in the background that they are not aware of and that cause disk activity and hence take some RAM. If they don't care about that background stuff and only care about the game, and the game is mostly read-write mapped, then you can improve this particular situation by having no swapspace.

---

### Post by shafi on 2009-01-01
> **PhysMeistro said:**
> Hi all.  Just tri-booted my iMac7,1 with OS X, Ubuntu, and Vista (thanks to tons of help from this forum), and as such didn't make a swap partition.  (Wasn't aware that I could do more than 4 partitions.)  So now I have no swap space.  My question is whether I need swap space.  I have 4GB of RAM, which seems like plenty, but on the other hand, I installed Ubuntu for physics research, and will likely be running some pretty intensive calculations on this machine.  Should I create a swap file?  And if so, how big should it be?

And finally, if I should make a swap file, can someone point me to a thread on the subject, as I'm completely new to Ubuntu?

Thanks in advance.

Its good to have a swap partition, it works as a temporary RAM storage.
The operating system copies as much data as possible into main memory, and leaves the rest on the disk
Normally the partion size for the swap formed double size of the ram
have a look to this link: [http://www.ptdd.com/datarecovery/swap.htm](http://www.ptdd.com/datarecovery/swap.htm)

---

### Post by PhysMeistro on 2009-01-01
Thanks for the responses.
So if I want to do a swap file instead of a swap partition, should I still do 2GB?  I'd heard that double your RAM was a good amount of swap space, but 8GB seems ridiculous.

And on a more theoretical note, a friend and I (both unlearned in the ways of Ubuntu) were discussing this the other day.  We were wondering, will swap space ever become obsolete?  As RAM capacities keep increasing (well beyond the rate of software's ability to utilize it), it occured to us that if you have more RAM than you typically ever need anyway-say, 16GB, for an average user in the not too distant future-then swap space will eventually be unnecessary.
Thoughts?

---

### Post by Cracauer on 2009-01-02
> **PhysMeistro said:**
> Thanks for the responses.
So if I want to do a swap file instead of a swap partition, should I still do 2GB?  I'd heard that double your RAM was a good amount of swap space, but 8GB seems ridiculous.


Yes, that rule of thumb is not valid when expanding RAM in an existing machine for an existing workload.

The rule of thumb is only valid if you have no idea what the workload is like. Then you can guesstimate that if you stuffed in enough RAM to work comfortably your workload should be happy with a total of three times the RAM.

But if you don't change your workload and expand RAM from 4 to 8 GB, then you can reduce swap from 8 to 4.  The same workload will be happy with the same total amount of physical memory (RAM + swap).

That rule of thumb has been abused to death. Also note that they give you the same rule of thumb for systems that first mirror RAM with swap, that means 4 RAM + 8 swap give you 8 total, not 12.  Still, they use the same rule of thumb. Don't buy into it too much.

> **PhysMeistro said:**
>  And on a more theoretical note, a friend and I (both unlearned in the ways of Ubuntu) were discussing this the other day.  We were wondering, will swap space ever become obsolete?  As RAM capacities keep increasing (well beyond the rate of software's ability to utilize it), it occured to us that if you have more RAM than you typically ever need anyway-say, 16GB, for an average user in the not too distant future-then swap space will eventually be unnecessary.
Thoughts?

No, see my first post in this thread.

Virtual memory management always need space to park read-write mapped pages to work best.

---

### Post by cyberdork33 on 2009-01-02
also, I believe that if you plan to use hibernate functions, you have to have a swap partition at least the same size as ram as the contents of RAM is dumped there for hibernation. I don't know how it would work with a swapfile rather than a swap partition...

---

### Post by Cracauer on 2009-01-02
> **cyberdork33 said:**
> also, I believe that if you plan to use hibernate functions, you have to have a swap partition at least the same size as ram as the contents of RAM is dumped there for hibernation. I don't know how it would work with a swapfile rather than a swap partition...

(that only applies to Linux software hybernation, not the BIOS-driven suspend-to-disk)

I always wondered: how does that work if you swapspace is already full with dirty pages from anonymous mappings?

---

### Post by cyberdork33 on 2009-01-02
> **Cracauer said:**
> (that only applies to Linux software hybernation, not the BIOS-driven suspend-to-disk)

I always wondered: how does that work if you swapspace is already full with dirty pages from anonymous mappings?

Well, Macs don't have a BIOS :) Still don't know how it works on the Mac. I don't use hibernation myself.

---

### Post by Cracauer on 2009-01-02
> **cyberdork33 said:**
> Well, Macs don't have a BIOS :) Still don't know how it works on the Mac. I don't use hibernation myself.

They have a BIOS-equivalent that manages suspend-to-disk without the OS.

---

### Post by Tomatz on 2009-01-02
> **Cracauer said:**
> They have a BIOS-equivalent that manages suspend-to-disk without the OS.

They do have bios (basic in out settings) but it is off limits to the user ;)

---

### Post by Cracauer on 2009-01-02
> **Tomatz said:**
> They do have bios (basic in out settings) but it is off limits to the user ;)

Anyway, the point is that for suspend-to-disk you have two options: 1) let Linux do it 2) let the computer do it.

"BIOS" doesn't mean a bunch of config option screens.

---

### Post by Tomatz on 2009-01-02
> **Cracauer said:**
> Anyway, the point is that for suspend-to-disk you have two options: 1) let Linux do it 2) let the computer do it.

"BIOS" doesn't mean a bunch of config option screens.

Well said :)

---

### Post by cyberdork33 on 2009-01-02
> **Tomatz said:**
> They do have bios (basic in out settings) but it is off limits to the user ;)

> **Cracauer said:**
> Anyway, the point is that for suspend-to-disk you have two options: 1) let Linux do it 2) let the computer do it.

"BIOS" doesn't mean a bunch of config option screens.

> **Tomatz said:**
> Well said :)

but that isn't the case. Macs have EFI, not a BIOS.

---

### Post by Tomatz on 2009-01-02
> **cyberdork33 said:**
> but that isn't the case. Macs have EFI, not a BIOS.

I take my hat off to you sir ;) 

I just assumed macs used bios as i read something where someone hacked their macs mainbord configuration utility.

You learn something new everyday. Not that I'd ever use an evil-mac!


[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

---

### Post by Porch on 2009-01-02
In general, having a swap partition, or worse case, swap file is a good thing. However, as a test, I have been going without any swap type in my main work/play system. A Macbook with Ubuntu 7.10 now 8.10 and 2GB of ram. I do lots of stuff on this laptop including VMWare. The only times I have ran out of memory is when some app went nuts and started to eat up all the memory. In the past 2 or so years, it's happened 3 times. A swap file would give me some more lead time to quickly kill the app, but it's not that big of a problem. 

I do keep a a little graph open in my task bar. When I start to run out of memory, I see what is causing the problem and kill it. Most of the time, it's Firefox crashing. But again, it does not happen often.

Right now, I have no plans to ever install anything swap. I don't need it. And if I ever do, a simple swap file is easy to do. 

Be daring and go without the swap.

---

