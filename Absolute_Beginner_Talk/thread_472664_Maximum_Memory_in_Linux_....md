---
title: "Maximum Memory in Linux ..."
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-13
My Ubuntu PC has 3GB of RAM.  Windows XP, the 32-bit version, has a maximum limit of 3GB of RAM memory that the OS will utilize.

Is there a limit in Ubuntu Linux???


Carl

---

### Post by lazyart on 2007-06-13
There is but you haven't reached it yet.

---

### Post by mlentink on 2007-06-13
He has if he has a 1GB swap, as usual

see [this thread]("http://ubuntuforums.org/showthread.php?t=471721"), a couple of pages back

---

### Post by starcraft.man on 2007-06-13
> **mlentink said:**
> He has if he has a 1GB swap, as usual

Aye, like any other 32 bit system Ubuntu is limited to 4 GBs. This limit is the combined total of swap/Physical ram. Swap really isn't needed when you run with that much ram, I think the only function it is essential for is hibernating cuz ram needs to be powered to store data and swap obviously does not since its on the drive. So thats it, the only way to have more than 4 GB of swap/ram is to get the 64 bit version which I don't recommend, it causes breakage/problems....

---

### Post by vigleik on 2007-06-13
My understanding is it's 4GB if using 32bit, and a lot more than that if you use 64bit.

---

### Post by jhenager on 2007-06-13
I just bought 2 GB of PC4200 memory a few weeks ago for about $70, and it made me think back to 1993 when I bought 2 MB for $130 or so. I was so pumped that I could finally run 386 Enhanced Mode in Windows 3.1.
Crazy.

---

### Post by starcraft.man on 2007-06-13
> **vigleik said:**
> My understanding is it's 4GB if using 32bit, and a lot more than that if you use 64bit.
[QUOTE=Wikipedia]
The emergence of the 64-bit architecture effectively increases the memory ceiling to 264 addresses, equivalent to 17,179,869,184 gigabytes or 16 exabytes of RAM. [/QUOTE]

[Link.]("http://en.wikipedia.org/wiki/64-bit")

We won't be hitting exabytes of ram for a long while me thinks. The number comes from 2^64 btw, try it on your calculator :p.

---

### Post by cwmoser on 2007-06-13
On my PC, I have a 1GB swap and 3GB RAM.  So, does my Ubuntu Linux utilize all of this memory:  1GB + 3GB = 4GB?

Would any more memory help - or even be utilized?  I'm running the 32-bit Ubuntu Linux.

Carl

---

### Post by mlentink on 2007-06-13
> **cwmoser said:**
> 
Would any more memory help - or even be utilized?  I'm running the 32-bit Ubuntu Linux.


You're done. The 32-bit version cannot address more than 4GB. The only thing you could do is to install another GB and get rid of your swap.

---

### Post by starcraft.man on 2007-06-13
> **cwmoser said:**
> On my PC, I have a 1GB swap and 3GB RAM.  So, does my Ubuntu Linux utilize all of this memory:  1GB + 3GB = 4GB?

Would any more memory help - or even be utilized?  I'm running the 32-bit Ubuntu Linux.

Carl

Yup, your at the max for 32 bit. You can't put in any more swap it would go undetected/unused. If you add another stick of ram (to max at 4 GB), to get it used you would have to shrink the swap to something small like 128 MB(I think thats the min for hibernate...). You can likely even eliminate the swap entirely if you had 4 GB, its only really needed if you hibernate your machine. I don't >.>.

Edit: YAR!!!! Everyone's beating me to the post today :p

---

### Post by dptxp on 2007-06-13
> **starcraft.man said:**
> Aye, like any other 32 bit system Ubuntu is limited to 4 GBs. This limit is the combined total of swap/Physical ram. Swap really isn't needed when you run with that much ram, I think the only function it is essential for is hibernating cuz ram needs to be powered to store data and swap obviously does not since its on the drive. So thats it, the only way to have more than 4 GB of swap/ram is to get the 64 bit version which I don't recommend, it causes breakage/problems....

I use 64 bit, it does not break down. Wait till Kliz reads this :)

Ubuntu uses SWAP even if RAM is available. Check you system monitor.
HDD space is pretty cheap, why bother.

---

### Post by starcraft.man on 2007-06-13
> **dptxp said:**
> I use 64 bit, it does not break down. Wait till Kliz reads this :)

Ubuntu uses SWAP even if RAM is available. Check you system monitor.
HDD space is pretty cheap, why bother.

