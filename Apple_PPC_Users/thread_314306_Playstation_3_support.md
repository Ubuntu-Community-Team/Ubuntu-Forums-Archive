---
title: "Playstation 3 support"
date: 2006-12-07
forum: Apple PPC Users
---

### Post by Lars Noodén on 2006-12-07
Does the PPC version of Ubuntu support the new Playstation's architecture fully?  If I understand correctly there are several cores or coprocessors.  It would be important to utilize them.

---

### Post by DarkStarAeon on 2007-09-09
From what I've heard, only Yellow Dog Linux supports the Cell Processors in the PS3, all the rest of the distros use just the PPC processor in the PS3.

Personally, I just bought a PS3 and would absolutely love to have a PS3 optimized version of Ubuntu on it and Flash 9 too, but, I'm pretty sure that's just a dream I'll never see realized since Ubuntu doesn't seem to be doing much in the PPC dept.

---

### Post by DarkStarAeon on 2007-09-09
Hmm, I just found this, I guess they are interested...

[http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)

---

### Post by stmiller on 2007-09-10
[http://psubuntu.com/](http://psubuntu.com/)

---

### Post by DarkStarAeon on 2007-09-10
Seen it, but it just looks like it's regular Ubuntu with instructions on how to install it on PS3. 
I'm talking about one that's tweaked to run beautifully on it.

---

### Post by indelible on 2007-09-11
Actual recent version of Flash running well on a PPC chip?  Surely you jest. :biggrin:

---

### Post by stmiller on 2007-09-11
The support for the hardware of the PS3 does not have anything to do with Ubuntu, or any distro. Work is being done on the Linux kernel for ps3 support. You can configure the latest Linux kernel from kernel.org with

$ make ps3_defconfig

and it will make a PS3 optimized kernel, which can use all parts of the Cell processor.

Search this kernel [changelog]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.23") for 'ps3' for instance. 

So you could install Yellowdog, Fedora, Gentoo, Suse, Debian, or Ubuntu PowerPC and compile a recent kernel for PS3 and it would be 'optimized/tweaked' for the PS3. :popcorn:

I think Ubuntu's PS3 discs are basically a ps3 configured kernel + standard Ubuntu PowerPC. As I understand it, unless software is specifically written for parts of the Cell processor, it will only use dual Powermac G5 CPU crunching speeds.

---

### Post by Lars Noodén on 2007-10-14
[INDENT]
[I]$ make ps3_defconfig

and it will make a PS3 optimized kernel, which can use all parts of the Cell processor[/I].[/INDENT]

Thanks, that looks quite useful.

---

### Post by ssam on 2007-10-14
feisty ps3 cds
[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

you will find gutsy one at [http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/) in a few days (probably).

linux handles multicore processors pretty well, but few applications are threaded enough to use them fully.

the nouveau driver will one day be able to do 3d accelleration on the ps3. currently you will only get 2d. [http://www.phoronix.com/scan.php?page=article&item=876&num=1](http://www.phoronix.com/scan.php?page=article&item=876&num=1)

yellowdog put a lot moer effort into ps3 support. however they usually have older versions of software than ubuntu. also their stuff is redhat based, whereas debian based is best :-)

---

