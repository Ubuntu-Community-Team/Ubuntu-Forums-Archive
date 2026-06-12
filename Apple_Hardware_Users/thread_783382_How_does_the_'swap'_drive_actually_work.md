---
title: "How does the 'swap' drive actually work????"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-05-05
I was wondering about the Linux swap partition drive.

So, it uses hard drive space as memory. Does this mean that if I had a 100GB hard drive and used 90GB for swap, that this computer will run decently fast???

---

### Post by Whiffle on 2008-05-05
It only uses it as a last resort, because hard drives are _much_ slower than actual memory.  I notice a pretty big slowdown if/when my computer starts using the swap.  Most of the time it doesn't need it though.

---

### Post by solitaire on 2008-05-05
your Swap drive only needs to be twice as (or 2.5x) the physical RAM in your box.


i.e. if your box had 2Gb of RAM then the swap partition should be 4Gb or 5Gb in size. Anything bigger would not improve performance.

---

### Post by russo.mic on 2008-05-08
I've got 2 GB of RAM in my MPB, and I'm not even using a swap, and I never seem to have any problems.  

When the swap partition/file was invented, 2MB of ram was unthinkable.  I think it made alot more sense then.  But RAM is cheap.  

Really, you DON'T want your computer using the swap file if you can help it.  I've always heard it's good to use a swap file/partition as BIG as your ram, not 2.5 times.  I can't understand why you'd need that much space dedicated for 2.5 times Ram,  Although I could be wrong.

Russo

---

### Post by brigux on 2008-05-08
[http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)

---

### Post by Linux&amp;Gsus on 2008-05-08
I got a question related to that as well.

I never fully understood the need of a SWAP partition. It's needed when there is not enough RAM available. OK, I understand that. But what else is it really doing?
I checked a server in the office the other day that used (at the end of the day) around 250-300MB RAM, no SWAP was used so far. The next morning RAM usage didn't change but a few MB SWAP was used. The system has 4GB RAM. Why was the SWAP used with still tons of RAM available?

Another question that I have is what happens when I suspend to disk. Is the SWAP partition used to save the data from the RAM? If so, what if there is not enough space available for RAM + potential SWAP usage?
If not, where is the data saved to?

Which then also leads me to the question, how can SWAP increase the performance of systems that has plenty of RAM (2GB+). Assuming that it's not a computer that is used for RAM intensive work like video editing, etc. I would guess that someone doing that has "enough" RAM according to his needs, anyways.
So, with enough RAM, why wouldn't it be enough to have rather little SWAP, e.g. 300MB?

The last question that bugs me since a while is, since HDD's are rather slow, would it be possible to use a USB FlashDrive as SWAP partition? Would that increase the performance?

---

### Post by brigux on 2008-05-08
Quite simple. When the processor is requesting some data, it looks for it first in its lvl1 cache (very small, very fast access, usually contains only simple instruction), if not here it will look for it in the lvl 2 cache, if not, RAM, if not, swap, if not HDD... as you can see each operation is accessing a lower media at each stage.. that also why the swap should not be too big or then the system will spend too much time looking for the info.
Now to answer your question, the flash drive might be much slower than the HDD, hence using it for swap will decrease performance.

---

### Post by Sunspark on 2008-05-08
If you're using a laptop keep this in mind:

1) To hibernate your system you MUST have a swap partition slightly bigger than your ram. I have 4 gigs of ram, so I must have a partition between 5-8 gigs in size.

2) Swapfiles cannot be used for hibernate, so if you have a laptop don't use a swapfile.

3) If you know you aren't going to be hibernating then you can use a swapfile and it will be just as fast as a swap partition.

Hibernating is when you suspend your system to DISK and the computer power offs.

OS X system sleep default is a combo. It suspends to ram, AND hibernates it to disk 'just in case'. I got sick of waiting for it to write 4 gb to disk every time I slept the machine, so I changed it to just suspend to ram.

Swap is also a place used to store ram that is 'occupied' but isn't being used or called for whatever reason.. so why not shuffle it off to the back of the bus to free up the good seats for the paying customers? You get the idea. Think of it as a caching.

