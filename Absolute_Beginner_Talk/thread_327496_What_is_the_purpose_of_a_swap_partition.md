---
title: "What is the purpose of a swap partition?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Achetar on 2006-12-29
I am dual booting Windows XP and Ubuntu, and i want to know what the purpose of a swap partition is. I have it about 80MB larger than my ram (my ram is about 700MB) and if there is no use for it, then i want to remove it.

Also, I want to know how to get it so I can use standby in Windows and Suspend in Ubuntu. Is it just because i have multiple partitions that i cant use it?

:confused:

---

### Post by Asham on 2006-12-29
To my understanding a swap partition is used by the operating system as extra RAM when the RAM is used to its capacity. Correct me if I'm wrong.

---

### Post by bulldog on 2006-12-29
The swap is the same as the windows page file,and substitute RAM if there's no more physical  RAM available.

Standby  and hibernate must be supported by your hardware to get it working.
Keep in mind standby will keep the current status into memory,if there's short of memory it probably won't work.

Hibernate will write the status on hard disk,in the swap if I'm not mistaken,to small swap file will be spoiling things for you too.

---

### Post by moshuptrail on 2006-12-29
swap is used by linux when there are dormant programs in memory and it needs memory to do something you want.  It "swaps" them out to an area of hard drive.  Generally people suggest 2x system memory.  That's pretty small in disk space terms.
Windows has the same thing.  It uses a large hidden file (I think it might even be called swap32-it's been a while) on your C:\ drive.

Using standby, suspend, or even hibernate, is always problematic when you are attached to a network.  Things that expect to periodically keep in touch (ET phone home), don't, and you loose connections.  If that's not a problem, there is no reason partitions should interfere.  I use hibernate a lot (Ubuntu) and it works great.  Usually my gaim client complains bitterly when I restart, but I tell it to wake up and smell the coffee.

---

### Post by anaconda on 2006-12-29
If you dont want to make a separate partition for swap, you can use a swap-file instead. (like windows)

---

### Post by ron999 on 2006-12-29
> **anaconda said:**
> If you dont want to make a separate partition for swap, you can use a swap-file instead. (like windows)

I don't understand that? :-k

---

### Post by anaconda on 2006-12-29
> **ron999 said:**
> I don't understand that? :-k

I meant that you can make a swap-file instead of a swap partition if you want. I think that swap file is better, because you can change the size of your swap file easily if you need more swap.

Here is instructions howto make swap files:
[http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap](http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap)

And if the dd -copying bug is still around here is a workaround:
[http://www.ubuntuforums.org/showthread.php?t=168465&highlight=lang+dd+segfault](http://www.ubuntuforums.org/showthread.php?t=168465&highlight=lang+dd+segfault)

---

### Post by IanGB on 2006-12-29
The problem is that it is only when things slow down that you realise a larger swap file is required. My advice is is leave it alone. Is your hard drive space limited so you urgently need the space?

---

### Post by az on 2006-12-29
You can't hibernate (suspend-to-disk) without a swap partition - you can't do that with a swap file.

> **Achetar said:**
> 
Also, I want to know how to get it so I can use standby in Windows and Suspend in Ubuntu. Is it just because i have multiple partitions that i cant use it?


By Standby and Suspend, you mean suspend-to-ram?  In that case, your computer does not really turn off.  It only stays in a very low-power state, keeping your ram in use.  When you wake up, (resume) it's as though you never shut down.

Susped-to-disk (hibernate) writes the contents of your ram to disk.  Ubuntu uses the swap partition to do this - your swap must be about 25 per cent bigger than the amount of ram you have to do this.  Windows does not use any other partition for this.

Exactly what is not working for you?

---

### Post by anaconda on 2006-12-29
hmm.. 
and why cant you hibernate using a swap file?

It is mounted just like a swap partition. I can't see any difference.

Yep. I have heard that before. But wont believe before I try it myself.
Just have to find some extra time...

---

### Post by Frak on 2006-12-29
Free up RAM, and yes Windows does have a swap partition, its kept within the boot records.
EDIT
swap file, not partition

---

### Post by Sef on 2006-12-29
> Free up RAM, and yes Windows does have a swap partition, its kept within the boot records.

It's a [swap file]("http://www.pcnineoneone.com/howto/swpfile1.html").  Not a partition.

---

### Post by Frak on 2006-12-29
> **Sef said:**
> It's a swap file.  Not a partition.
Ment to say file, I was just saying they have a swap, I sounded really stupid just then, contradicting myself.

---

### Post by Sef on 2006-12-29
> Ment to say file, I was just saying they have a swap, I sounded really stupid just then, contradicting myself.

Wondered what was up.   No worries, we all do that at times on here.

---

### Post by smoker on 2006-12-29
is there any speed benefit using a swap file, rather than a swap partition?

also, any suggestions about the best position in a drive to place a swap partition, i have mine in the middle of the drive?

---

### Post by az on 2006-12-29
> **smoker said:**
> is there any speed benefit using a swap file, rather than a swap partition?

also, any suggestions about the best position in a drive to place a swap partition, i have mine in the middle of the drive?

A swap file is slower.  There is no benefit to using the beginning or the end of the drive.  There is no way to predict what would result in your drive head seeking the least.

> **anaconda said:**
> hmm.. 
and why cant you hibernate using a swap file?

It is mounted just like a swap partition. I can't see any difference.

I think it's a limitation on the  current implementation.  This happens at the kernel level - it's not just something you hack into your init scripts.

---

### Post by Achetar on 2006-12-30
I am not very limited in terms of HD space. Is the swap partition similar to the virtual memory in windows?

Hibernate and standby dont work in windows, suspend doesnt work in Ubuntu, and i havent tried hibernate. Do i need double Ram size (in my case about 1.4GB)? i have about 780 MB of swap space, which is about 80MB more.

I never realized this would spark such a big discussion.

---

### Post by az on 2006-12-30
> **Achetar said:**
>  Is the swap partition similar to the virtual memory in windows?

It's similar.  From what I can understand about it, Windows virtual memory is just a page file.  That means that when one application is using ram for variables or something, but that application is not needed at the moment, that ram can be stored there temporarily.

A swap does both paging and caching.  Caching to swap is beneficial when something takes a relatively long time to set up into ram - like starting OpenOffice, for example.  To start it from scratch can take a few seconds.  To retreive it from cache would take a lo tless time.

Don't ask me any more details about that, I dunno.


> **Achetar said:**
> 
Hibernate and standby dont work in windows, suspend doesnt work in Ubuntu, and i havent tried hibernate. 
Some (many?) machines cannot suspend-to-ram.  That's a hardware thing.

> **Achetar said:**
> Do i need double Ram size (in my case about 1.4GB)? i have about 780 MB of swap space, which is about 80MB more.


AFAIK, you need twenty-five percent more swap space than ram.  So you would need about one gig of swap.  Hibernation on linux works, but it is relatively new.  There are bugs.  If your machine cannot hibernate, please file a bug or add to an existing one.  Sometimes, just knowing that it doesn't work on a particular motherboard is helpful to the developers...

---

### Post by Achetar on 2006-12-30
I have XP standby and Hibernate working, the VMemory was not big enough. I tried in Ubuntu, but still no luck the errors disapeer before i can read them. I have an ATI Radeon IGP 330M/340M/350M

---

### Post by jdong on 2006-12-30
> **azz said:**
> It's similar.  From what I can understand about it, Windows virtual memory is just a page file.  That means that when one application is using ram for variables or something, but that application is not needed at the moment, that ram can be stored there temporarily.

Windows virtual memory pagefiles and Linux swap are basically the same thing, by different names. The main notable difference is Windows creates files on your system partitions for that, while Linux likes to dedicate a partition for it (but does also support swapfiles). Lesser-used applications are swapped out from RAM to swapfile to make room for other files.

> 
A swap does both paging and caching.  Caching to swap is beneficial when something takes a relatively long time to set up into ram - like starting OpenOffice, for example.  To start it from scratch can take a few seconds.  To retreive it from cache would take a lo tless time.

Don't ask me any more details about that, I dunno.

Kind of :). There's two reasons (pressures) to swap:

(1) To make more RAM available to a newly launched application demanding more than currently free.
(2) To make more RAM available to the disk cache, if Linux strongly believes that it can accelerate disk performance by shoving more apps into the cache.

You can influence #2 by adjusting "sysctl vm.swappiness", but I don't recommend touching it unless you are a power user who knows for sure this is needed. Majority of the time you'll just make performance worse.

> 
AFAIK, you need twenty-five percent more swap space than ram.  So you would need about one gig of swap.  Hibernation on linux works, but it is relatively new.  There are bugs.
There's no rule-of-thumb for this kind of thing. It depends on your work habits. For many people, during the course of normal work swap is not used at all... this is a good thing. Anytime swap is actively utilized your system will feel very slow and laggy.

However, swap lends a wonderful help when you need to run that one program or two that uses a large amount of RAM. If you run out of RAM+swap to house that program, a kernel routine called the OOM (out of memory) Killer is activated, and it will choose the most resource-intensive process and instantly kill it. No user ever wants to come face-to-face with this gremlin, so have some swap around :)


