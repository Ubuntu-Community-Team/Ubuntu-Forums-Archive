---
title: "What makes Arch so much faster than most other distros?"
date: 2008-02-25
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-02-25
I'm very curious to know why Arch is supposedly faster.

Is it something that happens during the installation?

Or does Arch have some secret that other distros don't know?

You can be as technical or as lay-person as need be in your explanation.

---

### Post by PurposeOfReason on 2008-02-25
Arch comes with less bloat and because everything is more vanilla, less of everything has to be loaded. It also has processor specific packages for i686 (which anything PII and newer is I believe) and x86_64 to make them optimized.

---

### Post by Rumor on 2008-02-25
The Arch kernel is optimized for i686 / x_64 architecture so it gains some significant speed there, I believe.

It is certainly lighter in the amount of system resources it uses. When I was dual booting Arch and Ubuntu, I noticed a difference in speed that I chalked up to memory usage. Ubuntu was using as much as a third more memory at idle over Arch. Both systems were running the same desktop environment and the same daemons. Ubuntu was just eating more resources doing so.

According to one of the Arch developers, it is the cacti  that make it so fast . . . [http://bbs.archlinux.org/viewtopic.php?id=22856](http://bbs.archlinux.org/viewtopic.php?id=22856)

---

### Post by mips on 2008-02-25
I don't really care why, I just know it is fast as snot and that makes me a happy camper!

---

### Post by ahaslam on 2008-02-25
> **mips said:**
> I don't really care why, I just know it is fast as snot and that makes me a happy camper!

;)

---

### Post by D-EJ915 on 2008-02-25
everything is compiled with more optimizations

---

### Post by fwojciec on 2008-02-25
The optimizations in Arch are not that complicated.  This is what is used for the 32bit version:
> CARCH="i686"
CHOST="i686-pc-linux-gnu"
CFLAGS="-march=i686 -mtune=generic -O2 -pipe"
CXXFLAGS="-march=i686 -mtune=generic -O2 -pipe"

This is for Arch64:
> CARCH="x86_64"
CHOST="x86_64-pc-linux-gnu"
CFLAGS="-march=x86-64 -mtune=generic -O2 -pipe"
CXXFLAGS="-march=x86-64 -mtune=generic -O2 -pipe"

---

### Post by Pogeymanz on 2008-02-25
So, if all processors Pentium 2 and up are 686, why don't all the main distros optimize for that?

Who runs Ubuntu or Fedora on a Pentium 1? Shouldn't all modern distros be made for 686?

---

### Post by fwojciec on 2008-02-25
> **EmosSuck777 said:**
> So, if all processors Pentium 2 and up are 686, why don't all the main distros optimize for that?

Who runs Ubuntu or Fedora on a Pentium 1? Shouldn't all modern distros be made for 686?

Maybe most people in the US use relatively new hardware -- but this is definitely not the case in the rest of the world, especially the developing world.  Also, people often tend to use older machines as servers, for example; Arch is designed as a desktop distro -- Ubuntu and Fedora are not.

---

### Post by bwtranch on 2008-02-25
[QUOTE=fwojciec;4404922]
fwo mentioned the server issue and I just had to say that lower level machines are great with other (smaller) kernels. Actually, the kernel is the same, it's what you compile into it. An Arch kernel will run faster than my Gentoo simply because it does not have to perform as many read/write operations, because it is less loaded (unlike me). This is an over-simplification, but it is basically true. There are a lot of other thing s that go into this, but, almost always, the lighter the load, the faster the machine.
I have been testing a Gentoo based distro called Sabayon and I like it, but it doesn't compare with the speed of Arch.I just wanted to see some things about LVM and installs that by default. So, I'm playing in the Gentoo sandbox for now, ...I'll be back to Arch in a week or so.Edit: Gee my spelling sucks, sorry it's been a long day in the wind.

---

### Post by mips on 2008-02-26
> **bwtranch said:**
> I just wanted to see some things about LVM and installs that by default. So, I'm playing in the Gentoo sandbox for now, ...I'll be back to Arch in a week or so.

Are you going to use LVM in Arch? If you are the I would advise you to use the sabayon cd to setup the LVM for arch. Doing it in arch via the cli can be a bit of a pain.

---

### Post by Majorix on 2008-02-27
I believe it's a secret formula, like with Cola :D

---

### Post by marscay on 2008-02-28
not only does it require less memory, i'm finding Arch a hell of alot more stable in X not to mention loads faster (compiz + firefox in particular).

i've probably got as many daemons running as i do with ubuntu and using the same ATI 8.2 proprietary drivers.

next thing is to whack virtualbox on and see how that runs versus ubuntu.

i guess it's faster because there's less bloat to begin with and the default compiler hits i686 only.

---

### Post by kpkeerthi on 2008-02-28
> **marscay said:**
> not only does it require less memory, i'm finding Arch a hell of alot more stable in X not to mention loads faster (compiz + firefox in particular).

i've probably got as many daemons running as i do with ubuntu and using the same ATI 8.2 proprietary drivers.

next thing is to whack virtualbox on and see how that runs versus ubuntu.

i guess it's faster because there's less bloat to begin with and the default compiler hits i686 only.

I agree. X has "never" crashed on me even after, probably, five kernel upgrades I have been through with nvidia proprietory driver. I ubuntu, i had to re-install the driver every time there was a kernel upgrade.

And I can't be more happy with the speed of VirtualBox (running Gutsy :) ) in Arch.

---

### Post by regbsn on 2008-03-03
Can Ubuntu be optimized for i686?
If so, how?

If it is not too difficult, a how-to thread would make a great sticky!!!:)

---

### Post by mips on 2008-03-03
> **regbsn said:**
> Can Ubuntu be optimized for i686?
If so, how?

If it is not too difficult, a how-to thread would make a great sticky!!!:)

Yes it can but that means you will have to compile everything from scratch.

---

### Post by regbsn on 2008-03-03
So... this is not an option for a n00b, huh?

---

### Post by mips on 2008-03-03
> **regbsn said:**
> So... this is not an option for a n00b, huh?

Personally I would not go that route as you would have to compile every single package from scratch. If you want to compile everything from scratch go Gentoo or else just use Arch fo precompile i686 binaries.

You are just going to make life very difficult for yourself but thats my opinion.

---

### Post by K.Mandla on 2008-03-03
If I could add on, personally I don't recompile Ubuntu. I think it defeats the purpose; I see Ubuntu as a generalized, one-size-fits-all distro that will 99 percent of the time work with any machine you throw at it.

Recompiling Ubuntu, to me, would make things faster, undoubtedly, but you lose the premise. 

If you want a distro that's tuned to your machine, think about distros that are prepared or intended for that. Arch is perfect for anything i686-ish, and you save yourself the work of compiling. If you want to get more specific (I regularly do), try something like Gentoo or LFS.

---