Well no, I didn't mean its bad. It is just this is a 32 bit world and a lot of apps are trouble to get working in 64 bit, some aren't even coded to work at all and you have to force a 32 bit version in. I'm sticking to 32 I don't see any need for more than 4 GB of ram right now.

As for Ubuntu using swap your right it does, the system won't use more than 4 total thats what we were saying. And the reason not to use swap is RAM is faster than swap, thats well known, thus if your using a lot of swap on the HDD your slowing your system down.

---

### Post by dptxp on 2007-06-13
> **starcraft.man said:**
> Well no, I didn't mean its bad. It is just this is a 32 bit world and a lot of apps are trouble to get working in 64 bit, some aren't even coded to work at all and you have to force a 32 bit version in. I'm sticking to 32 I don't see any need for more than 4 GB of ram right now.

As for Ubuntu using swap your right it does, the system won't use more than 4 total thats what we were saying. And the reason not to use swap is RAM is faster than swap, thats well known, thus if your using a lot of swap on the HDD your slowing your system down.

Yes, there are times when we feel stuck in 64 bit. I use 64 bit on my laptop but 32 bit on desktop (it is AMD64 too). I have not tried running 32 bit applications in 64 bit, i do not want any pain.

I do not know how Ubuntu uses SWAP/RAM, maybe if the RAM is not large enough, it uses SWAP to retain some RAM for more RAM intensive jobs for speed.

---

### Post by cwmoser on 2007-06-13
When I start up System --> Administration --> System Monitor and go to the System tab, It states that I have 2GB RAM and two processors.  That cannot be right as I have a single core processor and Windows XP reports that I have 3GB RAM.

Is there another tool to check resources?  

Also, I recall a post a while back that one had to recompile their Kernel setting a variable to access beyond 1GB Ram -- was that factual or not so?

Carl

---

### Post by Nekiruhs on 2007-06-13
Wow, thanks for that info. When installing this was my thought process:
Swap < Ram + I have 500 GB HD space = 6gb Swap 2gb Ram.
Am I doing myself a disservice by doing that? Should my swap only be 2 gb? Should I resize it? Or just not bother?

---

### Post by dptxp on 2007-06-13
> **Nekiruhs said:**
> Wow, thanks for that info. When installing this was my thought process:
Swap < Ram + I have 500 GB HD space = 6gb Swap 2gb Ram.
Am I doing myself a disservice by doing that? Should my swap only be 2 gb? Should I resize it? Or just not bother?

Let SWAP stay at 6GB, extra SWAP shall not hurt. 
Do it when your Disk becomes full.
It is not easy to resize SWAP, you will need GPARTED LIVE CD.
Just not worth it. You will never ever need that bit of space.
No one runs a 99 % full HDD.

---

### Post by starcraft.man on 2007-06-13
> **Nekiruhs said:**
> Wow, thanks for that info. When installing this was my thought process:
Swap < Ram + I have 500 GB HD space = 6gb Swap 2gb Ram.
Am I doing myself a disservice by doing that? Should my swap only be 2 gb? Should I resize it? Or just not bother?

Uh.... I gotta disagree with dptxp. 6 GB of swap is waste. Here is an easy test to find out. Start the most intensive thing you do with Ubuntu on a _daily basis_ (like a VM with multiple apps open for me) and then open the system monitor (System > Administration > System Monitor). Then watch the memory and swap history. Memory is your physical RAM, Swap is of course the scratch surface on your HDD. I bet you won't even see it break 1 GB the whole time. I only have one GB of regular DDR1 Ram and I don't break 1 GB in my maximum use (I average between 500-600 MB in Swap and maxed out RAM), which is a VM with 512 MB of Virtual Ram, Firefox, Banshee playing, Ktorrent downloading, Democracy downloading and OO writing a document. I do it all on my ol' p4, its an amazing machine :D.

I'd tell ya to shrink that down to maximum of 2 GBs of Swap, I'd probably even go 1. 2 GB of physical RAM is more than enough for operation and Swap is really only there for when your OS runs out of regular RAM (like above when I maxed my GB out on my VM) to make sure it doesn't slow to a crawl (which it does if it runs out of RAM/Swap). Swap will slow your machine down though when compared to RAM, that is known, writing and reading to HDD is simply slower than RAM.

For further reading of benefits of not running out of RAM, [please read the wikipedia article]("http://en.wikipedia.org/wiki/RAM"). There's one on swap file/paging file (thats what its called in windows) in there, search and you'll find it.

