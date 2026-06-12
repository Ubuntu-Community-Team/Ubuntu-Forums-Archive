---
title: "Ubuntu linux kernel on debian?"
date: 2011-05-08
forum: Any Other OS
---

### Post by ccc2007chaos on 2011-05-08
Hi!  I came up with this question: Can I install on Debian the Ubuntu linux kernel? I mean this kernel that has the drivers for my laptop etc.  For the story, I haven't tried anything yet.

---

### Post by wolfen69 on 2011-05-08
If you did that, you would be using ubuntu. What would be the point?

---

### Post by ccc2007chaos on 2011-05-09
The truth is that I'm just searching the linux world for a couple of years by just using it. Now, I want to try something more customized. I really don't know what it'd be the result of installing ubuntu kernel on debian distro but in my mind, I'll have an original debian system but with a different kernel. So, I want to test it. I'll try, although, to search for drivers or patches of the kernel to install them on the debian distro. That's all!  So, is there any place with drivers? I am just asking! I'll search it by my self too! :P

---

### Post by krapp on 2011-05-09
The drivers you're looking for would likely be in the official Debian non-free repos. What exactly are you trying to accomplish? Are you just trying to experiment?

---

### Post by ccc2007chaos on 2011-05-10
Ok. I'll search there too.

Yes, I'm trying to experiment. If you have any suggestions about this too, be my guest and let me know!

thanx

---

### Post by w4rh4wk on 2011-07-11
i have the same mind in rushing through my brain.

the debian system i currently use is very handy and i like it a lot to work with. Mainly it contains stable software, only a few packages are experimental.

Problem is the driver support. I migrated from ubuntu to debian because the debian system itself feels much more organized (mainly because there is no upstart and things like that)
But the kernel which comes with debian doesn't support my hardware as well as the Ubuntu kernel does. So i thought it would be a good combination to keep my system bases and change the kernel.

i once tried to compile the ubuntu kernel from source, but i messed something up i think (system couldn't boot, just black screen)

i was wondering if it would be possible to include the ubuntu repository in debian and install the ubuntu kernel via apt-get.


i know, you people think i am crazy like Frankenstein and would be better off with a full Ubuntu system.

---

### Post by NightwishFan on 2011-07-11
I am sure it is quite possible to download the Ubuntu kernel source and run make-kpkg. Do not try to just install the precompiled Ubuntu debs they are compiled for Ubuntu not Debian.

You will not gain much by doing so though. The only reason to do this would be for the novelty of it.

---

### Post by XubuRoxMySox on 2011-07-12
Just do a "[minimal Ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD")" installation and build your own custom 'buntu! That's like doing a Debian "net install" but with the Ubuntu kernel *and* compatible stuff in the repositories!

-Robin

---