Another interesting anecdote, I use swap for something called "tmpfs", which is like a RAMDrive that uses both RAM and swap, when I do my Backports compiles, because to ensure a clean building environment it builds a 100MB Ubuntu setup and destroys it between every packages. This is usually very disk-intensive and tmpfs alleviates a lot of that. However, it means I need to have around 5GB of swap to build those big packages!

---

### Post by az on 2006-12-31
> **jdong said:**
> 

There's no rule-of-thumb for this kind of thing. It depends on your work habits. 

I was refering to suspend-to-disk (hibernation).  I am not up-to-date on the latest kernel, but AFAIK, hibernation will try to write to swap even if there is not enough room in the swap;  it does not tend to fail gracefully when it fails.

---

### Post by jdong on 2006-12-31
> **azz said:**
> I was refering to suspend-to-disk (hibernation).  I am not up-to-date on the latest kernel, but AFAIK, hibernation will try to write to swap even if there is not enough room in the swap;  it does not tend to fail gracefully when it fails.
Ah, ok, sorry, misread that.

Usually yeah, 1.5-2x RAM is required in a worst-case s2d scenario, depending on how much RAM you were using at the moment.

---

### Post by Achetar on 2007-01-01
Aright, i found the error. It says:
*Cannot Find swap space*
Any way to set where my swap space is?