---

### Post by russo.mic on 2008-05-09
I have no swap partiton or file and my laptop hibernates just fine...


Russo

---

### Post by grim4593 on 2008-05-09
> **Sunspark said:**
> 2) Swapfiles cannot be used for hibernate, so if you have a laptop don't use a swapfile.
This is not true!
You can still hibernate if you have a swapfile. There is just an extra step you have to take in order to get it to work.

You have to find out where the swapfile resides on the system by looking up it’s FIRST SECTOR:
sudo filefrag -v /swapfile

Then add "resume=/dev/sdx resume_offset=xxxxxx" to the kernel boot options in /boot/grub/menu.lst, where /dev/sdx is the partition with the swapfile on it and xxxxxx is the first sector the swapfile starts at.
Ex: kernel		/vmlinuz-2.6.24-17-generic root=UUID=021e7fc9-ee7e-49ac-b9f1-2a084d229512 ro quiet splash resume=/dev/sda3 resume_offset=350624

And then so grub automatically adds the offset to future kernels add it to the end of this line: 
# defoptions=quiet splash resume=/dev/sdax resume_offset=xxxxxx

---

### Post by ssam on 2008-05-10
> **Linux&Gsus said:**
> 
I never fully understood the need of a SWAP partition. It's needed when there is not enough RAM available. OK, I understand that. But what else is it really doing?
I checked a server in the office the other day that used (at the end of the day) around 250-300MB RAM, no SWAP was used so far. The next morning RAM usage didn't change but a few MB SWAP was used. The system has 4GB RAM. Why was the SWAP used with still tons of RAM available?
[QUOTE=Linux&Gsus;4909892]

On linux (and any other sane operating system) free ram is used as disk cache. The first time you read a file it takes a long time because you have to read it from the disk. When you read it a second time, it is already in the cache so it is fast. (this is why openoffice starts much faster the second time you open it).
So the more free RAM you have the more disk cache you have.
If you have a program loaded into memory, but you are not using it, it is still using up memory. Or a program may have leaked some memory, so it is allocated, but never accessed by that program. If the OS can move this memory onto the swap space, then there is more RAM free to do useful things with.


Another question that I have is what happens when I suspend to disk. Is the SWAP partition used to save the data from the RAM? If so, what if there is not enough space available for RAM + potential SWAP usage?
If not, where is the data saved to?
> **Linux&Gsus said:**
> 

I have wonder about this. I imagine the hibernate must fail. 


Which then also leads me to the question, how can SWAP increase the performance of systems that has plenty of RAM (2GB+). Assuming that it's not a computer that is used for RAM intensive work like video editing, etc. I would guess that someone doing that has "enough" RAM according to his needs, anyways.
So, with enough RAM, why wouldn't it be enough to have rather little SWAP, e.g. 300MB?
[/QUOTE]

it depends what you want to happen when a program goes crazy and grabs a vast amount of ram. when you run out of memory the kernel starts killing processes that it thinks might be responisble.

If you have lots of swap, then there is a lower chance of getting to the out of memory case. however if the program is going to keep grabbing memory for ever, then you might do better to quickly hit out of memory, the kernel to kill stuff, and then reboot and get going again.

> **Linux&Gsus said:**
> 
The last question that bugs me since a while is, since HDD's are rather slow, would it be possible to use a USB FlashDrive as SWAP partition? Would that increase the performance?

hard disks still win for transfering large amounts of data. so it would depend on your usage pattern. if you get a 50MB/s flash disk, then it would probably beat most hard disks. a cheap pen drive will not be that fast.

---

### Post by munozga on 2008-05-11
> **Linux&Gsus said:**
> I got a question related to that as well.

I never fully understood the need of a SWAP partition. It's needed when there is not enough RAM available. OK, I understand that. But what else is it really doing?
Using swap space for insufficient memory is one reason for its existence, another is to have the capability to "swap" out memory that doesn't get used often (the latter reason is likely to take effect on longer running systems).

