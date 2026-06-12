---
title: "Rebuild a package... why?"
date: 2008-10-23
forum: Arch and derivatives
---

### Post by whitefort on 2008-10-23
Hi.

After yesterday's big Arch update, I found all sorts of stuff not working - totem, tracker, and one or two other things.

Following a hint from a forum message, I (finally) sat down and read about ABS, then rebuilt the non-functioning packages.

And they've been working perfectly.

My question... uh, what did I actually DO?  How is rebuilding, say, Tracker from source and re-installing it any different than just reinstalling via pacman?

This is non-urgent - like I say, everything's working again, but in the interests of extending my knowledge of Linux, Arch, and my PC, I'd be interested to know why a rebuild works and a re-install doesn't.

Does the rebuild produce a more up-to-date version, or does it communicate with the rest of the installation better?  :confused:

Yours sincerely,

Clueless in Ireland.

---

### Post by fwojciec on 2008-10-23
Let me see if I can explain this:

Package X depends on package Y.
When X is packaged it is built against the libraries (*.so files) provided by package Y.
Now, the package Y gets updated, and the new version of Y has new versions of libraries (*.so files) -- the result is that package X stops working, because it is looking for the old set of libraries that got replaced during the upgrade of Y.
Rebuilding X basically means that package X will look for the libraries provided by the current version of package Y -- the currently installed versions of libraries are linked during the build process.

Normally all this rebuilding work is done by Arch devs, but in some cases, especially for [community] packages, or if you're using [testing], there can be a delay between when package Y is upgraded and when package X is rebuilt against the new set of libraries.

---

### Post by whitefort on 2008-10-23
Thanks, that explained it in a way that finally made sense to me!

So, if I had done nothing, another update would have come along and fixed the problem anyway...  Which seems to be what happened, because both the packages I had to rebuild appeared in this morning's update.

But in spite of all the tension and panic, it was good!  I've been meaning to read up on ABS ever since I installed Arch, and this was the incentive I needed to finally do it!

Thanks again!

---

### Post by crimesaucer on 2008-10-23
> **whitefort said:**
> Thanks, that explained it in a way that finally made sense to me!

So, if I had done nothing, another update would have come along and fixed the problem anyway...  Which seems to be what happened, because both the packages I had to rebuild appeared in this morning's update.

But in spite of all the tension and panic, it was good!  I've been meaning to read up on ABS ever since I installed Arch, and this was the incentive I needed to finally do it!

Thanks again!


Another reason people use the ABS and the AUR is to use C[XX]FLAGS.


You have to edit your /etc/makepkg.conf to use custom flags for your processor.


I try to only use the ABS/AUR for my Arch install, occasionally I cheat with a binary if I have trouble building the package.


With ABS/AUR and the pacbuilder app, you can have a Arch system similar to Gentoo.

---

### Post by fwojciec on 2008-10-24
> **whitefort said:**
> Thanks, that explained it in a way that finally made sense to me!

So, if I had done nothing, another update would have come along and fixed the problem anyway...  Which seems to be what happened, because both the packages I had to rebuild appeared in this morning's update.

But in spite of all the tension and panic, it was good!  I've been meaning to read up on ABS ever since I installed Arch, and this was the incentive I needed to finally do it!

Thanks again!

You're welcome :)

Usually these sorts of problems get fixed quickly -- devs have actually gotten very good at managing those complicated rebuilds (another big one is coming up, I think, with python being upgraded to 2.6).  Still, there is always a chance that some packages will not be rebuilt immediately.  If that happens you can always report the bug on the bug tracker (there is a separate section for [community] packages).

By the way -- if you use yaourt then rebuilding a package is as easy as typing yaourt -Sb package, the (ingenious) script will do the rest.  

Which is not to discourage the use of ABS -- of course.  ABS can be really powerful, since it enables you to customize Arch beyond what the standard set of packages can provide.

---

### Post by whitefort on 2008-10-24
> **crimesaucer said:**
> Another reason people use the ABS and the AUR is to use C[XX]FLAGS.

:) I have absolutely no idea what you just said!  :)

So little time, so much to learn...

Arch certainly seems to be a good 'learning' distro.  I'm having a lot of fun with it (well, I'm having fun during the moments that I'm not terrified that I've totally messed up my system...

(and my computer's system too! :) )

Thanks!

---

### Post by whitefort on 2008-10-24
> **fwojciec said:**
> if you use yaourt then rebuilding a package is as easy as typing yaourt -Sb package, the (ingenious) script will do the rest. 

Yaourt is something else which is totally new to me.  I'll look it up.

BTW, I love the ninja bears pic - is there a full-size version of that anywhere?

---

### Post by fwojciec on 2008-10-24
> **whitefort said:**
> BTW, I love the ninja bears pic - is there a full-size version of that anywhere?

I think this is where I got it from initially: [http://http://images.usefulzero.com/s/ninja-bears/]("http://http://images.usefulzero.com/s/ninja-bears/")

---

### Post by whitefort on 2008-10-24
Thanks - I really love that pic!

---

### Post by crimesaucer on 2008-10-24
> **whitefort said:**
> :) I have absolutely no idea what you just said!  :)

So little time, so much to learn...

Arch certainly seems to be a good 'learning' distro.  I'm having a lot of fun with it (well, I'm having fun during the moments that I'm not terrified that I've totally messed up my system...

(and my computer's system too! :) )

Thanks!

Compiler flags are for building a package from source for different architectures, or with different optimizations:

[http://wiki.archlinux.org/index.php/Makepkg.conf](http://wiki.archlinux.org/index.php/Makepkg.conf)


I would show you this Gentoo page, but their site is down: [http://gentoo-wiki.com/CFLAGS#-Os](http://gentoo-wiki.com/CFLAGS#-Os)


Here is a list of C[XX]FLAGS and different optimizations: [http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)



This is what the Arch and Gentoo page say to use for safe C[XX]FLAGS for an AMD Turion 64x2 (I think the Gentoo page uses "-msse3"):

```
CHOST="x86_64-pc-linux-gnu"
CFLAGS="-march=athlon64 -O2 -pipe"
CXXFLAGS="${CFLAGS}"

```

and the MAKEFLAGE of:

```
MAKEFLAGS="-j3"

```


..... but since my Turion 64x2 TL-60 is newer, and has SSE3 available: [http://en.wikipedia.org/wiki/List_of_AMD_Turion_microprocessors#.22Trinidad.22_.2890_nm.29](http://en.wikipedia.org/wiki/List_of_AMD_Turion_microprocessors#.22Trinidad.22_.2890_nm.29)


.... I write in the "-msse3" option to enable it. I also use "-Os" instead of "-O2".


this is what I use in my /etc/makepkg.conf:

```

CARCH="x86_64"
CHOST="x86_64-unknown-linux-gnu"

#-- Exclusive: will only run on -march=x86-64 
# -march (or -mcpu) builds exclusively for an architecture
# -mtune optimizes for an architecture, but builds for whole processor family
CFLAGS="-march=athlon64 -msse3 -Os -pipe"
CXXFLAGS="-march=athlon64 -msse3 -Os -pipe"
#-- Make Flags: change this for DistCC/SMP systems
MAKEFLAGS="-j3"

```


I think these are pretty safe to use, I wish I knew more about the other settings available..... I'm still learning a lot about kernels and building a system from source.

---

