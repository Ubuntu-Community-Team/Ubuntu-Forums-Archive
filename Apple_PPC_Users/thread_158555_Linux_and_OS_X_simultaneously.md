---
title: "Linux and OS X simultaneously"
date: 2006-04-11
forum: Apple PPC Users
---

### Post by MrFrodo on 2006-04-11
Is it possible to run (K)Ubuntu and OS X at the same time on the same machine? This would be great for Web dev...

TIA

---

### Post by nuke on 2006-04-11
That would be rather exciting.  I don't know but was thinking about this issue over the last week when Apple announced BootCamp.

I believe the place to look is to see if Xen will run on the PPC version of (K)Ubuntu.  Then it might be possible.

---

### Post by nuke on 2006-04-11
You may wish to look at [http://www.free.oszoo.org/download.html]("http://www.free.oszoo.org/download.html") or [http://www.kberg.ch/q/]("http://www.kberg.ch/q/").

---

### Post by hentaidan on 2006-04-11
Or you could always try [Mac on Linux]("http://maconlinux.org/"), runs my MacOSX install at near native speeds. Worked with no hassle in Dapper.

---

### Post by nuke on 2006-04-12
Or even this one.  While this looks interesting at $39.95, it isn't exactly what you are looking for since it is running Linux(K)Ubuntu and/or Windows within virtual environments in MacOSX. [http://www.parallels.com/en/products/workstation/mac/]("http://www.parallels.com/en/products/workstation/mac/")

---

### Post by ZactheDragon on 2006-04-12
If you partition the hard drive using an application on the MAC under Applications>Utilities>Disk  Utility. And then install an operating system on each partition that might work.

What I have done on my Powermac G4 is just stuck a second hard drive in and installed an operating system on each and just boot up holding C or R and it asks what I want to boot from.

---

### Post by 3rdalbum on 2006-04-13
[QUOTE=ZactheDragon]If you partition the hard drive using an application on the MAC under Applications>Utilities>Disk  Utility. And then install an operating system on each partition that might work.

What I have done on my Powermac G4 is just stuck a second hard drive in and installed an operating system on each and just boot up holding C or R and it asks what I want to boot from.[/QUOTE]

I think what the original poster was talking about was a way to run OS X in an Ubuntu window, or Ubuntu in an OS X window.

If you have a PPC Mac, you could run Ubuntu through Virtual PC. If you have an Intel Mac, try using Parallels Workstation for OS X to run Ubuntu - the other way around probably won't work unless you have the "beige box" hacked version of OS X. If you're comfortable with recompiling the kernel, you could use Mac-On-Linux (on PowerPC)

---

### Post by youbuntoo on 2006-04-19
i'm actually running ubuntu side by side w/ OS X on my new mac book pro.  parallels beta 4 is working fine, couple bugs till, but getting there.  anyone else had luck w/ it?

---

### Post by 3rdalbum on 2006-04-20
Just to reply to an earlier poster: Xen won't run Ubuntu. With Xen, the guest OS needs to be aware that it's NOT running on the actual hardware. As you may have already heard, Edgy (Dapper + 1) will support Xen.

---

### Post by DJ_Max on 2006-04-22
[QUOTE=3rdalbum]Just to reply to an earlier poster: Xen won't run Ubuntu. With Xen, the guest OS needs to be aware that it's NOT running on the actual hardware. As you may have already heard, Edgy (Dapper + 1) will support Xen.[/QUOTE]
Ubuntu can run under Xen fine.

---

### Post by 3rdalbum on 2006-04-24
Sorry. I must've misunderstood something I read in Linux Format mag...

Then what exactly did sabdfl mean in that Edgy statement?

---

### Post by DJ_Max on 2006-04-24
[QUOTE=3rdalbum]Sorry. I must've misunderstood something I read in Linux Format mag...

Then what exactly did sabdfl mean in that Edgy statement?[/QUOTE]
Well, currently there are no Ubuntu Xen binaries. The closest we have is [xen-tools](http://packages.ubuntu.com/dapper/utils/xen-tools) in Dapper, but you still will need to compile the XenEngine from source manually.

I'm thinking he meant Dapper+1 will have Xen binaries available.

---

### Post by moon47usaco on 2006-05-27
What i have had in mind from the first glimse of boot camp of a simultanious boot...

Rather than having a virtual machine or windowed view of another system running within another sys...

Having more than one system switchable in the same manner that you switch users or sessions...

All systems (or selected systems) boot up at the same time at power on...

Users can log out of a particular session/user like normal per system but from there the user would have the option to further log out of one system and into another...

This would all be fairly complicated and is still a long way off but then again so everyone thought before we could dual/triple boot a mac...


Still dreaming... =]

R

---

