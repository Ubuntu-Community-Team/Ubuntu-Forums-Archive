---
title: "Virtualization vs Dual-booting vs Xen on a Mac?"
date: 2008-02-23
forum: Apple Intel Users
---

### Post by gutsy08 on 2008-02-23
Hi, I was just wondering what the pros and cons of virtualizing Ubuntu (and also XP) on a Mac would be.  I'm planning on getting either a iMac or Macbook with 4 gigs for RAM - so hopefully this will be enough. So far, I'm aware that virtualizing Ubuntu (with Virtualbox, VMware, or Parallels... or maybe Xen?) has a few drawbacks, such as the lack of 3D acceleration (not sure if this is the case with Xen too...), which means no Compiz :\.  I'm wondering if anyone can fill me in on what the other pros and cons of virtualizing vs triple-booting would be.

Virtualizing on to of Mac OS X - Parallels, Vmware, Virtualbox, Qemu... etc.
Pros: No need to reboot, nifty Coherence or Seamless modes mean better integration.  
Cons: Requires more RAM and CPU, performance, no Compiz...  I've heard that VMware performs fairly well here though, so perhaps with 4gigs of RAM it won't matter much.  I've also heard Parallels is slow, but that may have changed, and I'm not sure at all how Virtualbox runs.  Hardware support seems varied too.  VMware seems to support certain things like USB printing better than Parallels.  Again, not sure about Virtualbox.  However Parallels supports multiple displays, whereas VMware does not...

Triple-booting OS X, Ubuntu, XP
Pros: Faster, less RAM required, best possible performance.
Cons: Rebooting is time consuming and inconvenient.  Requires more partitioning.

Virtualizing with Xen, bare-metal virtualization, KVM... (any other options?)
Pros: Low-overhead, would be a nice solution.
Cons: Not sure it's possible to virtualize Mac OS X yet, at least not the retail edition.

Finally, just to make things more complicated, there is the possibility of dual booting Ubuntu part of the time, and virtualizing when it's not convenient to reboot.  I think VMware can do this, but I'm not sure about the other programs.

So, have I covered all the options?  I'm want to make sure I have a good idea of what the possible options are.  For the most part, I would like to have Ubuntu, OS X and Windows apps all on one desktop (with shared data, cut and paste between all programs, etc.), though I would like to be able to run the occasional 3D game.

Also, are there any machine specific issues I might encounter here?  I'd assume it'd all be about the same if you're running inside a virtual machine, but maybe then again maybe not?

---

### Post by SpiderGorilla on 2008-02-23
Don't forget you've always got Qemu to help you with your emulation needs. Solid piece of software. At least... on Windows and Linux. I never got to try it on Mac OS X.

You have basically covered all the options, yes.

For the purposes of speed and sanity, I personally recommend a dual-boot solution.

---

### Post by cyberdork33 on 2008-02-23
I dual boot OS X and Ubuntu, and usually stick to one or the other for long periods of time. I have Ubuntu and Windows XP in Fusion when needed.

---

### Post by lex1 on 2008-02-23
just as a matter of interest why do you need windows  in vmware fusion?


lex1

---

### Post by gutsy08 on 2008-02-23
> **lex1 said:**
> just as a matter of interest why do you need windows  in vmware fusion?


lex1

I'm mainly interested in running Windows in a VM for a few small Windows programs that won't run  under Linux or Mac OS X.  Also, I might occasionally want to run a few games.  I heard VMware performs pretty well for certain games.  I suppose Wine might be a good solution too, not sure which one is better.

---

### Post by lex1 on 2008-02-23
i have just installed ubuntu and windows on a imac i like it a lot more than vmware.

I think vmware is easy to set up a mac and vmware fusion has a more simple way of commincating between say ubuntu and windows and mac. But for me the full
feeling of windows and ubuntu in its partition makes it more comfortable to use.

lex1

---

### Post by cyberdork33 on 2008-02-23
I don't need a full install of windows, and I don't want to fiddle with triple booting. I just run a few apps that run only in windows, mainly for hacking phones, and writing some VBA macros for work in Office.

---

### Post by handy on 2008-02-24
> **gutsy08 said:**
> I'm mainly interested in running Windows in a VM for a few small Windows programs that won't run  under Linux or Mac OS X.  Also, I might occasionally want to run a few games.  I heard VMware performs pretty well for certain games.  I suppose Wine might be a good solution too, not sure which one is better.

I would investigate whether the games you want to run will work satisfactorily in a VM.  Also, they may work well under Wine, Cedega or CrossOver(Mac or Linux).  It is highly unlikely that a game under any kind of VM will work as well as one running under Wine or one of it's derivatives, of course the game has to first be able to run in the non-native environment. ;-)

