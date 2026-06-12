---
title: "Another Question..."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by nightynight on 2007-11-11
When installing Ubuntu, how big should i make a swap partition?  And do i need to flag or mark it as anything?

I'm making sure i dont mess anything up...

---

### Post by Bachstelze on 2007-11-11
Rule of the thumb is twice your RAM but from experience, if you have 1G of RAM or more, it's unlikely you willl ever need more than 256M of swap (unless you plan to use suspend-to-disk of course, in which case your swap will need to be at least as large as your RAM).

---

### Post by FuturePilot on 2007-11-11
See the post above.

---

### Post by ubnewbie2 on 2007-11-11
> **nightynight said:**
> When installing Ubuntu, how big should i make a swap partition?  And do i need to flag or mark it as anything?

I'm making sure i dont mess anything up...

When you make a swap partition, you tell the partitioner that it is swap, instead of choosing a file system like ext3 or Reiser or whatever, so that's how the system knows it is swap.

I tend to create one about 4 times your memory for systems with small amounts of memory,  Maybe only twice the amount if you have lots of memory (1GB or so).

---

### Post by oilchangeguy on 2007-11-11
> **FuturePilot said:**
> They usually say about 2X your RAM. So if you have 1GB of RAM you would probably want a swap partition around 2GB.

who is "they"? and read post #2.

---

### Post by oilchangeguy on 2007-11-11
> **ubnewbie2 said:**
> When you make a swap partition, you tell the partitioner that it is swap, instead of choosing a file system like ext3 or Reiser or whatever, so that's how the system knows it is swap.

I tend to create one about 4 times your memory for systems with small amounts of memory,  Maybe only twice the amount if you have lots of memory (1GB or so).

do you even understand what swap is? it's virtual ram. the computer uses space on the hard drive as needed for virtual ram. there's no way any computer will ever need 4 times the amount of physical ram. physical ram is much, much faster than virtual ram. and please explain just what is it that you do with your computer, that it needs so much virtual ram. try this, go to system, admin, system monitor. and let us know just how much swap your computer is NOT using.

---

### Post by SOULRiDER on 2007-11-11
I have 1 GB of RAM and 256MB of swap space. Right now with desktop effects enabled im using only 250MB of RAM and no swap at all. IMHO if youre not going todo any virtualization, with 1GB of RAM even 128MB of swap is enough, but if youre going to do WINDOWS virtualization I suggest you make your swap partition 256MB or more although more than 1GB would be more than enough.

---

### Post by FuturePilot on 2007-11-11
> **oilchangeguy said:**
> who is "they"? and read post #2.

Yes, I saw that after I posted since we posted at the same time. ;)

---

### Post by ubnewbie2 on 2007-11-11
> **oilchangeguy said:**
> do you even understand what swap is? it's virtual ram. the computer uses space on the hard drive as needed for virtual ram. there's no way any computer will ever need 4 times the amount of physical ram. physical ram is much, much faster than virtual ram. and please explain just what is it that you do with your computer, that it needs so much virtual ram. try this, go to system, admin, system monitor. and let us know just how much swap your computer is NOT using.

Instead of abusing me, you should realise that I merely posted what _I_ do, and there is NO harm in having more than you need. OTOH not having enough can be awkward. 

If you run many applications, only one or 2 are usually active at a time, so having the other's memory swapped out is good.  If you have no, or very little swap, you will be limited.

oh, and try running a few virtual machines for a good way to eat up your RAM :-)

---

