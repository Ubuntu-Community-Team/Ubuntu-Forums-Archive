---
title: "Why so many kernels are maintened same time?"
date: 2013-03-03
forum: Any Other OS
---

### Post by deri on 2013-03-03
Why so many kernels are developed same time? Would think that is just waste of time. Adding same peace of code to all currently active kernels.

---

### Post by tgalati4 on 2013-03-03
Only one kernel is developed at [http://kernel.org](http://kernel.org) but each distro takes it and adds patches to make it work better.  For Ubuntu, security patches get pushed into older kernels that are still maintained--like the Long Term Support, LTS 12.04.  It can be a lot of work, but it's not a waste of time if there is a major security vulnerability and it affects your machine.

Most of the distro/kernel building is done automatically, but the testing has to be done by you and me.  Which is why these forums are helpful.  When something doesn't work the way you expect, you have to start looking at what has changed.  It's not a perfect system, but it's the only system we have.

Consider the alternatives using Windows or Mac OSX.

---

### Post by jazzabrotha on 2013-03-04
Adding on, how do the kernel mainteners decide which kernels will become stable kernels? Sorry if I hijacked this thread.

---

### Post by BBQdave on 2013-03-04
> **jazzabrotha said:**
> Adding on, how do the kernel mainteners decide which kernels will become stable kernels? Sorry if I hijacked this thread.

If I understand what you are asking...

A Kernel Linux is only released when stable. In Linux distros like Fedora, the Kernel Linux is rapidly evolving, as Fedora quickly updates the new Kernel Linux to the current Fedora distro release.

In Linux distros like Debian, what Ubuntu is based on, they choose a Kernel Linux for long term support, and patch it - maintain it for their current distro release.

I switched from Debian 6 to Fedora 16, and have updated Fedora releases to the current Fedora 18. Honestly, Debian and Fedora are both incredibly stable. So if you like a solid distro with little change in applications over time, go with Debian. If you want the latest and greatest applications, go with Fedora.

Part of what motivated my switch from Debian 6 to Fedora 16 - new hardware. I needed the updated Kernel Linux that was in Fedora 16 for full function of my new hardware. I am excited to try out Debian 7, when released, as the Kernel Linux in Debian 7 will support my new hardware.

---

