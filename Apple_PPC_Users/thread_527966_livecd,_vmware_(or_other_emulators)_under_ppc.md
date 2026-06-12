---
title: "livecd, vmware (or other emulators) under ppc"
date: 2007-08-17
forum: Apple PPC Users
---

### Post by supremedalek on 2007-08-17
I would like to create a liveCD that runs in a ppc machine (specifically Mac and RS/6000). if I am going to use ubuntu, what would be the version I should use that will play nice with most PPCs? I am right now running feisty (and very happy with it) in my Cube.  If that does not work, I was thinking on going a bit more primitive and using debian instead. if I do that, I guess I would need to run it under some kinda of emulation.  Now, AFAIK, vmware only runs in a intel Linux box.  Am I mistaken?  What would be other emulator options?

---

### Post by stmiller on 2007-08-17
Yeah you are correct- VMware is x86 only. 

The only PowerPC options are Qemu and Mac-On-Linux. (Xen is being ported to PowerPC, but would require a G5 it looks like. ppc64 only.) 

Mac-on-Linux can run PowerPC Linux, MacOS9, and Mac OS X (including Tiger).

I recommend fetching the latest Mac on Linux from their homepage instead of the package in the Ubuntu repos, which are horribly out of date.

I have never gotten a PowerPC Live Linux cd to boot under qemu but you may have better luck...

---

