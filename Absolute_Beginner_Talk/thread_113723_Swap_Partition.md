---
title: "Swap Partition"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-07
Just curious as to why you need to set up a swap partition when first installing ubuntu.

---

### Post by Mission 10 on 2006-01-07
Being a new user I am under the understanding that it acts as "Virtual Memory" does in Windows based OS's. Reduces ram usage.

---

### Post by Mustard on 2006-01-07
Swap is used to swap out memory to the hard drive, when memory usage is excessive.  That's my take on it anyway. :)

---

### Post by shadesfox on 2006-01-07
A swap partition is just what the others said, extra memory.  IE if you have 512 megs of ram and a 1.5 gig swap partition you get 2 gigs of memory.  It is equivelent to the windows page file, except it is not resizeable, but it is faster.

---

### Post by diggs on 2006-01-07
gotcha. cuz I have one of those fancy desklets that allows me to monitor all this memory business, and the swap space is never used. I made it 2 gigs, I have 1 gig of ram. Thanks!

---

### Post by banadushi on 2006-01-07
Just a word to the wise, when you start hitting swap (>100M used) you need to either not hit your box so hard or invest in some more RAM.  Since disk access is inherently slower than ram access the paging out to swap can criple an otherwise beefy system.

Its normal for a box to sometimes dip a little into swap, and because of Linux's memory management, its not freed immediatly.  Meaning if a box hits swap for like 1M of memory, then some ram free's up, the swap is still considered part of the availible memory area (I'm pretty sure that it is however weighted so that the box prefers area's availible in RAM over those availible in swap, however I can't verify that for a fact right now).

The old school rule, when RAM was more expensive, was to make swap at least double the RAM, and systems were expected to page out to it quite often.  Now since RAM is relativly cheap, I usually choose a very small, oftem 512M of swap on a partition.  Just enough to get by, and if needed you can always create a file on the filesystem and add it into the swap space until you can get more RAM into the box.

I like to tell customers that swap is like insurance, you hope to never use it, but if you need to its there.

Have a good one!

Jason

PS.  Technically a box with the 2.6 kernel can exist without swap at all and be expected to deal with it quite well.  But then again some people also drive without insurance.

---

### Post by OlineSixtyOne on 2006-01-07
I have 1 GB of RAM. Would it be allright if I didn't have a swap partition at all?

Sorry to hijack thread, but I searched and found this, so I saw no reason to start another thread.

---

### Post by diggs on 2006-01-07
I dunno, cuz when I was doing all my setups, things got really pissy when I didn't have the swap space, to the point where ubuntu wouldn't install. give it a shot though, it could have just been my laptop...

---

### Post by banadushi on 2006-01-07
[QUOTE=OlineSixtyOne]I have 1 GB of RAM. Would it be allright if I didn't have a swap partition at all?.[/QUOTE]

Well you could.  But it really all depends on how you plan to use the box.  For a general workstation I like to err on the safe sides of things and I have a 512M swap partition on my box with also has 1G of RAM. 

Once you are out of memory Linux will start killing off proccesses, so if I'm editing video, I'd really hate it to kill off Kino while I'm using it.  When I said it could deal quite well with no swap at all, I meant that it won't Kernel Panic (lock hard and need a power cycle), like in the olden days, but it will kill off memory hungry proccesses.

If you didn't create a swap partition and down the road you find out that you need to have a little swap to dip into now and then, you can use a swap file instead of a partition.  Just do as root:

[code]
# dd if=/dev/zero of=/swap.1 bs=1024k count=512
# mkswap /swap.1
# swapon /swap.1
[\code]

This will then give you 512M of swap space until you can free up some RAM.  You can then disable the swap file by doing:

[code]
# swapoff /swap.1
[\code]

Have a good one!

Jason

---

### Post by banadushi on 2006-01-07
[QUOTE=diggs]things got really pissy when I didn't have the swap space, to the point where ubuntu wouldn't install.[/QUOTE]

Yea, the installer will throw a hissy fit, you have to use expert mode or create swap on LVM, then after all is done, you can delete the swap volume group and reclaim the space.

For what most people use Ubuntu for, they will want at least a little swap, for insurance and ease of install.

Have a good one!

Jason

---

### Post by towsonu2003 on 2006-01-07
to complicate things, on my 1GB RAM + 2GB Swap, I sometimes use 10-20 MG swap while 75% of RAM is empty... So I would put in a swap in there just in case :)

---

### Post by newuser111 on 2006-01-07
even if you have a gig of memory its still a good idea to have at least 512mb of swap because if you load so many programs it will error out rather than load into swap

---

### Post by UncleBulgaria on 2006-01-07
[QUOTE=banadushi]
If you didn't create a swap partition and down the road you find out that you need to have a little swap to dip into now and then, you can use a swap file instead of a partition.  Just do as root:

