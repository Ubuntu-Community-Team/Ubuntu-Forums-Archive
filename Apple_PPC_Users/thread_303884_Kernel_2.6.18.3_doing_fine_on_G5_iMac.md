---
title: "Kernel 2.6.18.3 doing fine on G5 iMac"
date: 2006-11-21
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-21
Yeah!  The stable 2.6.18.3 seems to be working just fine on my G5 iMac running Edgy.  Noticed another bit of G5 goodness in the release notes so I went for it and compiled.

I still used -fno-stack-protector in the BOOTCFLAGS, - I was too lazy to leave it out and see if the compile process complained.

I guess compiling vanilla kernels has it's risks down the road, but I don't know if we really have a road to follow anymore. :)

---

### Post by stmiller on 2006-11-21
Ah, sweet thanks. It's good to have threads like this. If there are any iMac users browsing about ubuntu, they can see that it works.

Check out this page I recently found:

[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

Has lots of good details about what's happening in the kernel releases.

---

### Post by Torrance on 2006-11-21
Yup, same here. 2.6.18.3 works great on my machine - nice splash screen, full fan control, full sound support, etc.

I also added -fno-stack-protector to the BOOTCFLAGS in  arch/powerpc/boot/Makefile without checking if it worked otherwise, but I'm pretty sure that compile problem has only been resolved in 2.6.19.

Yay!

---

### Post by stream303 on 2006-11-21
Forgot to mention that I chicken-ed out and set the Kernel Timer frequency to 1000 hz for desktop use.

Thanks for turning me on to this guys - I'm no longer afraid of compiling.  Ready for Gentoo! :)

Makes me wonder - and before I get thrown out, I just want to say **thanks to the Debian PPC developers**.  When their latest release comes out, I plan to triple boot Debian, Ubuntu, and Gentoo.

So here comes the question - I wonder if Ubuntu PPC support would be easier if *they* switched to Gentoo instead of Debian.  Naive again, I know...  (in the end, we're all one happy Linux family for the most part right?)

---

### Post by stmiller on 2006-11-21
I used Gentoo PPC for awhile before switching to Ubuntu. Gentoo was great, but Ubuntu had more software packages available to install easily. I needed some audio apps, and Ubuntu had them all!

But there is nothing too scary about Gentoo. Even though packages are all compiled from source, it still fetches all dependencies, etc for you. A few config files to get set up is the biggest headache.

I'm sad to say that if PPC Ubuntu is moved off the official servers, I'll probably go back to Gentoo. The packages are well maintained and stable.

---

### Post by stream303 on 2006-11-28
Ok, one breakage point with 2.6.18.2 or 2.6.18.3:

Firestarter.  I don't need it, I just wanted to test it.  Even though I compiled in Netfilter Xtable and IP Tables Support, the system complains that the kernel doesn't have IPtables support.

I'm not a kernel guru, so I'm not going to worry - probably operator error during make menuconfig on my part somewhere.

(although I could have sworn that this was mentioned somewhere else... )

---

