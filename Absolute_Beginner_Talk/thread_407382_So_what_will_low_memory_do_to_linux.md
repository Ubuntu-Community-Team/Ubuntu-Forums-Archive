---
title: "So what will low memory do to linux?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-04-12
In general what can happen if ram is low and top only shows 3 meg left out of 256, and swap is fully in use?  Can is cause system freezes?  Can is cause SSH to not work properly, or hand on login?

I had a NAS basically freeze up and memory was fully in use and swap was about full.  Runs a version of Redhat.  Wondering it that's normal when memory gets eaten up -system grinds to a halt and cannot execute commands anymore.  I have never had a box running linux or unix eat up all of the memory before so I'm not sure it this is "normal" + I'm no expert.

---

### Post by anaconda on 2007-04-12
Yes!
Actually linux kernel overuses the ram. So if you have 512 MB ram and one program asks for 300MB: of ram and then the 2nd program asks for 350MB both queries are accepted and both programs are given the ram they asked for.

Obviously this can (and will) cause problems, when the programs actually want to use the memory at the same time.

When memory runs out the OOM-killer (Out Of Memory killer) starts randomly killing memory-hungry aplications.

So yes it is "normal", but you should have enough swap, so that OOM-killer wont ever start killing aplications. 

Google for OOM-killer if you want more info.

actually this way of using memory is thought to be very efective.. I think this kind of memory allocation can be switched off so that overusing memory wont happen and then oom-killer wont ever start.

EDIT:  in this swap memory is the same than actual ram. so oom-killer starts when you run out of both ram and swap..

---

### Post by LaurelLynn on 2007-04-12
Dear Atomic Dog,

I don´t know of any os that takes a lack of memory well.  Having to use swap space tends to make everything slow to a crawl.

Filling both ram and swap up, will result at least in an inability to run new programs, or many commands. So the answer to your question is yes that is what commonly happens.

---

### Post by Atomic Dog on 2007-04-12
Thanks for the 411.  I thought so, but wanted to be sure.  Good information!

---

### Post by sailor2001 on 2007-04-12
freeze-up is common in ubuntu if the ram is too low.

---

### Post by FuriousLettuce on 2007-04-12
Just so you know, Linux handles its memory differently to Windows (apart from Vista). Where Windows will purge RAM entries that haven't been accessed in a while (minimised applications), wheras Linux will keep all entries in the RAM until it starts running out space, so even if you have 2GB it's likely to be full, it's nothing to worry about - you don't have to start killing applications to free up memory, it will be handled fine by Linux.

If you have a low amount of RAM, you should be fine as long as you have enough swap space, just be aware it will make the system much slower if you are continually using the swap space.

---

