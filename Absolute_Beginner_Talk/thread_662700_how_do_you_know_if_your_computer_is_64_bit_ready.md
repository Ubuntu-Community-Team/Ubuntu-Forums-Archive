---
title: "how do you know if your computer is 64 bit ready?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2008-01-09
What are some of the ways to tell if your computer is ready for 64 bit?

---

### Post by milton1 on 2008-01-09
Either you have a 64-bit CPU, or you do not. For example, P4: not, AMD Athlon 64 or Intel Core 2 Duo: 64-bit.

---

### Post by pdlethbridge on 2008-01-09
I have a 2.6 gig p4, no good huh?

---

### Post by Pevichaey5 on 2008-01-09
the later Pentium 4 processors were 64bit, and normally a computer is 64bit compatiable if they have a 64bit bus/fsb but the new dual core procesors are 64bit compatiable

check on intel website

---

### Post by overdrank on 2008-01-09
> **pdlethbridge said:**
> What are some of the ways to tell if your computer is ready for 64 bit?

HI and you can also use the command ```
lshw | less
```
example
 *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.11.2
          size: 1GHz
          capacity: 1GHz
    [COLOR="Red"]      width: 64 bits[/COLOR]

---

### Post by LowSky on 2008-01-09
I thought pentiums werent 64 bit until intel release the Pentium D

I know when I boot my computer it says 64 bit compatible. next to the processor model. but intels website should say something, as long as you know more about your chip like model number or core name.

If you dont know or cant tel x86 versions of ubuntu or any OS will run just as good.

---

### Post by Taboo Mirage on 2008-01-09
*Deleted.*

---

### Post by pdlethbridge on 2008-01-09
deleted

---

### Post by oldb0y on 2008-01-09
Hehe... too bad. You could always get a cheap Core 2 Duo.

---

### Post by staticvoid on 2008-01-09
whys 64-bit better then 32-bit?

sorry  :) dumb noob question ;)

SV

---

### Post by pdlethbridge on 2008-01-09
lshw | less gave me this

 description: Desktop Computer
    product: MS-6728
    vendor: MICRO-STAR INC.
    version: 2.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: MS-6728
       vendor: MICRO-STAR INC.
       physical id: 0
       version: 2.00
       serial: 00000000
       slot: v
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V3.A (09/29/2004)
          size: 64KB
:

---

### Post by oldb0y on 2008-01-09
Yeah... It's 32-bit:(

---

### Post by Taboo Mirage on 2008-01-09
```
lshw -C cpu | grep width
```

That'll tell you explicitly what your CPU's width is only.  It is probably the most reliable method.  As it says 32 bits, then you cannot run a 64-bit version of any operating system.

---

### Post by Pevichaey5 on 2008-01-09
i have a 64bit C2D laptop and i was running ubuntu 64bit for a while, but i had problems, such as, i needed to install an anti virus called avg for my coursework at college, but wasn't able to because it was a 32bit application

personally, i don't think 64bit software is really upto the job yet so i'm going to stick to 32bit

---

### Post by pdlethbridge on 2008-01-09
pdleth@pdleth-desktop:~$ lshw -C cpu | grep width
WARNING: you should run this program as super-user.
       width: 32 bits     
          width: 32 bits
          width: 32 bits
pdleth@pdleth-desktop:~$

---

### Post by pdlethbridge on 2008-01-09
well, It says 32 bits 3 times, so does that mean I can run up to a 96 bit system?

---

### Post by Pevichaey5 on 2008-01-09
lol

maybe its talking about the width x height x length lol

---

### Post by Taboo Mirage on 2008-01-09
Lol. =P

Your CPU is 32-bit, man.  You can't run 64-bit OS on it at all.  Ever.  You'd need a new chip.  Frankly, it's not worth it unless you're doing some CPU-heavy tasks such as compiling things from source, etc. on a frequent basis or other such number-crunching things.  It'd be nice to have, but certainly not a necessity.

---

### Post by oldb0y on 2008-01-09
Just check my sig, let's you use every Hz of your CPU:)

---

### Post by capink on 2008-01-09
> **staticvoid said:**
> whys 64-bit better then 32-bit?

