---
title: "Problems to get SMP running on my G4"
date: 2006-09-26
forum: Apple PPC Users
---

### Post by quilty on 2006-09-26
Hello everybody,

when I install Ubunutu (Dapper Drake) from the desktop live cd it only shows one cpu running
```
cat /proc/cpuinfo
```

Now I already read that I need to get the SMP version of the kernel and I thought I did this by installing the ppc32-smp kernel using Synaptic but somehow unbuntu is still booting the old kernel.
My quess is that I need to reconfigure the bootloader but I've no idea how yaboot works since I only worked with grub so far.

Any hints where to start or what to do? I like Ubuntu so far but I really need my 2nd cpu :)

quilty

---

### Post by moof on 2006-10-03
Hi Quilty-

I'm in the same boat myself.  I've installed the SMP version of the kernel via Synaptic and I can find it in my /boot firectory, but the computer is still going on using the original kernel.

So, here's what I think is going on (unofficially):

There are two link files in /boot for the Mac: 'initrd.img' and 'vmlinux'.  These point to their respective versions of kernel files: initrd.img.xxxxxxx-powerpc and vmlinux-xxxxxxx-powerpc  There should be a version in your /boot dir of these files that has -smp tagged on the end, and these files are what we want to point to.

I'm ticked off that Synaptic doesn't seem to do *any* update for YaBoot (the bootloader for PowerPC) when it seems to do quite a bit of stuff for GRUB on the PC.    However, I think it could be as easy as just changing those linked files to point to the SMP versions of the kernel and then just rebooting and seeing what happens.  Alternately, I suppose we could also edit the kernel Boot menu (the second menu in YaBoot after starting up) that could include a list of kernels to boot from.  I've got quite a collection now after trying to get Synaptic to install the darn things for me.

YaBoot actually is pretty well documented, as long as you know where to look.  [This]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml") Howto is pretty good and gets down to the nitty-gritty.  I have yet to do the research myself, but I would think that it could be as simple as editing the list for the kernel menu and just chosing the kernel from there (or even better, make it the default once it's proved stable).

Like I said, this is all unofficial...I'm going from my own working knowledge of Unix and Mac OS X as-is.  My biggest reservation is messing up the link files in /boot or tweaking Yaboot for the worse.  Good luck to us!

---

