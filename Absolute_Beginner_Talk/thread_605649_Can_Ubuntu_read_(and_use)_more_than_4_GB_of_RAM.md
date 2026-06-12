---
title: "Can Ubuntu read (and use) more than 4 GB of RAM?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by alicson on 2007-11-07
It might be evident just based on my question that I'm completely new to Linux, but
can Ubuntu make use of more than 4gb of RAM?  If possible, how would I set that up?
I'm on a PC (dual core 2 processor).

[Was very disappointed to learn that Windows has no concept of RAM above (and barely) 4gigs.. Might also be true with Linux, but would think there's more flexibility there..?]

---

### Post by hyper_ch on 2007-11-07
the 64bit version can... the 32bit is stuck at 3gb I think

I think also Windows 32bit is stuck at 3gb

---

### Post by aaaantoine on 2007-11-07
The 32-bit version of both Ubuntu and Windows can use a maximum of 4GB.  Ubuntu *might* be able to use 64GB (I once read that modern 32-bit processors are actually more like 36-bit processors), but beyond 4GB you're better off with the 64-bit version of Ubuntu anyway.

Also, there is a 64-bit version of both Windows XP and Vista.  For a small fee you can order the software discs and use them with your current license.

---

### Post by hyper_ch on 2007-11-07
well, there are hardly any 64bit applications for Windows as far as I know...

---

### Post by insane_alien on 2007-11-07
64-bit can read far more than 4GiB of RAM(i'm running on 8 just now) 

32-Bit will be limited to 3.7GiB(the other 0.3GiB is reserved for external devices like PCI and kernel operations)

the kernel can  be recompiled with the 'big memory' module which uses a block model to address the RAM and can read more than 4GiB thoug hthis is rather innefficient and slightly slower.

in your case i  would recommend moving to 64-bit it will cause the least problems.

---

### Post by alicson on 2007-11-07
So 64-bit Ubuntu should recognize 6 GB of RAM without additional setup/actions?

And there's no conflict with having 32-bit XP Pro and 64-bit Ubuntu (dual-boot) on one machine, right?

Thank you all for your responses.

---

### Post by P4man on 2007-11-07
Its far more complicated than that really. 32 bit OSs (windows or linux, doesnt matter)  can use more than 4GB **Ram,** they have been able to do so since the 386 era I believe. However, 32 bit OSs can not use more than 4 GB of **address  space per process**. Regardless of how much RAM you have. 

Address space is virtual address space, so its basically ram + swap. Ram+swap can never be more than 4GB for each process on a 32 bit OS  This could be a limitation for systems even with just 1GB Ram ( because the rest could be swapped -> virtual address space)  

But its worse than that, the OS also needs its own address space. In windows the realistic limit is 2GB per process (with a hack, this can be increased to 3GB with some caveats)  in Linux, I'm not sure, I think it is 3GB per process. The rest is reserved for the OS. We are talking about **virtual** memory here (ram+swap), not necessarily RAM. You could have more or less RAM, doesnt matter.

So  iIf you are going to run lots  of "small"  applications, or applications that run in different processes, you can might be able to make use of  4GB RAM or even  more on a 32 bit OS. Each app/process will have 2GB address space, and the more RAM you have, the less the OS has to swap.

If you are going to run BIG  applications that need large (contiguous ) address space, you will need a 64 bit OS, even though you might have far less than 4GB Ram (the rest could be swapped).

And if you thought all  that was confusing, note that if you have a process that needs ,say 2 or 2.5GB, on a 32 bit OS you are going to get into problems even though you might have 3GB address space per process, and you might have anywhere from 0,5  to 16GB RAM, doesnt matter (if you have less, it will be swapped, if its more, it will be unused)r. The reason is memory space fragmentation.  64 bit OSs dont have this problem, as address space per process is virtually (pun intended) unlimited. Therefore, they should be faster in theory in this regard, or allow applications or workloads that do not run on a 32 bit OS. Regardless of how much RAM you have.

Are you confused yet ? :)

---

### Post by Inxsible on 2007-11-07
> **alicson said:**
> So 64-bit Ubuntu should recognize 6 GB of RAM without additional setup/actions?

And there's no conflict with having 32-bit XP Pro and 64-bit Ubuntu (dual-boot) on one machine, right?

Thank you all for your responses.Yes. Its the architecture that defines how much memory can be used, because the more the memory you need more bits to address those huge blocks of memory. 32 bit processors can handle only 2^32 bits =  4294967296 bits of addressing. if you notice that's close to 4GB (just a bit less since 1KB = 1024bytes and NOT 1000 bytes). That's why a 32 bit processor can only access 4GB or less. 64 bit processors however can access 2^64 bits = 18446744073709551616 bits  ~= 16 exabytes  ~= 16 billion GB

No. None whatsoever. I have a dual boot of Vista 32 bit and Gutsy 64 bit

---

### Post by P4man on 2007-11-07
> **Inxsible said:**
> Yes. Its the architecture that defines how much memory can be used, because the more the memory you need more bits to address those huge blocks of memory. 32 bit processors can handle only 2^32 bits =  4294967296 bits of addressing. if you notice that's close to 4GB (just a bit less since 1KB = 1024bytes and NOT 1000 bytes). That's why a 32 bit processor can only access 4GB or less. 64 bit processors however can access 2^64 bits = 18446744073709551616 bits  ~= 16 exabytes  ~= 16 billion GBt

you are probably deliberately simplifying,  but the above is incorrect. Since the Pentium Pro, our cpu's have been able to address 36 to 48 bits of **RAM** (depending on the cpu). Do the math, its faaar more tthan  4GB. They have, however, been limited to 32 bit **virtual** address space (per process). Until AMD64 came along that is.

So there could have been Pentium Pro servers with say 64 GB RAM and a 32 bit OS. These worked fine if they ran many small workloads.  That same machine would have been able to process the exact same workload with just 1GB RAM, only MUCH slower. But such a machine could never load a 4GB app (/process) even if it had 64GB RAM; A 64 bit machine with a 64 bit OS would be able to load that 4+ GB workload even if it had only 1 GB physical ram.

Capiche ? 

:)

