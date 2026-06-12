---
title: "Compile Vanilla PPC kernel, Cross compiling and other misc help please."
date: 2009-01-31
forum: Apple Hardware Users
---

### Post by noriek on 2009-01-31
Hello all.

Right, my irrational obsession to get an optimized G3 iMac installation of any flavour, which if i'm honest will be dreadfully slow anyway, has led me to conclude that the best solution is a self compiled PPC kernel from the vanilla source code.

I'm planning to cross compile this on a i686 architecture for speed reasons. 

I'm at the preliminary research stage but if anyone has done this and got any invaluable advice or sources which describe this process I'd appreciate a heads-up. 

In addition my experience of compiling kernels is limited: i've done it previously where I added a module, removed a section of modules (probably ham radio support or something similar) and where I changed the architecture from i386 to i686. This is nothing more than a few mouse clicks under X and so reasonably easy. This time I want to strip everything that's not vital even down to the kernel, for example, having the system recognise the USB flash disc I use with the system but none other (not by design at least, if it happens that the drivers are the same etc then no matter obviously). 

To this end does anyone know where/how I can find out the exact hardware in my iMac DV G3 400Mhz. I mean to chip level so I can support the exact hardware and nothing else.

Secondly, and given my limited kernel experience, are there known instances where the implementation of a type of hardware device relies directly on the system supporting a different type of device? For example: am I right in saying IDE is not supported natively and is emulated using SCSI support???? Is that true and are there anymore examples I'd have to be aware of when choosing what to include in the compile?

A lot of questions there but tidbits in any of those or related areas appreciated. I will of course share the compiled kernel for those who want it!

Thanks

---