sorry  :) dumb noob question ;)

SV

The major difference is that 64 bit processors are able to access ram more the 4G. I don't think this will make a difference for a end users at the moment.

---

### Post by Paulmd on 2008-01-09
> **Taboo Mirage said:**
> Lol. =P

Your CPU is 32-bit, man.  You can't run 64-bit OS on it at all.  Ever.  You'd need a new chip.  Frankly, it's not worth it unless you're doing some CPU-heavy tasks such as compiling things from source, etc. on a frequent basis or other such number-crunching things.  It'd be nice to have, but certainly not a necessity.

The problem with THAT is along with a new processor, it's likely you'd need a new motherboard, too.

---

### Post by pdlethbridge on 2008-01-09
especially if OS's like Vista can't recognize anything above 3 gigs

---

### Post by Pevichaey5 on 2008-01-09
i heard 64bit has been around since like the 70's a few weeks back to help isp's and big company servers, and that it has only hit the end user resently

not sure if its true though

---

### Post by pdlethbridge on 2008-01-09
I built this system 2 years ago just before the pci/sli/775 lga craze hit. It would cost me between $400 and $500 minimum to upgrade now.About the only things I could use are the hard drives and cd/dvd drives. To me, it's not worth it.

is there a 64 bit ubuntu? or 96 bit?:lolflag:

---

### Post by oldb0y on 2008-01-09
> **pdlethbridge said:**
> especially if OS's like Vista can't recognize anything above 3 gigs

I've got a desktop with 32-bit XP, and it detects 3.5 GB out of 4 GB. not that bad.

---

### Post by Pevichaey5 on 2008-01-09
i'm 99.99% sure there is no such thing as a 96bit computer yet lol if anything i would think 128, but not yet, they haven't even perfected 64bit yet lol

64bit of ubuntu is available for download as well

---

### Post by Taboo Mirage on 2008-01-09
> **capink said:**
> The major difference is that 64 bit processors are able to access ram more the 4G. I don't think this will make a difference for a end users at the moment.

While it is a major difference, a more significant difference is that a 64-bit core will be able to handle data at twice the rate a 32-bit processor can do, in theory at least.  Intensive processor tasks on a 64-bit CPU will run much faster than they would on a 32-bit chip.  With the right applications coded to take full advantage of a 64-bit core, you could see a significant performance increase.  See some [benchmarks](http://art-blog.no-ip.info/files/amd64vsi386.pdf) for an idea.

---

### Post by Paulmd on 2008-01-09
> **staticvoid said:**
> whys 64-bit better then 32-bit?

sorry  :) dumb noob question ;)

SV


Not a dumb question. The incredibly oversimplified answer is that a 32 bit cpu can push 32bits of data each cycle. A 64 bit cpu can push 64bits. That means all other things being equal, a 64 bit cpu is going to give better performance.

In reality, this works out to about 15% performance increase. 

Most consumer grade PC-clone processors have been 32 bit since the days of the 386.

---

### Post by pdlethbridge on 2008-01-09
what good is it if you are not 100% sure!](*,)   #26

---

### Post by oldb0y on 2008-01-09
Not 100% sure, about what?

---

### Post by pdlethbridge on 2008-01-09
#26

---

### Post by oldb0y on 2008-01-09
I'm sorry m8, you have a 32-bit CPU, and that's the way it is:lolflag:

---

### Post by philinux on 2008-01-09
> **capink said:**
> The major difference is that 64 bit processors are able to access ram more the 4G. I don't think this will make a difference for a end users at the moment.

Microsoft are partly to blame for this myth.

32 bit Windows 2000 datacentre server edition can access 32gb. M$ could have made 32 bit vista address this much they already cracked it years ago with PAE (Physical address extension). It bumps the memory address system to 36bits. The limit for that is 64gb.

---

### Post by Paulmd on 2008-01-09
> **philinux said:**
> Microsoft are partly to blame for this myth.

32 bit Windows 2000 datacentre server edition can access 32gb. M$ could have made 32 bit vista address this much they already cracked it years ago with PAE (Physical address extension). It bumps the memory address system to 36bits. The limit for that is 64gb.


