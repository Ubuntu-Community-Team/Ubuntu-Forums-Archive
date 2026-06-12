---
title: "Question about device drivers and hardware support - compiling kernel"
date: 2011-07-17
forum: Any Other OS
---

### Post by ClientAlive on 2011-07-17
Hi,

I'm wondering if, when I compile my kernel, I'm going to have to get the driver for each expansion card that's in the machine and have to manually install each one - or if it works differently.


Btw. I will be a Gentoo compile.

---

### Post by bodhi.zazen on 2011-07-17
> **ClientAlive said:**
> Hi,

I'm wondering if, when I compile my kernel, I'm going to have to get the driver for each expansion card that's in the machine and have to manually install each one - or if it works differently.


Btw. I will be a Gentoo compile.

On Gentoo, you can try the genkern (general kernel), otherwise it is safe to assume you will need to do exactly that, identify your hardware and make sure you compile the appropriate modules.

---

### Post by Elfy on 2011-07-17
Thread moved to Other OS/Distro Talk.

Sorry bodhi - didn't see you in here :)

---

### Post by ClientAlive on 2011-07-17
> **bodhi.zazen said:**
> On Gentoo, you can try the genkern (general kernel), otherwise it is safe to assume you will need to do exactly that, identify your hardware and make sure you compile the appropriate modules.


Thanks bodhi.

Ok. So I plan to actually compile the thing myself (a stage 3 build). What I'm struggling with is the location of drivers within the Linux system - and that from a couple different angles, I guess.

So then, these "modules" I know are part of the kernel and simply have to do with the selections that are made when configuring the kernel. (Actually, some things you want to compile in and some as a module but that's getting a little off track from my real question). So, I also know there is more to a functional Linux o/s than just a kernel. You also have System Tools - like bash (or ksh or zsh, whatever - your shell) and all the little stuff that helps you admin the system; then you have libraries (and other categories I won't mention).

What I'm getting at though, is that once I compile the kernel I don't think that's going to be the end of it regarding hardware. Specifically, making expansion cards work, I'm trying to figure out what is going to come next and what it is going to be like. Will I find myself on the Internet fishing around for some single device driver for say, my sound card or my NIC? If so, what will I do with it when I find it? What if there isn't one for Linux but only Window/ proprietary? Will I then have to deal with ndlswrapper? And where will I put that driver? What if it is made up of more than one file? Will one file go in this directory and the other in that and so on? What directory does it go in anyway?

That's what I'm talking about.

---

### Post by bodhi.zazen on 2011-07-17
> **ClientAlive said:**
> Thanks bodhi.

Ok. So I plan to actually compile the thing myself (a stage 3 build). What I'm struggling with is the location of drivers within the Linux system - and that from a couple different angles, I guess.

So then, these "modules" I know are part of the kernel and simply have to do with the selections that are made when configuring the kernel. (Actually, some things you want to compile in and some as a module but that's getting a little off track from my real question). So, I also know there is more to a functional Linux o/s than just a kernel. You also have System Tools - like bash (or ksh or zsh, whatever - your shell) and all the little stuff that helps you admin the system; then you have libraries (and other categories I won't mention).

What I'm getting at though, is that once I compile the kernel I don't think that's going to be the end of it regarding hardware. Specifically, making expansion cards work, I'm trying to figure out what is going to come next and what it is going to be like. Will I find myself on the Internet fishing around for some single device driver for say, my sound card or my NIC? If so, what will I do with it when I find it? What if there isn't one for Linux but only Window/ proprietary? Will I then have to deal with ndlswrapper? And where will I put that driver? What if it is made up of more than one file? Will one file go in this directory and the other in that and so on? What directory does it go in anyway?

That's what I'm talking about.

You will have to read the gentoo documentation ;p Last time I installed gentoo it only took me a month or so, but I was using LUKS and had to write an initrd.

Most "power users" are using Arch these days, so you may want to look at Arch.

