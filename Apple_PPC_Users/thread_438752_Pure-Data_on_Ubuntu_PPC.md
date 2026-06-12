---
title: "Pure-Data on Ubuntu PPC?"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by myo on 2007-05-10
I've been looking into using Ubuntu on my Powerbook for live performance. If anyone can share their experience with running Pd (or audio in general) on Ubuntu PPC it would be greatly appreciated.

---

### Post by stmiller on 2007-05-10
Hey it works great. For audio work in Linux, it is best to compile the kernel for low-latency and increase the kernel timing. Unfortunately ubuntu does not provide these audio-specific ppc kernels. (They do provide low-latency kernels for x86 and x64).
So compiling the kernel for those things are ideal, but not required I suppose.

The audio latency with a realtime 2.6.18 or higher kernel is astonishingly small. Something like 13 ms or smaller. It's amazing.

Most all usb midi keyboards work with the snd-usb-audio driver, if you have one.

I do random audio work in powerpc linux (I'm a commercial music composer) mostly with cecila and csound and am happy with the results. Jack works with the internal sound chip of the *books, imacs, and powermac G5 machines, as of Feisty.

I haven't used pd very much but am curious to check it out more. Also Ardour 2 looks amazing. It supports more frame rates for syncing audio to video than Logic Pro currently does. But I haven't had a chance to try it out yet.





Anyways, get the latest Feisty release.

---

### Post by myo on 2007-05-11
Cool, thanks for the input. I fear that I'm too much of a nub to compile my own kernel, so I'll have to stick with the stock. I've also decided to stick with Ubuntu since I already know it from my desktop. 

I downloaded the latest Feisty PPC image, and I'm repartitioning my disk for a dual boot now. So I guess I'll post the results in a few days when I get around to configuring everything. 

It's good to hear that audio on Linux is coming along. A long way from when I tried this 4-5 years ago and nothing worked =\  My main worry is that my OS X patches will break and that some of the externals I use  aren't available and/or I'll have to compile them myself. So if I can sort that out it sounds like I might be OK.

---

