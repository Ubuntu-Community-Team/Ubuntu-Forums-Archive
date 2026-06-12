---
title: "Did I buy too much RAM for Ubuntu? Or am I lost again?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by langster on 2007-09-12
I pose a question to the community concerning RAM and HDDs. Having read the speed difference between RAM and HDDs, i just wonder why ubuntu 7.04 64 only uses 633 MB of user memory for my rig out of 1.8 gigabytes in System Monitor? No matter what program I use, I cannot utilize >50% of RAM. Is ubuntu underutilizing the 2 Gig + monstrosities that common brand names are pumping out now with dual and quad cores? Can we somehow use the command line to get more out of the RAM? I would like some of the community out there to please list what programs they now have open and running and then what does your System Monitor say about your RAM usage?. Thank You. Maybe there is some awesome programs I don't know about which should be running now as well on my half awake rig.

For example,
Firefox Surfing / You tube streaming
Iceweasel playing Java chess
Bit Torrent Sharing 7.04 64
System Monitor
Firestarter
XMMS
AbiWord
Some other game

CPU 1: 12%
CPU 2  18%
User Memory: 633 MB out of 1.8 Gig
Used Swap: 38.2 MB out of 3.3 Gig 

Cheers!:)

---

### Post by jflaker on 2007-09-12
This is not Windows!

Windows loads alot of crap in memory whether or not it is being used.  Linux has always ran lean and will load what it needs only when it is needed.

Enjoy having plenty of resources!.....
217MB of 1GB with 2 browser windows open.

---

### Post by swoll1980 on 2007-09-12
You don't need all that ram unless your doing some sierious gaming or running multiple vm's

---

### Post by oilchangeguy on 2007-09-12
your computer is fine. it's not supposed to max out it's ram. if it does, then you've got problems. if it ain't broke, don't fix it.

---

### Post by mpgarate on 2007-09-12
i have 2gb ram, and ii think all mine's getting used.. are you sure that your computer is gonna need the memory? I don't think ive ever seen mine go above 50%.. just because im not using that much stuff... except the cache... that gets up to about 80% sometimes...

try this.. add the system monitor to the panel and look at the memory part (make sure its enabled) how much is used there? heres mine

[http://mikesubuntu.googlepages.com/Screenshot.jpg](http://mikesubuntu.googlepages.com/Screenshot.jpg)

---

### Post by ryno519 on 2007-09-12
I've nver seen anybody complaining that their system isn't using enough of their RAM before. I for one have 1 gig of RAM and never use more than 350 megs of it.

First of all, you are not underutilizing your RAM. RAM is just memory which holds a programs data, which includes cached data, variables, etc. It's not really possible to underutilize it. As long as you're < 100% usage you're perfectly fine. You can never have too much RAM.

---

### Post by oilchangeguy on 2007-09-12
> **bloor75 said:**
> You don't need all that ram unless your doing some sierious gaming or running multiple vm's

maybe not at the present time. but as operating systems continue to evolve, he will.

---

### Post by K.Mandla on 2007-09-12
Linux is far more memory-efficient than its Windows counterparts. 

If you'd like to study more about how Linux handles memory resources, the Gentoo wiki is an excellent place to learn.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by NovaAesa on 2007-09-12
I have a similar question to this (and it appears to be happening to langster).

Why is some swap space used before the _entire_ main memory is used? It just seems silly to me - isn't swap space many times slower than main memory?

---

### Post by oilchangeguy on 2007-09-12
> **jflaker said:**
> This is not Windows!

Windows loads alot of crap in memory whether or not it is being used.  Linux has always ran lean and will load what it needs only when it is needed.

Enjoy having plenty of resources!.....

speak for yourself, and your virus, and spyware loaded machine. a properly maintained windows system, is a good running system.

---

### Post by ryno519 on 2007-09-12
If you want something to take up more of your resources, just so they don't go to waste, may I suggest Folding@Home?

Give it a read. :)

[http://folding.stanford.edu/](http://folding.stanford.edu/)

---

### Post by K.Mandla on 2007-09-12
> **NovaAesa said:**
> Why is some swap space used before the _entire_ main memory is used? It just seems silly to me - isn't swap space many times slower than main memory?
Does this answer your question?

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29)