> I checked a server in the office the other day that used (at the end of the day) around 250-300MB RAM, no SWAP was used so far. The next morning RAM usage didn't change but a few MB SWAP was used. The system has 4GB RAM. Why was the SWAP used with still tons of RAM available?
This is an example of swap space being used to purge infrequently used pages from physical RAM. You pointed out that it happened over night, so the system was doing something that caused it to notice that some pages weren't used at all and it swapped them out in favor of some other memory (probably related to the cache usage).

BTW, did you notice how much of the 4GB of RAM was used **including** the cache? You have to think about cache usage as well when understanding the use of swap, not just resident memory (or virtual, etc, etc). Cache usage gets printed out with `free' as well. It's an important thing to make note of.

> Another question that I have is what happens when I suspend to disk. Is the SWAP partition used to save the data from the RAM? If so, what if there is not enough space available for RAM + potential SWAP usage?
If not, where is the data saved to?
Well, this is a case where you would want to have more swap space than you have memory (I think it would fail if you don't have enough space, but I'm not sure, never thought to try). IIRC, it is common to store the contents of physical memory in swap space when hibernating, but not necessary (it's configurable, but simpler to just use swap).

> Which then also leads me to the question, how can SWAP increase the performance of systems that has plenty of RAM (2GB+). Assuming that it's not a computer that is used for RAM intensive work like video editing, etc. I would guess that someone doing that has "enough" RAM according to his needs, anyways.
To the kernel, there is no such thing as having "plenty of RAM". An operating system is only operating at peak performance when it is using all of physical RAM (minus a little bit for kernel emergencies, such as running out of memory). Even if you have enough RAM for your workload you will notice the rest of memory gradually creeps up to near 100% utilization because it is a waste of space not to use it (not to mention money), and performance can be improved by caching frequently used files (even if they aren't in use). Thus, the longer you run a system, the better it performs--well, it's supposed to anyway :). This is also why more RAM can really help web servers and file servers (things that just dish out files) because more of those files can be cached, even if they don't really need to be cached, and even if you have plenty of RAM.

(Want to see this phenomenon in action, execute a complex `find' command on a large amount of files. Then do it a second time. Time each run and take snapshots of memory utilization before and after. Try to rationalize what you see, if you can't then keep asking questions. Now repeat the experiment while also compiling a kernel. Still understand?)

So not using swap space is OK if you have the memory, but it can degrade memory utilization by keeping pages resident that don't have to be resident at the cost of cache (or the like--it gets complex quick). BTW, this is the type of "performance" improvement that might be undetectable to users, especially if you don't know how to realize its effects **throughout** the system.

> The last question that bugs me since a while is, since HDD's are rather slow, would it be possible to use a USB FlashDrive as SWAP partition? Would that increase the performance?
Flash drives can be used like any other file system, so I imagine they can be used for this purpose. In fact, I'm sure they are used for that purpose. Look at the laptops that are out there now! And yes, it would then be faster, but still much slower than RAM, and in the case of out-of-memory, you'd still be hurting in the same ways (disk swappiness, etc). Only RAM can replace RAM :)

---

### Post by Linux&amp;Gsus on 2008-05-11
Thanks guys for all the explanations. That helped a lot.
I guess I understand the concept of caching files and that the RAM is used for that. I just wasn't too sure about all aspects of SWAP. E.g. I somehow would have expected that it would rather purge the cache than using SWAP.

But now I feel enlightened. *Bows down*

Cheers,
Steve

---

### Post by ssam on 2008-05-11
for got to mention. flash drives, have limitted write cycles. the problem is not as bad as it used to be.

If you were hitting swap regularly, then the life og the flash driver may be reduced to something on the order of a few years. for a server that may not be acceptable. for a home system it should be fine.

---

### Post by Linux&amp;Gsus on 2008-05-11
Right the limited write cycles. But I never thought of the flash drives as a server solution, rather to re-use older ones for a desktop, instead of using up HD space.
However, since the speed seems to not be as good as I thought it might not be the smartest idea.

Cheers,
Steve

---