---

### Post by lex1 on 2008-02-24
When you you don't need a full install of windows what do you mean?

Fiddle with triple booting? well not all that much diffrence with a dual boot, from what I can make out

lex1

---

### Post by bringar on 2008-02-26
i strongly recommend fusion right now if you're bent on virtualization, 
it is the clear performance winner and has avery mature stable code base on several platforms, paralells just can't say that as well right now.

my only experiences with Qemu are on my powerPC hardware... however it is a full hardware emulation, 
vmware, xen and their like allow you to run at near iron speed for many things.
you're going to get the worst performance of any of the options you list with qemu, it also requires guest OS alteration to my memory.

bare iron virtualization does not yet work off the shelf on macs to my knowledge.

if you're after playing windows games or high performance, i'd reccomend to dual boot, same goes for using openGL or the like, of course then i still like XFce 3.18 

if you still want to virtualize and want better graphics performance, shell out the extra dough for discrete graphics as other threads will advise.

I've deployed a mac pro quad 2.66 with 8GB ram running 10.4 with  two copies of windows server 2003 inside VMware Fusion. these machines run great with a whole slew of windows services on them.  VMware is the only choice right now for running production servers unmodified virtualized on macosX

however parallels is in closed beta on a server product for the mac, and i'm sure VMware has something up their sleeves for this market.

apple has said that you can virtualize macosX as long as the license is legal and you're doing it on apple hardware.
that said, the only near term solutions here are macos on macos, elsewise you'd be reverse engineering....

cheers!

---

### Post by aletheianalex on 2008-02-26
I just got my new setup running, and I am triple booting OSX.5.2, Linux, and XP  on a MBR-formatted drive with rEFIt.  I also have WINE installed in both Linux and OSX as well as Crossover/wine  in OSX AND I run Parallels, VMware player as well as VirtualBox (free virtualizer) and Oemu 0.9.1 with FreeDOS unser x86 and Qemu 0.8.2 with  Debian Woody under PowerPC (for compiling PPC crap).

  It may be overkill, but I run  that setup so that I only have to reboot when absolutely neccessary.  OSX is my main OS, but I spend a lot of time in Linux.  WINE runs most of the Win32 apps that I need, but occasionally I boot into XP if I have to run a DAW audio proggie that just won't run, and I need FreeDOS in QEMU for a few little DOS engineering apps and playing Xcom (old video game).

You can run a virtualizer from a REAL partition (XP or Linux) with a little hacking, and still boot into that partition when needed... so that is not an either/or... however, there are some drawbacks and at one point in time, Parallels screwed my XP install into oblivion, but I was able to restore it.

ALSO... rEFIt will boot OSX or Linux off an external drive just fine, so that is another thing to keep in mind... AND even though XP will not boot from an external drive without heavy hacking and patching, you can install and  boot XP off an external USB drive  in a VIRTUALIZER no problem.  I have also cloned my various installs, moved them on and off partitions and external drives and booted them up in a virtualizer with no issues except occasionally having to go through sysprep-ing XP and occasionally re-authorizing it with Microsoft.


Hope there is some useful info in there for you...

---

### Post by cyberdork33 on 2008-02-26
> **aletheianalex said:**
> ALSO... rEFIt will boot OSX or Linux off an external drive just fine, so that is another thing to keep in mind... 

Care to elaborate here?
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)
There is almost nobody able to boot Linux from an external drive due to issues with Apple's EFI implementation.

---

### Post by lex1 on 2008-02-26
Just as a matter of interest how did you set up wine on OSX?


lex1

---

### Post by aletheianalex on 2008-02-26
> **cyberdork33 said:**
> Care to elaborate here?
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)
There is almost nobody able to boot Linux from an external drive due to issues with Apple's EFI implementation.

Sure... I'll collect the details.  I was completely unaware of that problem, so I'll read the thread.   I have Debian on an external drive and just did a standard install with no issues.

> Just as a matter of interest how did you set up wine on OSX?.

I used to compile it myself and then add in the fonts, but I got the newest build pre-compiled from here:

[http://www.kronenberg.org/darwine/](http://www.kronenberg.org/darwine/)

From there you just run the setup proggie from the folder just like the Linux version.

---

### Post by lex1 on 2008-02-26
Thanks for Darwine , its much like the linux version .

lex1

---

### Post by cyberdork33 on 2008-02-26
> **aletheianalex said:**
> Sure... I'll collect the details.  I was completely unaware of that problem, so I'll read the thread.   I have Debian on an external drive and just did a standard install with no issues.Someone suggested that it worked without a hitch on certain Macbooks, but most everything else has issues for some reason. I know it didn't work for me the last time I tried it on my iMac.

---