You can build a custom kernel on any distro, google has a number of guides.

---

### Post by 1clue on 2011-07-17
I bounce back and forth between Gentoo and Ubuntu.

You're making this much too complicated.

Most drivers are bundled into the kernel source.  If you want a proprietary driver then you need to go look for it on the Internet, but if you're using any sort of standard PC hardware then the kernel source has enough to get you going.

The rest of the system accesses the drivers in a standard Linux way.  The driver itself is what cause the hardware's specific properties to work with the standard API of the operating system.  Once you get the driver working and the protocols you want to use set up in the kernel, then the rest of the OS works with that.

Might help to start at [http://www.kernel-seeds.org](http://www.kernel-seeds.org) where you can get a basic kernel config and then modify it to your hardware.

Figure on it taking more than one try.  Even after you get proficient at compiling and installing your kernel, you will probably sit there for hours and tweak a setting just to see what happens.

Safety:
Always keep one known-to-work kernel in your system, preferably as the default boot.  Otherwise you have to boot from the installer CD, mount your partitions and chroot into your environment and try again.  If you can boot semi-normally then you can move your new kernel to the default and go on from there.  But I always keep at least one "happy" kernel, maybe two.

---

### Post by 1clue on 2011-07-17
BTW, if you ask on the Gentoo forum and you get pappy_mcfae, who seems to specialize in kernel compiling and is the owner of kernel-seeds.org, listen to what he says, do it that way and THEN try to mess around with your own ideas.

If you get the attention of Neddy Seagoon you can bank on just about anything the guy says.  He really does know it all.

---

### Post by bodhi.zazen on 2011-07-17
> **1clue said:**
> I bounce back and forth between Gentoo and Ubuntu.

You're making this much too complicated.

Most drivers are bundled into the kernel source.  If you want a proprietary driver then you need to go look for it on the Internet, but if you're using any sort of standard PC hardware then the kernel source has enough to get you going.

The rest of the system accesses the drivers in a standard Linux way.  The driver itself is what cause the hardware's specific properties to work with the standard API of the operating system.  Once you get the driver working and the protocols you want to use set up in the kernel, then the rest of the OS works with that.

Might help to start at [http://www.kernel-seeds.org](http://www.kernel-seeds.org) where you can get a basic kernel config and then modify it to your hardware.

Figure on it taking more than one try.  Even after you get proficient at compiling and installing your kernel, you will probably sit there for hours and tweak a setting just to see what happens.

Safety:
Always keep one known-to-work kernel in your system, preferably as the default boot.  Otherwise you have to boot from the installer CD, mount your partitions and chroot into your environment and try again.  If you can boot semi-normally then you can move your new kernel to the default and go on from there.  But I always keep at least one "happy" kernel, maybe two.

Those kernel seeds are great, but they are fairly minimal ;)

---

### Post by 1clue on 2011-07-17
> **bodhi.zazen said:**
> Those kernel seeds are great, but they are fairly minimal ;)

Yeah, I noticed that too.  But it got me going for my first i7 kernel compile (the previous was the p4 I had still been using up until then) and then I started playing from there.

FWIW much of what I was compiling into the kernel thinking it was necessary wasn't necessary at all.  You need support for YOUR hardware, not anybody else's.  You need support for the specific protocols YOU need, and nothing else.  Pappy makes a good minimalist kernel that has support for most end users just running a Linux box.

I REALLY like that approach.  Think of it this way:  If an option is not turned on when you compile the kernel, then it doesn't even exist in the kernel you built.  If it's not there, then it can't be hacked.

Minimalism is a great place to start when compiling a kernel.

And for the record, the .config you download from kernel-seeds is NOT a functional configuration.  It has no hardware support, so it won't run until you add support for your hardware.

Good luck and have fun.

---

