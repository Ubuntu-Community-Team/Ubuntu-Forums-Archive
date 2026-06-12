---
title: "new kernel update"
date: 2009-01-26
forum: Arch and derivatives
---

### Post by kerry_s on 2009-01-26
anyone else get burned on the new kernel update?
mine was screwed on both regular and fallback, so it wouldn't even boot. i'm in the process of reinstalling now. :(

---

### Post by crimesaucer on 2009-01-26
> **kerry_s said:**
> anyone else get burned on the new kernel update?
mine was screwed on both regular and fallback, so it wouldn't even boot. i'm in the process of reinstalling now. :(

I use my own compiled kernel for AMD64.... I install it as a parallel kernel so I can just leave the stock -ARCH one alone.


I did a pacman -Sy kernel26 to upgrade it today but since I never log into that kernel on my grub list I haven't seen if there is anything wrong with it......


I was actually waiting until the 2.6.28.2-1 PKGBUILD is updated in ABS (usually a day or two behind the regular repos)..... so I can build it with AMD64 instead of generic x86_64..... I hope I don't run into any problems.... but I always keep the last 2 kernels as backup (2.6.28.1-ARCHtestAMD2 and 2.6.28-ARCHtestAMD)


I might be uploading an AUR package soon for people that want to build their own parallel kernel with "make menuconfig". Basically the same ABS PKGBUILD and preset/install/config files except that it will have a different name so it doesn't overwrite the default stock 2.6.28-ARCH kernel..... and it also has the "make menuconfig" option so that you can customize.

---

### Post by crimesaucer on 2009-01-26
> **kerry_s said:**
> anyone else get burned on the new kernel update?
mine was screwed on both regular and fallback, so it wouldn't even boot. i'm in the process of reinstalling now. :(

I also forgot to say that it's too bad that happened..... at least Arch only takes an hour to install, configure, and add the important packages.

---

### Post by ghindo on 2009-01-26
I haven't had any issues with the new kernel so far.

---

### Post by smartboyathome on 2009-01-26
> **ghindo said:**
> I haven't had any issues with the new kernel so far.

I haven't had any either.

---

### Post by handy on 2009-01-26
So what is the procedure when you can't boot your Arch system as kerry_s?

Can you boot from the Arch install CD, chroot & then use the standard pacman -U downgrade method?

---

### Post by sisco311 on 2009-01-26
no issues here either.

reinstalling the kernel is not so hard.

---

### Post by kerry_s on 2009-01-26
yaa, i'm backup!

i'm thinking maybe i tweaked to many things and just got bit in the butt. i been trying all kinds of things from the wiki and forum. i'll try and keep it more basic till i get use to arch's little quirks.

question:
i'm not using that testing repo, just the core,extra,community, are there usually problems from updates?

---

### Post by OutOfReach on 2009-01-26
> **crimesaucer said:**
> I use my own compiled kernel for AMD64.... I install it as a parallel kernel so I can just leave the stock -ARCH one alone.


I did a pacman -Sy kernel26 to upgrade it today but since I never log into that kernel on my grub list I haven't seen if there is anything wrong with it......


I was actually waiting until the 2.6.28.2-1 PKGBUILD is updated in ABS (usually a day or two behind the regular repos)..... so I can build it with AMD64 instead of generic x86_64..... I hope I don't run into any problems.... but I always keep the last 2 kernels as backup (2.6.28.1-ARCHtestAMD2 and 2.6.28-ARCHtestAMD)


I might be uploading an AUR package soon for people that want to build their own parallel kernel with "make menuconfig". Basically the same ABS PKGBUILD and preset/install/config files except that it will have a different name so it doesn't overwrite the default stock 2.6.28-ARCH kernel..... and it also has the "make menuconfig" option so that you can customize.

Is there an improvement in performance when not using the stock Arch kernel? As you can see from my sig I have an i7 and running Arch64, so this interests me.

As for the kernel update, everything is all good here. Boot has gone significantly faster for me.

---

### Post by ghindo on 2009-01-26
> **kerry_s said:**
> question:
i'm not using that testing repo, just the core,extra,community, are there usually problems from updates?Generally not.  I know that there have been a few issues in the past with Xorg and a few other packages, but nothing significant or frequent.

---

### Post by handy on 2009-01-26
> **sisco311 said:**
> no issues here either.

reinstalling the kernel is not so hard.

Thanks for your detailed step by step instructions in answer to my previous post.

---

### Post by crimesaucer on 2009-01-26
> **OutOfReach said:**
> Is there an improvement in performance when not using the stock Arch kernel? As you can see from my sig I have an i7 and running Arch64, so this interests me.

As for the kernel update, everything is all good here. Boot has gone significantly faster for me.

I just like to use the AMD64 settings and a couple of other modifications like -Os to strip the kernel code a bit to reduce size. I also like to de-select some modules that I don't need.... sometimes I try new things that are offered as "new" or "experimental". I have also messed around with the Timer settings and have recently gone back to the default 300HZ.


The main reason I do it is that my entire system is built from source using C[XX]FLAGS for my AMD64 Turion 64 X 2 TL-60..... so I feel that I might as well have the kernel compiled as AMD64 also..... since I've compiled all my apps for AMD64.....


Most people say that it is only a placebo effect if you feel that there is any improvement. I know back in kernel 2.6.25 when I started building my own AMD64 kernels I kept on having strange dmesg errors with the generic x86_64.... but that all stopped from 2.6.26


I mostly do this as a hobby and a learning experience..... so that is why I'll probably make an AUR package to share with people.

---

### Post by sisco311 on 2009-01-26
> **handy said:**
> Thanks for your detailed step by step instructions in answer to my previous post.

Sorry, I didn't see your post. 

The [Arch Wiki]("http://wiki.archlinux.org/index.php/Kernel_panic") provides step by step instructions. I thought this is obvious. :evil:

I'm sorry again. :)

---

### Post by OutOfReach on 2009-01-26
> **crimesaucer said:**
> I just like to use the AMD64 settings and a couple of other modifications like -Os to strip the kernel code a bit to reduce size. I also like to de-select some modules that I don't need.... sometimes I try new things that are offered as "new" or "experimental". I have also messed around with the Timer settings and have recently gone back to the default 300HZ.


The main reason I do it is that my entire system is built from source using C[XX]FLAGS for my AMD64 Turion 64 X 2 TL-60..... so I feel that I might as well have the kernel compiled as AMD64 also..... since I've compiled all my apps for AMD64.....


Most people say that it is only a placebo effect if you feel that there is any improvement. I know back in kernel 2.6.25 when I started building my own AMD64 kernels I kept on having strange dmesg errors with the generic x86_64.... but that all stopped from 2.6.26


I mostly do this as a hobby and a learning experience..... so that is why I'll probably make an AUR package to share with people.

Ahh. I see. I would love to see an AUR package with something like that. :)

Well, I don't really want to get into kernel compilation since I am very busy these days. And you know what they say, "If it ain't broken, don't fix it."

But I'll probably try kernel compilation when I have lots of free time. :D

---

### Post by crimesaucer on 2009-01-26
> **OutOfReach said:**
> Ahh. I see. I would love to see an AUR package with something like that. :)

Well, I don't really want to get into kernel compilation since I am very busy these days. And you know what they say, "If it ain't broken, don't fix it."

But I'll probably try kernel compilation when I have lots of free time. :D

Or the other saying, "don't start no trouble won't be no trouble".


The AUR package I will be submitting is so you "don't have to worry about breaking anything"..... so a beginner can try their first attempt at building a kernel from source using "make menuconfig"..... while not damaging anything having to do with the default -ARCH kernel or any of it's files/images and directories like: "/lib/modules/2.6.28-ARCH" and "/usr/src/linux-2.6.28-ARCH"



I just have to look into the procedure about submitting an AUR package.

---

### Post by handy on 2009-01-27
> **sisco311 said:**
> Sorry, I didn't see your post. 

The [Arch Wiki]("http://wiki.archlinux.org/index.php/Kernel_panic") provides step by step instructions. I thought this is obvious. :evil:

I'm sorry again. :)

No problem, I know it is easy to miss things in the forum, & my apologies for being a little short. ;-)