[quote=Gentoo wiki]When an application needs memory and all the RAM is fully occupied, the kernel has two ways to free some memory at its disposal: it can either reduce the disk cache in the RAM by eliminating the oldest data or it may swap some less used portions (pages) of programs out to the swap partition on disk. It is not easy to predict which method would be more efficient. The kernel makes a choice by roughly guessing the effectiveness of the two methods at a given instant, based on the recent history of activity.[/quote]
Not a word-for-word answer, but it might be helpful.

---

### Post by K.Mandla on 2007-09-12
> **oilchangeguy said:**
> a properly maintained windows system, is a good running system.
This is true. Unfortunately, in most of the circumstances I've seen, Windows has the worst trouble when the [PEBKAC]("http://en.wikipedia.org/wiki/PEBKAC").

---

### Post by overdrank on 2007-09-12
> **K.Mandla said:**
> This is true. Unfortunately, in most of the circumstances I've seen, Windows has the worst trouble when the [PEBKAC]("http://en.wikipedia.org/wiki/PEBKAC").

That is priceless !!!!!!!!:lolflag:

---

### Post by swoll1980 on 2007-09-12
> **oilchangeguy said:**
> maybe not at the present time. but as operating systems continue to evolve, he will.

I should have added vista to that list as well. That thing sucks up memory like it's going out of style

---

### Post by swoll1980 on 2007-09-12
> **oilchangeguy said:**
> speak for yourself, and your virus, and spyware loaded machine. a properly maintained windows system, is a good running system.

I'm just glad I don't have to worry about all that "Maintenance" anymore

---

### Post by vexorian on 2007-09-12
> speak for yourself, and your virus, and spyware loaded machine. a properly maintained windows system, is a good running system.

Is it? I think I tried very hard to make windows stable for 4 years, and I pretty much succeeded by not adding it antivirus or anti spyware and all those shields windows apparentally needs.

And it was working quite well, mostly thanks to firefox and specially noscript that were stopping anything that would try to attack me, I would also say I am good at preventing viruses/etc. Until this year in which my brother got more active with it and I got many virus infestations, since I am good at windows I was able to clean them all but that takes time and is pretty annoying, so I had to implement antivirus, anti spyware, firewall , etc. Now my computer feels protected (unless you count the two occations in which the antivirus didn't block the malware, and I had to still clean it myself...) But windows XP has gotten way slower.

I am just glad I don't use it, let my brother ruin it, I don't care, the only XP I use is one in a virtual machine without internet access, and without those antivirus,etc it is actually faster than when I run the native XP in the same computer...

---

### Post by fflarex on 2007-09-12
As operating systems evolve, it's still hard to imagine that he will need that much RAM within the lifetime of his computer, if that operating system has performance as one of its goals (I'm sure Vista could have been designed with much less powerful systems in mind without sacrificing anything -- even the new Aero effects -- but Microsoft has a strong financial incentive to get people to buy new hardware). GNU/Linux and most related projects have this as a goal.

Now, the exception to this is gaming and other specialized tasks. But even most power users, unless they plan to game, will not need anywhere near 2GB.

---

### Post by vexorian on 2007-09-12
He can need that much RAM, what if he wants to run vista in a virtual machine?

hey, run 4 virtual machines and make a virtual network , just for fun!

---

### Post by por100pre1 on 2007-09-12
> **K.Mandla said:**
> This is true. Unfortunately, in most of the circumstances I've seen, Windows has the worst trouble when the [PEBKAC]("http://en.wikipedia.org/wiki/PEBKAC").

That's true. Ironically, when the PEBKAC issue is resolved,is very likely that the user doesn't like Windows anymore. :)

---

### Post by jimrz on 2007-09-12
> **oilchangeguy said:**
>  a properly maintained windows system, is a good running system.

I tend to agree (at least in the case of XP) but, to be fair, XP does at least show higher memory usage with similar workloads than does Ubuntu.

---

### Post by langster on 2007-09-12
Thank you EVERYONE. Will check out the Virtual Machines, and Folding@Home

---

### Post by sstusick on 2007-09-12
I don't know about anyone else... but I like to see a large percent of free memory in my system monitor.

---