A similar thing was done with 286s a long time ago. 16 bit brocessor, but dos would address 24bit. It was ugly.

I seem to remember something similar on the mac world, years ago. But I'm not a mac man, and macs were less similar to pcs then they are now.

---

### Post by pdlethbridge on 2008-01-09
Wasn't it true that win 95 couldn't see over 386mg of memory until a patch was added then it only could see 500mg? And that was a 2 bit system like Me.

---

### Post by philinux on 2008-01-09
Interestingly if you have say a 512meg graphics card this has to be addressed too. And guess what, when the machine wants access to the memory on your nice graphics card, it needs to get at it directly.

If the total address space is 4gb then the graphics cards 512meg addresses has to lie within it.

---

### Post by whein on 2008-01-09
> **Taboo Mirage said:**
> While it is a major difference, a more significant difference is that a 64-bit core will be able to handle data at twice the rate a 32-bit processor can do, in theory at least.  Intensive processor tasks on a 64-bit CPU will run much faster than they would on a 32-bit chip.  With the right applications coded to take full advantage of a 64-bit core, you could see a significant performance increase.  See some [benchmarks](http://art-blog.no-ip.info/files/amd64vsi386.pdf) for an idea.

Sorry, but this is wildly misleading.  64 bit CPUs can handle 64 bit numbers in a single operation, but they take just as long if you are adding two 32 bit numbers as a 32 bit processor would.  The difference is that a 32 bit CPU adding two 64 bit numbers has to do some funky things in software to get the result.  So unless you work with very large numbers (heavy engineering and science calculations mostly, like weather modeling or high end CAD) there will be no appreciable speedup moving from 32 bit to 64 bit.

  However, a lot of the newer chips have more than one core (AMD's X2 series for example) so that you really can perform two operations at the same time.  Now that's fun!
-Will

---

### Post by oldb0y on 2008-01-09
> **whein said:**
> However, a lot of the newer chips have more than one core (AMD's X2 series for example) so that you really can perform two operations at the same time.  Now that's fun!
-Will

Not to mention Quad Core, even more fun:-D

---

### Post by capink on 2008-01-09
> **philinux said:**
> Microsoft are partly to blame for this myth.

32 bit Windows 2000 datacentre server edition can access 32gb. M$ could have made 32 bit vista address this much they already cracked it years ago with PAE (Physical address extension). It bumps the memory address system to 36bits. The limit for that is 64gb.

That is news for me. So does this mean that 32 bit cpu running ubuntu can access more than 4 giga.

---

### Post by philinux on 2008-01-09
No you need the 64 bit version of ubuntu.

The reason 32 bit vista is crippled is cos they want to sell you the 64 bit version. $$$$$$$

---

### Post by capink on 2008-01-09
and will the 64 version work on a 32 processor?

---

### Post by perlluver on 2008-01-09
> **capink said:**
> and will the 64 version work on a 32 processor?

No, it will not work with a 32 bit processor.

---

### Post by capink on 2008-01-09
So, to access more than 4 giga you need the 64 bit edition.

And to use the 64 bit edition, you need 64 bit processor.

So, you cannot access more than 4 giga with a 32 bit processor no matter what operating system you are using.

Am I correct? or maybe I missing something.

---

### Post by Paulmd on 2008-01-10
> **pdlethbridge said:**
> Wasn't it true that win 95 couldn't see over 386mg of memory until a patch was added then it only could see 500mg? And that was a 2 bit system like Me.

512mb for win9x/me. But, back then it wasn't much of an issue, the few systems with more than 512mb ram weren't running 95, they were NT4, or were special in some way. 

386 mb is a funny number for ram, it's all powers of 2, y'see. It could be 384mb, which is 256+128. I've never heard of a 384mb barrier on win95 either. Then again, I haven't been inclined to put win95 on a system with that much ram. 

There could be limits on dimm size,  or overall limits imposed by motherboard. For example, take an old celeron 566mhz emachine. You can upgrade it to a whopping 256mb (2x 128mb pc100). Pre-crippled. Another example is a Dimention 4100, which the factory specs say you can put 2x256mb pc-133 in, for a total of 512, but in reality, you can slap a single stick of 512mb in, But any beyond that and it refuses to complete the post, complaining about a memory size error.

---

### Post by Paulmd on 2008-01-10
> **capink said:**
> So, to access more than 4 giga you need the 64 bit edition.

And to use the 64 bit edition, you need 64 bit processor.

So, you cannot access more than 4 giga with a 32 bit processor no matter what operating system you are using.

Am I correct? or maybe I missing something.

First 2 are correct, in the context of home-user oses. The last is not, though the 32bit oses that can go beyond this are server class, or are otherwise special.

For the purposes of home computing, however, it is correct.

---

### Post by pdlethbridge on 2008-01-10
someone mentioned video cards, so if you have 2 SLI video cards with 512 mg memory, then your 4 gig computer will be only 3 gig. Right?

---

### Post by Paulmd on 2008-01-10
> **pdlethbridge said:**
> someone mentioned video cards, so if you have 2 SLI video cards with 512 mg memory, then your 4 gig computer will be only 3 gig. Right?

Not positive on this, because of how SLI works.

When working together, to get improved graphics performance, you don't get to add the memories of the cards together as if you had a 1GB card. It acts like a single 512mb card. 

2 SLI-capable cards in non-SLI mode, perhaps.

However, if you have that kind of system, it's almost certain you'd have the capabilities to go to 64 bit, and avoid the whole mess.

---

### Post by pdlethbridge on 2008-01-10
mess? you say mess? That's an understatement!:confused:

---

### Post by pdlethbridge on 2008-01-10
I seem to recall that if you had a store bought computer, your 256mg ram would always show up a few missing and I don't think it had to do with on board video.

---

### Post by pdlethbridge on 2008-01-10
bump

---

### Post by philinux on 2008-01-10
> **pdlethbridge said:**
> I seem to recall that if you had a store bought computer, your 256mg ram would always show up a few missing and I don't think it had to do with on board video.

Yes with shared thats the case.

Problem only occurs on 32bit if you've got the max ram ie 4gig then the graphics card(s) have to be addressed from within that.

---

### Post by philinux on 2008-01-10
It's worse than i thought.

[http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by pdlethbridge on 2008-01-10
I should have posted that. I saw it in a another computer forum the other day.

---

### Post by oldb0y on 2008-01-10
Well, next time I decide to buy a processor, it definitely will be a 64-bit.

---

### Post by pdlethbridge on 2008-01-10
But will you ever need it in linux?

---

### Post by oldb0y on 2008-01-10
Sure, why not?

---

### Post by pdlethbridge on 2008-01-10
when?

---

### Post by oldb0y on 2008-01-10
What do you mean, when?

---

### Post by philinux on 2008-01-10
My next pc is going to be a dual core amd 64 bit probably 4800+ or 5000+

Gonna get 4gig mem installed.

Whats the point of installing a 32bit OS.

---

### Post by eolson on 2008-01-10
> **philinux said:**
> My next pc is going to be a dual core amd 64 bit probably 4800+ or 5000+

Gonna get 4gig mem installed.

Whats the point of installing a 32bit OS.

Software availability and stability.

64 bit is coming,  but not here yet.   I have 2 64 bit systems and have 32 bit Ubuntu on both of them.

---

### Post by pdlethbridge on 2008-01-10
when will Ubuntu have a 64 bit OS?

---

### Post by philinux on 2008-01-10
Linux will be the only OS on it so I'll give it a whirl. Prob end Jan when new pc arrives.

Nothing to lose I suppose.

I've got the 64 bit ubuntu cd already burned ready to go

---

### Post by oldb0y on 2008-01-10
> **pdlethbridge said:**
> when will Ubuntu have a 64 bit OS?

There is one already.

---

### Post by pdlethbridge on 2008-01-10
dah:oops:

---

### Post by Paulmd on 2008-01-10
> **pdlethbridge said:**
> I seem to recall that if you had a store bought computer, your 256mg ram would always show up a few missing and I don't think it had to do with on board video.

Not usually. Not a few MB, anyway A couple KB, 

Onboard video would be the single largest chunk.

---