Thanks very much for the link. :-)

I thought it would be a boot from the Arch install disk, chroot &  pacman -U type of thing.

---

### Post by kerry_s on 2009-01-27
that wouldn't have helped me, i had already cleaned up(pacman -Scc) a habit of mine to clean up after install. this time i'm not cleaning nothing, so i didn't put no shortcut for it in my bash.rc, hopefully i can have a backup to roll back to. ;)

---

### Post by handy on 2009-01-27
> **kerry_s said:**
> that wouldn't have helped me, i had already cleaned up(pacman -Scc) a habit of mine to clean up after install. this time i'm not cleaning nothing, so i didn't put no shortcut for it in my bash.rc, hopefully i can have a backup to roll back to. ;)

Using the pacman -Sc command when you are sure that you have installed no problems in your last -Syu is a good way to keep your cache size down, but still gives you a quick & easy way out if your next -Syu brings unexpected trouble.

---

### Post by crimesaucer on 2009-01-27
> **OutOfReach said:**
> Ahh. I see. I would love to see an AUR package with something like that. :)

Well, I don't really want to get into kernel compilation since I am very busy these days. And you know what they say, "If it ain't broken, don't fix it."

But I'll probably try kernel compilation when I have lots of free time. :D

I just uploaded it here, check it out if you want to: [http://aur.archlinux.org/packages.php?ID=23467](http://aur.archlinux.org/packages.php?ID=23467)

---

### Post by kerry_s on 2009-01-27
> **handy said:**
> Using the pacman -Sc command when you are sure that you have installed no problems in your last -Syu is a good way to keep your cache size down, but still gives you a quick & easy way out if your next -Syu brings unexpected trouble.

good idea, that will only clean what is no longer installed right?

---

### Post by handy on 2009-01-27
> **kerry_s said:**
> good idea, that will only clean what is no longer installed right?

Yes. 

I just have to remember to do it when I'm happy that -Syu  or -Syu --aur was ok. :-)

---

### Post by will1911a1 on 2009-01-27
Just updated, no problems here.

---

### Post by kerry_s on 2009-01-29
yeah, i figured it out, what i did was linked /bin/sh to dash, arch scripts depend on /bin/bash, but i guess some have /bin/sh and expect it to be linked to bash. anyways, i was pretty sure it was something i did, i'm use to certain tweaks from debian, but they just don't fly on arch. i'll just stick with a standard install for now, cause i'm working for the next couple of months and i'm just to tired to figure out the inner workings just yet.
:)

---

