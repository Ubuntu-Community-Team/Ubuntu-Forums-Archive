---
title: "How much swap?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-08-30
Ok I am going to be putting Ubuntu on an 80GB hdd and I was wondering how much of that should be swap space?

Another question is what is the swap space for?

Thanks for your help in advance.

Paul

---

### Post by crackseller on 2006-08-30
Swap space is an extension of your ram. As soon as your ram is "full" the kernel will use the swap space to store important data. 
As you can see swap depends on your amount of ram you got. The more ram you got the less swap you need (if at all). I myself got 1GB of ram and went for 512mb of swap which is more than enough. With a 80GB harddrive you can easily affort to have more swap than you need. I went for 512MB as this is the (conservative) usual swap space.

---

### Post by bruce89 on 2006-08-30
If you want to hibernate the computer, you need at least the same amount of swap as you have RAM.

---

### Post by PPAAUULL on 2006-08-30
I was looking on a website and it said to do 2 times your RAM and even that can not be enough.

Oh and I have 1gb of ram

Paul

---

### Post by bruce89 on 2006-08-30
> **PPAAUULL said:**
> I was looking on a website and it said to do 2 times your RAM and even that can not be enough.

Oh and I have 1gb of ram

Paul

Look at System Monitor though, you will find no or very little swap usage.  Mine is 0MiB used at the moment.

Strange thing is that Linux seems to cache a lot of the disk to RAM, which is revealed with *top*.  800MiB (approx.) of my 1GiB is being used just now.  Linux doesn't put disk cache onto the swap though, as that would be pointless.

---

### Post by PPAAUULL on 2006-08-30
Ok Thanks for the help.

Paul

---

### Post by Sef on 2006-08-30
With 1 GB ram, you generally don't need any swap unless you are doing heavy gaming or photo (especially video) editing.

---

### Post by crackseller on 2006-08-30
> **PPAAUULL said:**
> I was looking on a website and it said to do 2 times your RAM and even that can not be enough.

Oh and I have 1gb of ram

Paul
I know of this rule and it used to be valid back in the days when 128MB of ram was a luxury. In my opinion with modern systems (and ram in the gigabytes range) this just doesn't apply anymore, maybe except for when it comes to hibernating. That, however, I didn't know of as I do not use the hibernating feature.

---

### Post by PPAAUULL on 2006-08-30
Ok Thanks.

---

### Post by PPAAUULL on 2006-08-30
I am not going to use that feture either so I think I am set. Besides if I over gague the swap then I have a lot of space left, so I am not worried.

---

### Post by huygens on 2006-08-30
Swap space is what is called page file under Windows (in case it happens that you know about it...), it is the [virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory") of the system. When you happen to be short of memory, the OS will use this virtual part.

Typically, a user would like to use twice the amount of main computer memory ([RAM]("http://en.wikipedia.org/wiki/RAM")) for its swap space. And at least greater strictly than the amount of RAM. Why? [For hibernation you need a swap larger than the RAM]("http://www.linux.com/article.pl?sid=06/07/26/1641234").
[Microsoft recommends a minimum of 1,5x]("http://support.microsoft.com/kb/308417/#31") to a maximum of 3x the amount of RAM.

Huygens

---

### Post by PPAAUULL on 2006-08-30
Ok I think I got it now. Thanks for the info though.

---

### Post by The Seeker on 2006-08-30
When I installed Ubuntu it automatically gave me 5.8 GB of swap space; I have 2 GB of RAM incidentally.

---

### Post by PPAAUULL on 2006-08-30
does it do the swap space automaticly? or do I have to set how much?

---

### Post by bluenova on 2006-08-30
For modern systems with 1GB or more of RAM I think 1GB of Swap is sufficent no matter how much RAM the system has.

For older machines, I always use double the RAM so...
128Mb RAM = 256Mb Swap
256Mb RAM = 512Mb Swap
512Mb RAM = 1Gb Swap

---

### Post by PPAAUULL on 2006-08-30
Sounds like a good rule. I think I will use it.

---

### Post by bruce89 on 2006-08-30
> **The Seeker said:**
> When I installed Ubuntu it automatically gave me 5.8 GB of swap space; I have 2 GB of RAM incidentally.

That must be a large hard disk, as I think it allocates a amount just above the RAM size, but if the disk is big enough, a percentage of the disk size.

---

### Post by The Seeker on 2006-08-30
> **bruce89 said:**
> That must be a large hard disk, as I think it allocates a amount just above the RAM size, but if the disk is big enough, a percentage of the disk size.

Well I have two separate HDDs, each 150 GB.

I have a look at the swap sometimes in the system monitor and it's usually untouched, although I've seen it used a few times.

---

### Post by PPAAUULL on 2006-08-30
neat I never knew that. I just used the swap from my linux distro before which was 1gb on a 15gb partition

---

### Post by jdong on 2006-08-30
Please don't waste ridiculous amounts of disk space dedicated to swap... if you're gonna do that, send that hard drive to me and I'll gladly give you a smaller one in return :)


The truths regarding swap are:

(1) If you plan on hibernating (read: if you're lucky enough that it works :-/), you need at least your RAM size in swap. I'd actually recommend 1.5x your RAM in swap, as I've seen cases where it requires that much.

(2) If you are not hibernating, then start with conservatively small amounts of swap.

(3) If you have relatively low amounts of RAM (512 or below), you  should have around 500MB of swap or so, as opening a few large programs (openoffice, firefox on its memory rampages) could use up all your RAM.

(4) If you have large amounts of RAM (512+), then you should only need around 256MB or so of swap just in case you need that overflow.


If you are allocating GB's of swap, chances are you'll never use it. The highest swap usage I've seen on my systems is about 100MB, and that forced it to be dog slow, so I doubt your system would be usable if you had to be using 1GB of swap :)


Remember that (except if you are hibernating) it is always possible to add more swap via "swap files" later on, but it's more difficult to reclaim swap partition space as storage space.

---

### Post by PPAAUULL on 2006-08-30
Ok Thanks

---