---

### Post by az on 2007-01-03
How did you install?  Have you created any partitions since then?

Your swap is mounted at boot time.  Your mountpoints are in /etc/fstab.

like this:

/dev/hda5       none            swap    sw              0       0

---

### Post by bobpur on 2007-01-03
Just my 2 cents here...  Why don't you get a low capacity hard drive (4 gb or so) and format it as "linux swap" and set it up as dedicated swap on its own drive? I understand this is faster than having swap on  the same drive as you OS and it, also, recycles one of those old drives that have been cluttering up your "junk drawer."
This also works for Windows, but I'm not sure how you set it up.

---

### Post by iampoch on 2007-01-03
here's a question:

I've recently upgraded my ram from 512mb to 1024mb.  I dual-boot in WinXP and in that OS the only thing I have to do is to reconfigure the page file to 2.5x my current ram, so i set it to 2560mb.  I wanted to do a similar upscaling to the swap partition but I don't know how to do it.  I tried Partition Magic but it didn't work for some reason.  How do I upscale the swap partition?

---

### Post by insane_alien on 2007-01-03
for resizing the swap partition you have to have it unmounted. this means using the liveCD. you'll also need to make sure that there is enough space for it to expand into. but, you probably won't ever need the additional space since you have extra RAM.

---

### Post by jdong on 2007-01-03
iampouch, that is a lot of swap already and I don't think you'd really need any more unless you need to suspend-to-disk.

---

### Post by kinematic on 2007-01-03
there's no real difference between a swap file/partition.
they both take up space on the harddrive,just at different locations ;)

---

### Post by jdong on 2007-01-03
Except:

(1) swap file can fragment while a swap partition can't
(2) Swap partitions bypass the filesystem read/write layer which will improve performance


In either case, if you are trying to squeeze any performance out of swap, there is something serious wrong and you should really wonder to yourself why you are depending on swap so much that speed counts ;-)

---

### Post by iampoch on 2007-01-03
Thanks people, so resizing my partition will not be much of a concern :) hmm i guess that is a lot of RAM already :)  Ubuntu isn't memory-hungry as WinXP.  I upgraded my ram because the 512mb always put my xp to a crawl. I dread to imagine how much more awful it'll be for Vista :(

---

### Post by Achetar on 2007-02-05
Aright, I have not created new partitions since the install. Though i have edited the size of the WinXP and swap partitions. Also, every time I boot into windows, it seems to reformat the swap from Linux-swap the blank nothingness. Is there a way to fix that?

---

### Post by az on 2007-02-05
> **Achetar said:**
> Also, every time I boot into windows, it seems to reformat the swap from Linux-swap the blank nothingness. Is there a way to fix that?

That does not make sense.  What do you mean?

---

### Post by Frak on 2007-02-06
> **az said:**
> That does not make sense.  What do you mean?
I think he means **to** blank nothingness.

---

### Post by Achetar on 2007-06-11
Originally, I formatted the Swap Partition as ext2, when I boot into windows, it reads it as unformatted, when I reboot into Ubuntu from that, it doesn't mount until I reboot (again) then in Ubuntu it appears as ext2 until I boot into windows again.

Also I know that (at least under Windows) my hardware is able to Suspend/Hibernate. But when I do Hibernate then reboot into Ubuntu it says that the File System has errors, finds out it doesn't and then reboots (again).

:confused:

---

### Post by Nekiruhs on 2007-06-11
> **Achetar said:**
> Originally, I formatted the Swap Partition as ext2, when I boot into windows, it reads it as unformatted, when I reboot into Ubuntu from that, it doesn't mount until I reboot (again) then in Ubuntu it appears as ext2 until I boot into windows again.

Also I know that (at least under Windows) my hardware is able to Suspend/Hibernate. But when I do Hibernate then reboot into Ubuntu it says that the File System has errors, finds out it doesn't and then reboots (again).

:confused:
Windows doesnt touch the data in swap, its cleared evey time you reboot, just like ram. Swap must be formatted linux-swap.

---

