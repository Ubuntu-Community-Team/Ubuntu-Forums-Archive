---
title: "VLC installed, NOT playing anything"
date: 2012-05-21
forum: Apple Hardware Users
---

### Post by Kanesodi on 2012-05-21
Hello All :)

I have an iBook which I use as a videoscreen. Basicly I installed Ubuntu 8.04 PPC command-line system (very basic), xorg, openbox and VLC 0.8.6. It worked great. Since I wasn't happy with the web-interface of VLC 0.8.6 I decided to update the iBook.

I never upgrade, but do a clean install. This time I installed Ubuntu 12.04 PPC command-line system, xorg, openbox and VLC 2.0.1. Not much has changed, except that VLC doesn't play anything. It keeps crashing and telling me the following:

> VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
[[COLOR=Lime]0x100bc8f0[/COLOR]] main libvlc debug: translation test: code is "C"
Warning: your CPU has Altivec instructions, but not your operating system.
                   some optimizations will be disabled unless you upgrade your OSAfter some research I kept wondering if "Altivec" might be the problem. As the warning states, my hardware and VLC are *Altivec *aware but Ubuntu isn't. I found this message: [http://lists.debian.org/debian-powerpc/2009/04/msg00031.html](http://lists.debian.org/debian-powerpc/2009/04/msg00031.html) which states:

> On Apr 05 2009, Gunther Furtado wrote: 
> I am getting a lot of Illegal Instruction complains from VLC (whenever 
> I ask it to show me video).  

You should already know this, but it sounds like an altivec enabled program running in a non-altivec enabled machine.And now I'm lost, how do I fix this?

---

### Post by Kanesodi on 2012-05-27
Not sure why nobody replied. Today I got VLC working on iBook G3 300Mhz blabla.

After the post above, I first installed mplayer, to see if that would work and if not, which errors mplayer would give me. Unfortunately mplayer gave the same clues as VLC, namely that there must be something wrong with cpu configs. 

Since 12.04 uses smp kernel, I searched to see if I can somehow let the kernel know that my system has a single core CPU. I came across "maxcpu=1" which you can add to yaboot.conf. That didn't work either. So I was back to the  Altivec issue.

Using this link: [http://lists.debian.org/debian-powerpc/2011/06/msg00066.html](http://lists.debian.org/debian-powerpc/2011/06/msg00066.html) and this link: [http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile) I managed to compile VLC using  [FONT=monospace]
[/FONT]
```
./configure --disable-altivec --disable-optimizations
```one note: compiling VLC 2.0.1 on a 300Mhz system = SLOW! :P

---