---

### Post by Inxsible on 2007-11-07
> **P4man said:**
> you are probably deliberately simplifying,  but the above is incorrect. Since the Pentium Pro, our cpu's have been able to address 36 to 48 bits of **RAM** (depending on the cpu). Do the math, its faaar more tthan  4GB. They have, however, been limited to 32 bit **virtual** address space (per process). Until AMD64 came along that is.

So there could have been Pentium Pro servers with say 64 GB RAM and a 32 bit OS. These worked fine if they ran many small workloads.  That same machine would have been able to process the exact same workload with just 1GB RAM, only MUCH slower. But such a machine could never load a 4GB app (/process) even if it had 64GB RAM; A 64 bit machine with a 64 bit OS would be able to load that 4+ GB workload even if it had only 1 GB physical ram.

Capiche ? 

:)I know. When I posted, i meant per process addressing. Sorry I didnt mention it earlier. My bad.

---

### Post by alicson on 2007-11-07
Heh, I've been confused and upset since I discovered yesterday that Windows can barely see 4GB of RAM.  I'm used to running many apps at once, and some of them are always browsers, email client, photo/graphics editing, etc., which would all appreciate more RAM.  I've given a full partition just for pagefile, but I had mistakenly thought that more RAM would be helpful -- not totally and utterly ignored and useless.

Your explanations are quite good, and very appreciated; thank you.   

I don't really trust Vista or even 64-bit XP, so those options are out for me (plus the fact that I'm just sore at Windows at moment, though otherwise mostly very comfortable in it -- have apps and setup for everything I want to do..but I've been telling myself I'll try Linux for years and really want to do that), .. but what are your thoughts re: me running Ubuntu (64-bit) with 6gb of RAM? Will it be no/little difference from, say, 3gb of RAM?  [The answer I want is "yes, yes it will be a wonderful difference", but if it's "no", then I guess I'll return the awesome new RAM and just go back to my 3 (the 4th was a bad stick I never replaced..which turns out not to have mattered because Windows would have never seen it ANYways!!)]

---

### Post by P4man on 2007-11-07
Actually, ,the error was not omitting 'per process' but rather not distinguishing between physical RAM addressing capabilities of the cpu (/chipset) with the virtual address space an OS can use and provide. These are almost literally unrelated. 

This is pretty technical and complicated  stuff though, and probably not relevant to the OP, so sorry for going OT.

---

### Post by P4man on 2007-11-07
> **alicson said:**
> Heh, I've been confused and upset since I discovered yesterday that Windows can barely see 4GB of RAM.]