### Post by ClientAlive on 2011-07-17
> **1clue said:**
> 
Most drivers are bundled into the kernel source.  If you want a proprietary driver then you need to go look for it on the Internet, but if you're using any sort of standard PC hardware then the kernel source has enough to get you going.


There it is! Exactly where my confusion had layed. It was like that thing, "Where in the world is Carmen Sandiego?" Where in the Linux is my driver? And you answered it for me. Easy peasy. Thank you.


> **1clue said:**
> BTW, if you ask on the Gentoo forum and you get pappy_mcfae, who seems to specialize in kernel compiling and is the owner of kernel-seeds.org, listen to what he says, do it that way and THEN try to mess around with your own ideas.

If you get the attention of Neddy Seagoon you can bank on just about anything the guy says.  He really does know it all.

Thanks,

I have a tab open to kernel-seeds from last night and I've heard a little bit about this Pappy character ;)  I simply need to understand a couple key things (like the question about drivers) before I can possible dig into this - and I just hadn't been seeing it in the documentation. Maybe it's there and I just missed it, I don't know, but you cleared that confusion for me. Thanks.

I have a thread at the Gentoo forums too and Neddy is there. I think these guys are getting a little impatient with me but I have to understand a couple key things or how can I possibly be competent when I do it for real?

Anyhoo . . . thanks guys. Sorry if I'm a little short with ppl today. It's frustrating cause I don't have as much time for these things as I would like to spend on them; and it seems like things take forever to get accomplished.

Have a great Sunday afternoon (or whatever it is in your time zone).


Sincerely,
Jake

---

### Post by ClientAlive on 2011-07-17
> **1clue said:**
> Yeah, I noticed that too.  But it got me going for my first i7 kernel compile (the previous was the p4 I had still been using up until then) and then I started playing from there.

FWIW much of what I was compiling into the kernel thinking it was necessary wasn't necessary at all.  You need support for YOUR hardware, not anybody else's.  You need support for the specific protocols YOU need, and nothing else.  Pappy makes a good minimalist kernel that has support for most end users just running a Linux box.

I REALLY like that approach.  Think of it this way:  If an option is not turned on when you compile the kernel, then it doesn't even exist in the kernel you built.  If it's not there, then it can't be hacked.

Minimalism is a great place to start when compiling a kernel.

And for the record, the .config you download from kernel-seeds is NOT a functional configuration.  It has no hardware support, so it won't run until you add support for your hardware.

Good luck and have fun.


Thanks 1clue. I'm sure I will  :D

---

### Post by 1clue on 2011-07-17
The best thing to do is just dive in.  Count on your first one or two installations to be bad ones, because Gentoo is NOT a novice distribution.  Those guys might be a bit frustrated with you, but they are good guys.

Try to read ALL the documentation, starting with the Gentoo Handbook, and go from there.  Don't skip anything unless you are specifically told to skip it, and if you're confused then read any links they point to before going on.

With Pappy's site, you can't assume that even one paragraph is irrelevant.  Start paying attention right away.

---

### Post by ClientAlive on 2011-07-17
> **1clue said:**
> The best thing to do is just dive in.  Count on your first one or two installations to be bad ones, because Gentoo is NOT a novice distribution.  Those guys might be a bit frustrated with you, but they are good guys.

Try to read ALL the documentation, starting with the Gentoo Handbook, and go from there.  Don't skip anything unless you are specifically told to skip it, and if you're confused then read any links they point to before going on.

With Pappy's site, you can't assume that even one paragraph is irrelevant.  Start paying attention right away.

Right on 1clue. I am reading up on some concepts to help me get a better idea of what will suit my purposes best and how to approach this.

The truth is, there are a lot of things I haven't been telling - about what my intentions are/ what I'm shooting for. It would just be too much to get into. Really though, this is not 'just' for the learning experience (although it is that too). It is also to set up a system by which I can begin development of an idea I've had.

