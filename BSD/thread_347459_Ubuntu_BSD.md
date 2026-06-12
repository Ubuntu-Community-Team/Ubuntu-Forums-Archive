---
title: "Ubuntu BSD"
date: 2007-01-27
forum: BSD
---

### Post by max.diems on 2007-01-27
Is there a way to get the BSD kernel in Ubuntu repos? If not, can it be added? Debian already does it, so we can just kidnap their packages.

---

### Post by SunnyRabbiera on 2007-01-27
I wouldnt do it myself as it could kill your compy.

---

### Post by max.diems on 2007-01-28
Yes, it *could* kill your computer, but that's the risk ou take. It could be in the not-yet-there "Deadly" repo. A big part of FOSS is choice.

---

### Post by manmower on 2007-01-28
I guess the major issue would be how nice it plays with all the Linux software. I don't know enough about  Debian GNU/kFreeBSD to really have an idea how much the other software had to be altered to work with the BSD kernel. In the ideal scenario of all the software working with the kernel without alteration, the chances of it "killing" your system would be pretty slim considering you could just keep it alongside the Linux kernel and boot into your kernel of choice.

---

### Post by max.diems on 2007-01-28
As I understand it, the BSD kernel can use Linux software, though it won't be as fast as on Linux (or BSD software on BSD)

---

### Post by -Rick- on 2007-01-29
> **max.diems said:**
> As I understand it, the BSD kernel can use Linux software, though it won't be as fast as on Linux (or BSD software on BSD)

You hardly notice any difference, I can happily play ut2004 in freebsd.

---

### Post by angryfirelord on 2007-01-29
> **max.diems said:**
> As I understand it, the BSD kernel can use Linux software, though it won't be as fast as on Linux (or BSD software on BSD)

According to FreeBSD, Linux apps can run close to their native speeds under BSD. It can be enable by adding this to your /etc/rc.conf file:

linux_enable="YES"

I know that Gentoo is working on a FreeBSD kernel port & Debian is working on a Hurd port, but I don't think Ubuntu is doing any of that.

---

### Post by max.diems on 2007-01-30
We should offer it, preconfigured to use Linux apps. IT could be a package, not a full distro. As I said before, Debian already offfers BSD, so we only need to adapt their packages.

---

### Post by 3rdalbum on 2007-02-01
> **max.diems said:**
> We should offer it, preconfigured to use Linux apps. IT could be a package, not a full distro. As I said before, Debian already offfers BSD, so we only need to adapt their packages.

Does Debian offer a BSD package, or a version of the distro based on BSD?

I know that parts of Ubuntu are dependent on Linux-specific stuff (HAL and ALSA, to name a few), so I'd be surprised if Debian/kFreeBSD will work with the exact same packages as Debian/Linux.

---

### Post by xabbott on 2007-02-01
> **max.diems said:**
> We should offer it, preconfigured to use Linux apps. IT could be a package, not a full distro. As I said before, Debian already offfers BSD, so we only need to adapt their packages.

If Debian offers it why not use it? Ubuntu and Debian have different goals and I don't think this is something Ubuntu needs to tackle at all.

---

### Post by max.diems on 2007-02-01
Free CDs. Easier to use.

---

### Post by xabbott on 2007-02-01
> **max.diems said:**
> Free CDs. Easier to use.

Easier how?

---

### Post by mips on 2007-02-02
> **xabbott said:**
> Easier how?

Not sure but maybe he means that you get a full cd/dvd install set of debian which makes it easier for dialup users.

---

### Post by max.diems on 2007-02-02
Also, I'm pretty sure Ubuntu has more configuration tools. Also, Ubuntu people don't think you're inferior for using non-free software. Too many Debian people seem to.

---

### Post by xabbott on 2007-02-02
> **max.diems said:**
> Also, I'm pretty sure Ubuntu has more configuration tools.
wrong.

> **max.diems said:**
> Also, Ubuntu people don't think you're inferior for using non-free software. Too many Debian people seem to.
Generalizations? Inaccurate, you do know the generalizations of Ubuntu users right?

---

### Post by Rounin on 2007-04-18
You know, I've wondered why so many vendors of open-source software seem to prefer Linux over BSD, seeing as BSD's license is much more permissive when it comes to combining proprietary and open-source software.

Sure, it may be a security risk to have users loading more and more binary software onto their systems, but it would seem logical that at least distributions wanting to support proprietary graphics drivers (like, I suppose, nVidia and ATI?) would want to base themselves on BSD and not Linux, so as to avoid the licensing controversy. And then there's gaming. Oh, the gaming.

In the end, do we really want to restrict ourselves to running open-source software? By all means, I wish we could, but can we? I personally would love to see Ubuntu/BSD, anyhow.

---

### Post by Pobega on 2007-04-21
> **max.diems said:**
> Is there a way to get the BSD kernel in Ubuntu repos? If not, can it be added? Debian already does it, so we can just kidnap their packages.

Debian worked extremely hard to get the FreeBSD kernel playing nicely with all of it's components...And I'm not exactly sure if apt-getting the FreeBSD kernel on a Debian Linux system will exactly work, but I do know there is a Debian GNU/kFreeBSD distribution.

---

### Post by tux9656 on 2008-11-04
Hello, everyone.

I also think Ubuntu GNU/kFreeBSD would be a great idea and I would love to see more distros attempt the combining of GNU with diffent kernels. However, the previous poster is correct in saying that it was a lot of work for the debian developers to get the FreeBSD kernel working with the Debian GNU userland.  It's not as simple as booting an existing GNU system with the FreeBSD kernel.  First off, FreeBSD is not designed to have the system installed on ext2/3, xfs, jfs, or ReiserFS.  It needs to be on UFS2.  You will also need the fs tools to support this.  Second, FreeBSD uses different names for the device files and uses different methods to interact with the kernel so applications would have to be moddified to handle this difference.  Also, don't even think about gaming on GNU/kFreeBSD.  At least not yet.  Nvidia's FreeBSD driver expects a FreeBSD userland which is very diffent from GNU.  I do think that if enough distros offer a GNU/kFreeBSD version that Nvidia would release a GNU/kFreeBSD driver.  I do really enjoy playing with Debian GNU/kFreeBSD.  It seems fast and more responsive compared to GNU/Linux.  I especially like the UFS2 filesystem.  It is blazingly fast.  I actually switched a Samba server I have over to Debian GNU/kFreeBSD just because of how much I like the UFS2 filesystem.  If you do decide to give it a try, install it natively and use the i386 build.  It doesn't seem to work well under Virtualbox, and i386 seems to be working better than AMD64.

---