[code]
# dd if=/dev/zero of=/swap.1 bs=1024k count=512
# mkswap /swap.1
# swapon /swap.1
[\code]

This will then give you 512M of swap space until you can free up some RAM.  You can then disable the swap file by doing:

[code]
# swapoff /swap.1
[\code]

[/QUOTE]

Sorry to ask a newbie question, but what do you use to enter the above?

Robert.

---

### Post by piedamaro on 2006-01-07
In a terminal.

---

### Post by Mustard on 2006-01-07
[QUOTE=UncleBulgaria]Sorry to ask a newbie question, but what do you use to enter the above?

Robert.[/QUOTE]

The terminal or command line interface can be found in the Applications>>Accessories menu if you have Breezy Badger installed.

---

### Post by Efrain Valles on 2006-01-08
Hey Guys ... I have a little question...
  I am quite new to linux... 
  I installed ubuntu on a windows xp partition. I can't remember making a swap partition... can I make one now... my ubuntu keeps hanging up...  I have 256 megs on a Compaq 1700t ...

I tried the code for making a swap file... nothing happened...

any help????

---

### Post by OlineSixtyOne on 2006-01-08
I put a 1 GB swap partition on. That gives me 2GB of total "memory", so I guess I should be okay. I don't do anything really memory intensive.

---

### Post by towsonu2003 on 2006-01-08
[QUOTE=Efrain Valles]Hey Guys ... I have a little question...
  I am quite new to linux... 
  I installed ubuntu on a windows xp partition. I can't remember making a swap partition... can I make one now... my ubuntu keeps hanging up...  I have 256 megs on a Compaq 1700t ...

I tried the code for making a swap file... nothing happened...

any help????[/QUOTE]

banadushi's commands may require sudo to be used?? (that's a question for banadushi)

in a terminal, what's your output for ```
free -m
``` this will show whether you have a swap,  how big it is, and how much of it is in use...

---

### Post by banadushi on 2006-01-09
[QUOTE=towsonu2003]banadushi's commands may require sudo to be used?? (that's a question for banadushi)
[/QUOTE]

Yea those command need to be executed with root permissions.  So either you need to become root, or if you're on a stock install prefix all those commands with sudo to execute them with root permissions.

Also if you need the swap file to be persistant across reboots you will need to put it into /etc/fstab like so:

```

/swap.1    none    swap    sw    0 0

```

Have a good one.

Jason

---

### Post by shadesfox on 2006-01-09
You can work with out a swap file.  I would highly advise against it.  Linux already does a good job of keeping out of the swap unless it needs to.  On my machine I have a 512 meg swap file with 1 gig of ram.  In some cases not having the swap can cause a kernel panic.  It really is best to have at least 512 megs even on a modern system.  Hard disk space is cheap and things get really nasty if you need it and don't have it so why not run with swap?

---

### Post by Efrain Valles on 2006-01-09
ok guys here is my output from   free -m:

             total       used       free     shared    buffers     cached
Mem:           250        246          3          0          4        109
-/+ buffers/cache:        133        116
[COLOR="Red"]Swap:            0          0          0
[/COLOR]
No swap file...
I want to add maybe 512 megs more out of my hard drive for VM... I tried the code above but once I ejecute the first line. my system hangs up...

thanks for your help guys...

Efrain

---

### Post by rooster on 2006-01-09
[QUOTE=banadushi] [...] I like to tell customers that swap is like insurance, you hope to never use it, but if you need to its there.

[...]

PS.  Technically a box with the 2.6 kernel can exist without swap at all and be expected to deal with it quite well.  But then again some people also drive without insurance.[/QUOTE]

Just a sidenote: in Germany it's illegal to drive without insurance. ;)  And since not only RAM has dropped in price, but HDD space has dropped just more, imho there is no reason to work without a swap partition.

Rooster

---

### Post by rooster on 2006-01-09
[QUOTE=Efrain Valles]I installed ubuntu on a windows xp partition. [/QUOTE]

What do you mean by it? Did you set up a dual boot? Or did you delete the Win-partition?

What does your /etc/fstab say? ```
cat /etc/fstab
```

Rooster

---

### Post by Efrain Valles on 2006-01-09
Thnx Rooster...

I did It.. the code above did the trick . but since I am a newbie I didn't know I had to cut out the "#'s" from the code.... :razz: :razz: 

It worked thank you all very much...

my system is much more stable... and I saw the difference of Swap and no swap... 
I couldn't execute too many things at the same time without a swap.. I tried executing many programs that run using JRE (LIMEWIRE, and AUZERUS . Eclipse) and my free output showed som usage of both the RAM and SWAP... :)

thank you  very much ... My ubuntu Rocks.. again....

---

### Post by rooster on 2006-01-09
[QUOTE=Efrain Valles]My ubuntu Rocks.. again....[/QUOTE]
That's nice to hear!

Then, keep on rockin'!

---