I know this thread was not started on this but my latest question now is whether setting up a dual boot system with grub chain loading is possible after the compile of the first system (in this case Gentoo => Xen).

I'd like to end up with Gentoo => Xen on one partition and some development (platform?) on the other (possibly running grml but need to look into grml more). This is important to know because this whole build thing is going to take a long time and effort and I don't want to just do it over for the sake of doing it over. If I have to do it over a couple times because I make mistakes and that's what it takes, that's cool; but, I'd like to approach it from the right angle to begin with too. It's that "right angle" that I think I'm nearing the end of now.

So now I need to discover the right way to approach the whole grub/ chain load thing.

In case anyone is interested, here are a few of the things I'm looking at now:

[http://swift.siphos.be/linux_sea/](http://swift.siphos.be/linux_sea/)
[http://lennartb.home.xs4all.nl/bootloaders/node3.html](http://lennartb.home.xs4all.nl/bootloaders/node3.html)
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)
[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)
[http://www.cs.iastate.edu/~cs554/NOTES/Ch11-1.pdf](http://www.cs.iastate.edu/~cs554/NOTES/Ch11-1.pdf) (for use in the "idea" not the build)

And the usual googling that comes with sorting through it all. The last one I'll open a tab on (just before firing up that machine to do the build) will be the Gentoo manual. At that point I'll be settling in for a nice long compile.

Thanks for your help.


Jake
--------------

Edit:

From [http://lennartb.home.xs4all.nl/bootloaders/node3.html](http://lennartb.home.xs4all.nl/bootloaders/node3.html) it looks like I may be able to add grub on top of the build later.

I guess it's either Grub => lilo (a) or lilo (b) OR it's grub => grub (a) or grub (b).

Looks like there's pros and cons to either configuration.

---

### Post by 1clue on 2011-07-17
Right with you all the way to the ch11 stuff.

First bit of advice:  Don't build a castle.  Build a house first.

I think you're over-complicating things.  Everything up to but not including the distributed filesystems and Xen is going to be covered in the Gentoo Handbook, just the documentation you're referencing might give you a bit more in-depth understanding.  The Xen stuff has its own documentation specifically for Gentoo.

Do yourself a favor and forget entirely about the distributed stuff until you get more comfortable with Linux.

Another thing is, your guest OS isn't usually on a filesystem, it's a file ON a filesystem.  Meaning your host OS can put the whole VM into a different directory.

Personally what I would do is set up something extremely reliable and easy to maintain as your Xen host.  Then set up however many VMs as you need to either learn from or build your end system.

---

### Post by ClientAlive on 2011-07-17
> **1clue said:**
> Right with you all the way to the ch11 stuff.

First bit of advice:  Don't build a castle.  Build a house first.

I think you're over-complicating things.  Everything up to but not including the distributed filesystems and Xen is going to be covered in the Gentoo Handbook, just the documentation you're referencing might give you a bit more in-depth understanding.  The Xen stuff has its own documentation specifically for Gentoo.

Do yourself a favor and forget entirely about the distributed stuff until you get more comfortable with Linux.

Another thing is, your guest OS isn't usually on a filesystem, it's a file ON a filesystem.  Meaning your host OS can put the whole VM into a different directory.

Personally what I would do is set up something extremely reliable and easy to maintain as your Xen host.  Then set up however many VMs as you need to either learn from or build your end system.

Ohhh . . . Ok . . .

Sounds like sound advice. I suppose I could run everything else in a vm anyhow. Maybe that's a better option.

I'm not sure any of it matters now anyhow. I think I killed my machine somehow, so, party's over for now I gues - unless I get it working. It powers up but there is no output; and, apparently, no bios or the bios is not loading. I'm gonna start another thread about that though. I don't think it's right to keep shifting this one all over the place. I can paste the link to the other thread here though, in case you want to check it out. It appears pretty gruesome though.    ](*,)
--------------------------

Edit:

[http://ubuntuforums.org/showthread.php?p=11058256#post11058256](http://ubuntuforums.org/showthread.php?p=11058256#post11058256)

---

### Post by 1clue on 2011-07-17
When you're experimenting, nothing beats a VM.  You can reach a stable spot, back it up to another directory and then go on.  If you mess it up, it's 2 minutes to get back to your last stable point.

---

### Post by bodhi.zazen on 2011-07-17
Actually building a custom kernel is much easier these days.

I highly suggest you read this (short version)

[http://irtfweb.ifa.hawaii.edu/~denault/notes/hints_compiling_kernels.html]("http://irtfweb.ifa.hawaii.edu/%7Edenault/notes/hints_compiling_kernels.html")

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch33_:_Modifying_the_Kernel_to_Improve_Performance](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch33_:_Modifying_the_Kernel_to_Improve_Performance)

With modules, make sure you underestand the differences between N , M , and Y.

And this (long version) : [http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

In particular see: [http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f](http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f)

> 
Most people uses the kernel shipped by distros - and that's good. But  some people like to compile their own kernels from kernel.org, or maybe  they like following the Linux development and want to try it.  Configuring your own kernel, however, has become a very difficult and  tedious task - there're too many options, and some times userspace  software will stop working if you don't enable some key option. You can  use a standard distro .config file, but it takes too much time to  compile all the options it enables. 
 To make the process of configuration easier, a  new build target has been added: make localmodconfig. It runs "lsmod" to  find all the modules loaded on the current running system. It will read  all the Makefiles to map which CONFIG enables a module. It will read  the Kconfig files to find the dependencies and selects that may be  needed to support a CONFIG. Finally, it reads the .config file and  removes any module "=m" that is not needed to enable the currently  loaded modules. With this tool, you can strip a distro .config of all  the unuseful drivers that are not needed in our machine, and it will  take much less time to build the kernel. There's an additional "make  localyesconfig" target, in case you don't want to use modules and/or  initrds.The trick is to first remove (unload) as many modules as possible =)

See also : [https://bbs.archlinux.org/viewtopic.php?id=103406](https://bbs.archlinux.org/viewtopic.php?id=103406)

So use ```
make localmodconfig
```Alternately you can use

```
make localyesconfig
```If you understand the difference between those tow commands, you are ready to go =)

This will generate a custom configuration file based on your loaded modules, and save a great deal of time.

---

### Post by handy on 2011-07-18
Wow! That's a huge improvement to how it used to be (at least 3+ years ago) when I was playing around with Gentoo.

Thanks for posting that bodhi.zazen.

---

### Post by ClientAlive on 2011-07-18
> **bodhi.zazen said:**
> Actually building a custom kernel is much easier these days.

I highly suggest you read this (short version)

[http://irtfweb.ifa.hawaii.edu/~denault/notes/hints_compiling_kernels.html]("http://irtfweb.ifa.hawaii.edu/%7Edenault/notes/hints_compiling_kernels.html")

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch33_:_Modifying_the_Kernel_to_Improve_Performance](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch33_:_Modifying_the_Kernel_to_Improve_Performance)

With modules, make sure you underestand the differences between N , M , and Y.

And this (long version) : [http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

In particular see: [http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f](http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f)

The trick is to first remove (unload) as many modules as possible =)

See also : [https://bbs.archlinux.org/viewtopic.php?id=103406](https://bbs.archlinux.org/viewtopic.php?id=103406)

So use ```
make localmodconfig
```Alternately you can use

```
make localyesconfig
```If you understand the difference between those tow commands, you are ready to go =)

This will generate a custom configuration file based on your loaded modules, and save a great deal of time.


OH, now that sounds neat! I'd bet I can run Ubuntu live from a cd on that machine with dd'ed drives, plug a usb in to save the output then take those files and use them for my kernel config? Something like that anyway?

That would be interesting.

Thanks bodhi.

---

