---
title: "[SOLVED] Linux not seeing 1gb or ram"
date: 2007-11-17
forum: Apple Intel Users
---

### Post by macaholic on 2007-11-17
Today I installed some upgrades to my Mac Pro. I installed 2 gbs of ram, a 500gb hard drive, and a new graphics card fan. My issue is that When I boot into Ubuntu, it is only seeing 2gbs of the ram. i should add that OSX sees all the ram just fine. Any ideas would be greatly appreciated.

---

### Post by Levo75 on 2007-11-17
I don't know if this is true but i think i heard someone say that 32bit operating systems don't support over 2 GB of ram.

---

### Post by prodigalson666 on 2007-11-17
Windows doesnt support more than 2 gigs, iIts 4 Gigs for a 32 bit processor actually. That also includes swap so if you have 1GB swap then it will support only 3 GB of RAM

There are ways for a 32 bit OS to support more than 4 GB RAM, but it cannot allocate more than 4GB to a single process.

a 64 bit processor can address 2^64 bytes of memory.

---

### Post by macaholic on 2007-11-17
That doesen't really answer my question, I am running a 32 bit version of Ubuntu,

---

### Post by cyberdork33 on 2007-11-17
> **macaholic said:**
> That doesen't really answer my question, I am running a 32 bit version of Ubuntu,
Ok, so how big is your swap? I think he addressed your problem.

---

### Post by macaholic on 2007-11-17
Well, about the swap, the thing is I don't have a swap partition, the install guide I was using said that it was uneccesary. (Probably was a bad idea) Does ubuntu make a swap file instead if I don't have a partiotion?

---

### Post by cyberdork33 on 2007-11-17
> **macaholic said:**
> Well, about the swap, the thing is I don't have a swap partition, the install guide I was using said that it was uneccesary. (Probably was a bad idea) Does ubuntu make a swap file instead if I don't have a partiotion?

Not that I know of, but if you just chose "install in free space" or whatever then it would have created a swap partition for you. 

Type 'free' at the commandline, and you should get output telling you how much ram and swap are available (and used).

On the 32-bit system, you are limited to just under 4GB of memory, so I don't know where the rest of it is going... You might try booting a LiveCD to make sure it is not an issue with your current system... (could try the 64bit vs 32bit issue that way too).

---

### Post by macaholic on 2007-11-17
The output of free confirms that I don't have a swap partition,
```
             total       used       free     shared    buffers     cached
Mem:       2037868    1199752     838116          0      82516     592712
-/+ buffers/cache:     524524    1513344
Swap:            0          0          0

```
I will try booting off a cd and see what happens then.
EDIT: It seems as if I have lost my live cd, and that I don't have the iso anymore. I'll have to try this tomorrow, it's getting late anyway.

---

### Post by macaholic on 2007-11-18
Same output under live cd. Someone suggested to me that installing the 64-bit version and compiling my own kernel would resolve the issue, I don't want to trash my current setup, so anyone else have any ideas?

---

### Post by macaholic on 2007-11-24
Well, I solved it by finally breaking down and installing tje 64-bit version of Ubuntu, of course this opened up a whole slew of new problems. :(

---

### Post by cyberdork33 on 2007-11-25
> **macaholic said:**
> Well, I solved it by finally breaking down and installing tje 64-bit version of Ubuntu, of course this opened up a whole slew of new problems. :(

What problems...

---

