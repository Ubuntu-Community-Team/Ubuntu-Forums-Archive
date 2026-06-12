---
title: "max memory in ubuntu"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-19
what is the maximum amount of RAM that Ubuntu 7.10 will read/address?  i currently have 2GB in the PC and want to increase to 4GB.  will this work?  thanks.

---

### Post by Origin415 on 2008-02-19
It depends on whether you have a 32-bit or 64-bit processor. 64-bit processors have no limit you could achieve anytime soon, but 32-bits max out at 3-4GB.

---

### Post by Matt26 on 2008-02-20
i have a 32bit CPU- is there any way for me to determine exactly how much RAM Ubuntu will recognize?  i want to add more for use on my vm's but i don't want to go out and buy more just to discover that Ubuntu won't utilize it.  thanks.

---

### Post by jan quark on 2008-02-20
check this thread

[http://ubuntuforums.org/showthread.php?t=508087](http://ubuntuforums.org/showthread.php?t=508087)

---

### Post by chewit on 2008-02-20
32bit can only handle upto 2GB

64bit can handle more than 2GB. not sure what the max is. But Mac OSX 10.5 can handle upto 32GB

---

### Post by shad0w_walker on 2008-02-20
32Bit will handle more along the lines of 3.2Gb (Can support more but requires some tinkering most of the time)

---

### Post by njparton on 2008-02-20
32 bit will address up to 3-3.5 GB in total (i.e. including the onboard RAM used by the BIOS (usually around 4MB) and your video card RAM (which can be 512-1024MB these days)).

If you want to go for 3GB+ and not have any issues then install the 64 bit version of ubuntu and make sure your motherboard supports 64 bit OSes and you have their latest BIOS.

I run 64bit ubuntu with 4GB ram without any problems on my desktop (unlike 64 bit Vista which can only be installed with 2GB until a patch has been applied!).

---

### Post by Matt26 on 2008-02-20
so what do i need to do in order for my system to recognize 4GB or RAM?

---

### Post by Duck2006 on 2008-02-20
> **Matt26 said:**
> so what do i need to do in order for my system to recognize 4GB or RAM?

Upgrade to a 64Bit CPU. other than that 4Gb on 32Bit is the maximum.

---

### Post by Matt26 on 2008-02-20
from what i have read here, i understand that there is some 'tweaking' required in order to have ubuntu recognize 4GB or RAM on a 32bit CPU, is this correct?  if so, what needs to be done?

---

### Post by Duck2006 on 2008-02-20
> **Matt26 said:**
> from what i have read here, i understand that there is some 'tweaking' required in order to have ubuntu recognize 4GB or RAM on a 32bit CPU, is this correct?  if so, what needs to be done?

I may be wrong but i think the system should read the 4Gb with out tweaking.

---

### Post by insane_alien on 2008-02-20
no, you definitely need tweaking as a bunch of addresses are reserved  for system buses and graphics. therefore they are unusable as RAM.

go 64-bit, i have 8GB RAM all recognised with that.

---

### Post by thisismalhotra on 2008-02-20
> **Matt26 said:**
> so what do i need to do in order for my system to recognize 4GB or RAM?

Most cases your system will only recognize a max of 3.5 gigs. With 4 gigs you use some more but will not use it fully. I would say if you can upgrade to  3 giggs you should be good

---

### Post by njparton on 2008-02-20
> **Matt26 said:**
> from what i have read here, i understand that there is some 'tweaking' required in order to have ubuntu recognize 4GB or RAM on a 32bit CPU, is this correct?  if so, what needs to be done?

Most CPUs these days are 64 bit capable. What do you have?

---

### Post by Matt26 on 2008-02-20
i only have a P4 3.0Ghz, and i won't be upgrading anytime soon, but i would like to be able to put 4GB RAM in and have ubuntu recognize all of it.

---

### Post by Duck2006 on 2008-02-20
Try using this search engine, it is for ubuntu searches.

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by oldb0y on 2008-02-20
I remember someone talking about the server-version of Ubuntu beeing able to handle more RAM, I do not have any sources to rely on, but maybe you could check this out for your self.

---

### Post by t-tbone on 2008-02-22
It is a shame that Ubuntu doesn't provide a big-mem kernel package that you can just apt-get install like Debian does.  That is all that it takes to get Debian Etch to see my 4 GB.

---

### Post by skunkTrader on 2008-04-16
I have a Dell workstation with 4GB RAM installed.  3635920k is recognized by my 2.6.22-14-generic kernel.

---

### Post by jon_herr on 2008-04-17
Theoretically, a 32 bit processor can address 4GB of RAM:

2 ^ 32 = 4294967296 is approx 4GB 

The problem comes in where memory mapped devices occupy the same address space...

The ONLY hope to get more use of available RAM using a 32 bit processor is through a more elaborate configuration of the peripherals.  This is not normally done, and sometimes requires hardware support through the BIOS or add in cards.

One thing you might try with the generic kernel is changing a BIOS setting.

Look in "advanced settings" for "memory hole remap" or the like and enable it.  Then do a 'cold' boot by shutting the computer off - and start up again.

See if any more physical ram is available in your 32 bit OS.  

Otherwise, use a 64 bit version of Ubuntu... which I might add - has come a long, long, way.  It's almost as capable as the 32 bit version.

: )

Jon

---

### Post by achelis on 2008-04-17
2 ^ 32 is exactly 4GB not approx :)

I'm just thinking you should make sure you really need that extra RAM... personally I've never used more than 1.5 GB since I switched to Ubuntu - but I guess it depends a lot on what kind of programs you run..

---

### Post by st33med on 2008-04-17
OK, let me clear up the facts. The kernel assigns memory that can be used. 256MB of memory are not used in 4GB in a 32-bit system because of the 32^2 equation. The 64-bit Ubuntu kernel has an option enabled that allows up to 64 Gigabytes to be assigned. However, 64-bit is not compatible with some programs, like Flash. It is advisable that, even if you have a 64-bit processor running, if you have less than or equal to 4 GB of memory, use the x86 kernel for Intel (AMD for... well AMD). If you have an extreme amount of memory, x86-64 is the way to go (or AMD64).

---

### Post by bodhi.zazen on 2008-04-17
Most older 32 bit motherboards will support just shy of 4 Gb RAM.

Some newer 32 bit motherboards will support up to 64 Gb RAM.

You will need to either compile your own kernel or use the server kernel + possibly re-compile GRUB.

See my posts in this thread for additional information :

[http://ubuntuforums.org/showthread.php?t=751479](http://ubuntuforums.org/showthread.php?t=751479)

---