Indeed, it can't see 4GB Ram even if you give it to it. Has to do with the mapping of video memory by windows in its own address space (even twice). The more videoram you have, the bigger the "hole" will be.
   
> I don't really trust Vista or even 64-bit XP, so those options are out for me (plus the fact that I'm just sore at Windows at moment, though otherwise mostly very comfortable in it -- have apps and setup for everything I want to do..but I've been telling myself I'll try Linux for years and really want to do that), .. but what are your thoughts re: me running Ubuntu (64-bit) with 6gb of RAM? Will it be no/little difference from, say, 3gb of RAM?  [The answer I want is "yes, yes it will be a wonderful difference", but if it's "no", then I guess I'll return the awesome new RAM and just go back to my 3 (the 4th was a bad stick I never replaced..which turns out not to have mattered because Windows would have never seen it ANYways!!)


Well, it really depends but it would surprise me you needed anything LIKE 6 GB ram for the type of apps you just named. I run Ubuntu with all Compiz bells and whistels, 20 open windows (firefox with a few dozen tabs, email, skype, Gimpshop (photoshop clone) and god knows what else, and Im not even close to using just 512 Mb RAM! I got 2 GB installed, since I moved from windows to Ubuntu, I don't think I ever used more than half of that. 

Well, actually, I have, by setting up a virtual machine, running windows inside it. I gave that VM just below 1GB. I still have plenty left !I have never ever swapped, I wonder why I set up the swap partition lol.

windows will swap no matter how much ram you have; it seriously sucks in that regard. With heavy multitasking its always swapping and trashing the disk, even if you are only using a fraction of your installed RAM. Adding more doesnt help there. Switching OSs does.  Try Ubuntu. It will fly with "just" 3GB Ram. I bet you'll never use more than half of it.

---

### Post by alicson on 2007-11-07
::sigh:: I'll farewell to my pretty shiny new RAM, then.  I realize I'm not doing anything really cool and intensive like running a server (when I do, it's very limited and personal), or compiling tons of code and stuffs... but in Windows, it does seem like it eats up all my RAM and would make use of more if only I had it--or rather, if only it could recognize it.

Does Ubuntu use swap file too?
Sorry to ask a Windows question here, but you seem to know -- would it be better to give a smaller space to Windows for pagefile?  I gave it 80gb, and quickly found that it used that all up, so I reduced it to 20, which is still probably absurdly large...
But I do see my Windows system processes running up RAM pretty regularly..

---

### Post by P4man on 2007-11-07
> **alicson said:**
> :
Does Ubuntu use swap file too?.

It needs a swap partition, rather than file, but the idea is the same as with windows, or any other OS. The difference is in implementation. windows will swap inactive apps to disk, even if you have a few hundred gigabyte free ram. Its insane, but true.  Linux will swap only when its needed (or you can adjust the "swappiness" to fit your needs).

> Sorry to ask a Windows question here, 

I'm not a fundamentalist Linux pusher :)

> but you seem to know -- would it be better to give a smaller space to Windows for pagefile?  I gave it 80gb, and quickly found that it used that all up, so I reduced it to 20, which is still probably absurdly large...


Try setting it to ZERO. Seriously. With that much ram, it shouldnt have to swap at all. Taking away its swap space is the only way I know to prevent windows from doing silly stuff. Of course, if ever you would exceed the amount of RAM you have, you might have trouble (crash).

> But I do see my Windows system processes running up RAM pretty regularly.

I suspect what you see is windows allocating tons of memory for disk cache. Its what it does... it swaps an application to disk, thereby freeing up even more RAM to use as disk cache.  That works ok if you are RAM restricted, but it makes no sense when you multitask heavily with (too) much RAM.

---

### Post by timcredible on 2007-11-07
you can run ubuntu on a machine with more than 4GB of memory, it just won't use anymore than 4GB.  but i have to ask - what app do you think you can run that will use 4GB of memory?  i just opened 37 apps (including openoffice, firefox, gimp, and other 'big' apps, etc.) on my system with 2GB of RAM, and it's showing 1.02GB of RAM used and 0 swap space used (and I'm running an apache server on this machine).

---

### Post by P4man on 2007-11-07
> **timcredible said:**
> y but i have to ask - what app do you think you can run that will use 4GB of memory?  .

I think it is based on his misunderstanding of the numbers windows Taskmanager report. In windows, if you have a machine with say 4GB Ram and 12 GB swap, and you open just calculator, after some time it is possible windows will report >3GB Ram "in use".

In fact, windows will have something like 2.5 GB of RAM used as diskcache. He should have deducted that number (also reported by taskmanager I believe) to see how much RAM he is really using, because otherwise he might end up buying 64GB to run calculator.

BTW, if you then open notepad, there is a good chance windows will swap calculator to disk, rather than keeping it RAM, so it can increase its diskcache by 0.01% and making it 99.99% certain you will need to hit the harddisk again when alt+tabbing to calculator again. That is what makes windows so sluggish.. stupidity.

---

### Post by alicson on 2007-11-07
I don't know. I haven't played in Linux.

I do know that in Windows, even with just my basic programs running, MS Word or Excel, Firefox, Opera, Thunderbird (eats lots. I think it feels I have too much email), chat app, Media Player Classic, uTorrent, and if I'm not using Word/Excel then I'm probably using Photoshop and/or Illustrator, and Picasa is more regularly used as well, the RAM is usually enough but does seem to leak or shoot up (especially if I'm using Photoshop.. and Firefox slowly eats more RAM the longer that it's open, or so it seems).  Then there's smaller stuff, FTP app (can take a lot when running file transfers), Winamp, random background processes; Windows eats tons of everything when moving files from one drive to another, but that affects Processor usage even more.. I just know that in Windows, it shows me as running my RAM up (and javaw, which underlies several different apps, will often eat up everything and then I hardkill it (doesn't hardkill the apps I'm using, though). That happens very regularly).

Might all be much more stable and resource-efficient in Linux..--actually, I'm fully expecting it to be. Hence me being here ;)

Yes, I'm basing this generally on what task manager/other system-reporting apps tell me.  The pagefile/disk-swapping stuff is new to me, but I think I essentially understand it now (the general,practical theory of it).  My general feeling is that Windows has never given me reason to think it was balking at smaller apps, but when I was trying to copy and paste a huge amount of text (mysql export) it definitely balked a lot at that, and Photoshop likes to report that it's out of memory when it shouldn't be, and (according to task manager, where I should actually be subtracting 2.5gb?) Firefox likes to run up RAM especially after being open a while..I guess that's caching, though?  Right now, on office computer (1gb RAM), it's reporting Firefox as using 196368 K physical and 210792 K paged.  Process usage: 503308 K and 578024 Kb.  

..and I'm a she. 
   
 Thank you all, again.

---

### Post by P4man on 2007-11-07
A few things.. Photoshop "running out of memory"..  has 2 likely causes: 
1, your scratchdisks are full. Photoshop handles its own disk swapping to some extend, check that first (somewhere in preferences)
2) if you are working with HUGE files or with tons of layers, you might be running  into the 32 bit addressing brick wall. Adding more ram won't help you here, nor will larger swap files or scratch disks. In this case, a 64 bit OS might help a bit, but not that much unless Adobe brings out a 64 bit version of Photoshop (have they?)

as for firefox eating up more memory over time: AFAICT thats a memory leak. Bad programming.

As for interpreting windows taksmanager, its not that obvious. Look at the peformance tab, the  physical memory part.  in my (virtual) windows, I now see:
total ~668Mb (thats what I set in the VM)
available: 501Mb
cache: 237Mb

What this means (I think), is that only 167Mb RAM is being used (668-501) by applications and windows itselve. 237Mb  is used as disk buffer (cache). The rest of windows itself and applications have been swapped to disk.

---

### Post by hyper_ch on 2007-11-07
Just a thing:

2³² bytes are exactely 4GB

4 GB --> 2² GB --> 2² * 1GB


1024B --> 1KB
1024KB --> 1MB
1024MB --> 1GB
1024 --> 2¹°

--> 2² * 2¹° * 1MB

--> 2² * 2¹° * 2¹° * 1KB

--> 2² * 2¹° * 2¹° * 2¹° * 1B

--> 2³² B

---

### Post by Inxsible on 2007-11-07
> **hyper_ch said:**
> Just a thing:

2³² bytes are exactely 4GB

4 GB --> 2² GB --> 2² * 1GB


1024B --> 1KB
1024KB --> 1MB
1024MB --> 1GB
1024 --> 2¹°

--> 2² * 2¹° * 1MB

--> 2² * 2¹° * 2¹° * 1KB

--> 2² * 2¹° * 2¹° * 2¹° * 1B

--> 2³³ BThe last line should be 2^32.
 2+10+10+10 =32.

I am sure it was just a typo :D

---

### Post by hyper_ch on 2007-11-08
> **Inxsible said:**
> The last line should be 2^32.
 2+10+10+10 =32.

I am sure it was just a typo :D

Yep and fixed and thx ;)

---

### Post by jojo4u on 2007-11-30
Linux cannot use more than 3 GB RAM per process on a 32 bit machine (using the default CONFIG_VMSPLIT_3G=y).
But if your CPU supports PAE ([http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)) - which is very likely - you can use more than 4 GB RAM for the whole system.
You need a recompiled generic kernel with CONFIG_HIGHMEM64G activated or the server kernel (linux-image-server). Note: The server kernel is not tailored for desktop use and may not feel as responsive.
The generic kernel has PAE disabled since the first Pentium-M does not support it. This also means, that desktop Ubuntu has no hardware NX-bit support!

---

### Post by markyb86 on 2007-11-30
> **P4man said:**
> you are probably deliberately simplifying,  but the above is incorrect. Since the Pentium Pro, our cpu's have been able to address 36 to 48 bits of **RAM** (depending on the cpu). Do the math, its faaar more tthan  4GB. They have, however, been limited to 32 bit **virtual** address space (per process). Until AMD64 came along that is.

So there could have been Pentium Pro servers with say 64 GB RAM and a 32 bit OS. These worked fine if they ran many small workloads.  That same machine would have been able to process the exact same workload with just 1GB RAM, only MUCH slower. But such a machine could never load a 4GB app (/process) even if it had 64GB RAM; A 64 bit machine with a 64 bit OS would be able to load that 4+ GB workload even if it had only 1 GB physical ram.

Capiche ? 

:)
He was not incorrect, those servers probably had several processors, and the Server operating system dictates whether or not they can handle that kind of load just like xp can use 4gb and server 2003 can use 64gb, but thats only with [SIZE="7"]8[/SIZE] processors. Yeah it was a 32 bit OS but it wasnt end user

---

### Post by P4man on 2007-11-30
> **markyb86 said:**
> He was not incorrect, those servers probably had several processors, and the Server operating system dictates whether or not they can handle that kind of load

Slow down, you are mixing a lot of very different issues First off, whether the poster I replied was right or wrong, depends how you interprete this paragraph:
[I]
"That's why a 32 bit processor can only access 4GB or less. 64 bit processors however can access 2^64 bits = 18446744073709551616 bits ~= 16 exabytes ~= 16 billion GBt"[/I]

He doesnt specify RAM or virtual memory, but given he replied to a question about RAM, I assumed he claimed 32 bit processors can not access more than 4GB RAM, which is wrong. Pentium Pro could access 64GB RAM, Pentium III and 4 based Xeons (also 32 bit cpus) over 256GB RAM.

Now chipsets may limit that. I dont think there where any Pentium Pro boards that allowed enough RAM modules to ever handle anywhere near 64GB RAM, but that doesnt mean the CPU could not.

Then you add Operating systems to the mix. These may further llimit how much RAM you can make use off, but I don't see how that is relevant in this context. If I run DOS on my Core2Duo, surely you will not claim "64 bit cpu's can only handle 1Mb RAM" because for whatever reason I run DOS on it.

>  just like xp can use 4gb and server 2003 can use 64gb, but thats only with 8 processors.

I think you are wrong here. XP may be limited to 4GB, but again that is almost irrelevant. Its a (fairly logical) choice MS made, it has nothing to do with capabilities of the CPU. Windows Server 2003 enterprise edition, the 32 bit one, supports 32 GB RAM maximum. It also supports up to 8 cpu's but one is not related to the other. 

If someone would make a single 32bit CPU board with enough RAM sockets to accommodate 32 GB, windows 2003 enterprise 32 bit ought to work with it and use all 32GB. It wouldnt be very useful, since you'd need many 2 or 3 GB apps or processes to make use of that much RAM, running on just 1 cpu makes not much sense, but it should work.

If it doesnt work on windows, its just another microsoft anomaly, Unix/Linux systems would work just fine with such a config as long as they support PAE: physical address extension, the way 32 bit x86 CPU's are able to access >4GB Ram (even though they can only work with 4GB of virtual memory per process).

---