---

### Post by Nekiruhs on 2007-06-13
Thanks starcraft.man I resized it using Gparted on the live CD. Its now 2gb.

---

### Post by starcraft.man on 2007-06-13
> **Nekiruhs said:**
> Thanks starcraft.man I resized it using Gparted on the live CD. Its now 2gb.

Your welcome. You know it sounds so funny when people call me starcraft.man... I should have probably registered as Zealot.man or protoss something, oooh ooooh Executor, now thats just a DAMN cool name. starcraft.man just sounds weird. :p

---

### Post by Nekiruhs on 2007-06-13
> **starcraft.man said:**
> Your welcome. You know it sounds so funny when people call me starcraft.man... I should have probably registered as Zealot.man or protoss something, oooh ooooh Executor, now thats just a DAMN cool name. starcraft.man just sounds weird. :p
What about Overmind.man, or InfestedTerran.man? That game was great. I'm sooo happy Blizzard is making Starcraft II. Theres also a huge petition to make it linux compatible.

---

### Post by regomodo on 2007-06-13
I may be wrong but surely isn't 1GB of swap and 3GB of ram wasted? It's a max of 4GB of CPU (32bit) addressable space and those addresses are taken up by other devices (pci/sound/graphics/ide devices?) than just RAM.

Someone correct me if i'm wrong as i didn't do too well in my 68000 module

---

### Post by starcraft.man on 2007-06-13
> **Nekiruhs said:**
> What about Overmind.man, or InfestedTerran.man? That game was great. I'm sooo happy Blizzard is making Starcraft II. Theres also a huge petition to make it linux compatible.

LOL the infested terrans. I loved those... run up to someone and BOOOOOOOOM! Hahahah.

But I'm a protoss man, have to stay on my side ;). Carriers were so cool in that game, and when ya had like 6 or more all on the same screen it was just awesome :).

Anyway, Blizzard better not screw up the sequel... or else.

Edit: To regomodo. No, I don't think 4 GB (combined) is waste. I run VM's all the time and more ram = better performance and maybe even multiple VMs running at same time (on my ol' p4 i'm limited to one VM due to CPU limitations).

---

### Post by regomodo on 2007-06-13
Well ok, not a waste exactly but surely some RAM is left unused?

---

### Post by jhenager on 2007-06-13
So the default swap size was a waste of my hd, if I am understanding the 4 GB total limit.

---

### Post by raijinsetsu on 2007-06-15
It's not exactly true about the "4G" limit on 32-bit operating systems. Most new processors support PAE (Paging Address Extension). However, the stock linux kernels do not support >4G total memory space without a kernel recompile. Windows supports >4gb on their Server products. There is some extra over-head in using PAE (virtual memory pages need to be remapped when accessing anything outside the current 4GB window), but you will fully utilize all your memory.
IMHO - only those people running database servers or multiple VMs really need anything more than 4gb of memory space.
The upside to 64-bit is it natively supports all the memory your system could ever have.

PS - Windows XP (ME?) 32-bit has a cap of 3GB because MS wants you to buy Server 32-bit (which supports upto 64gb on processors with PAE).

---

### Post by Happy_Man on 2007-06-15
> **Nekiruhs said:**
> What about Overmind.man, or InfestedTerran.man? That game was great. I'm sooo happy Blizzard is making Starcraft II. Theres also a huge petition to make it linux compatible.
Wait. What? A petition? For Linux compatability? WHERE?????? I NEED TO SIGN THAT!!!!!!!

---

### Post by Nekiruhs on 2007-06-15
[http://www.petitiononline.com/ibpfl/petition.html](http://www.petitiononline.com/ibpfl/petition.html)
There you go!
BTW, its practically exploded... I signed up a month a go as signer 293, there well over 10,000 now.

---

### Post by starcraft.man on 2007-06-15
> **jhenager said:**
> So the default swap size was a waste of my hd, if I am understanding the 4 GB total limit.

Yes! 4.3 GB of Swap won't ever be used no matter how much stuff you run, your cpu (or some other hardware limitation BUS, and such) will top off first likely. Downscale it to 2 GB at most, maybe even 1 and reconstitute excess into your home partition or any other one. No one has a need for 4 GB of swap.

> **Happy_Man said:**
> Wait. What? A petition? For Linux compatability? WHERE?????? I NEED TO SIGN THAT!!!!!!!

*an evil infested terran wanders over to the booth where the petition is and laughs maniacally, BOOOOOM* :p

---

