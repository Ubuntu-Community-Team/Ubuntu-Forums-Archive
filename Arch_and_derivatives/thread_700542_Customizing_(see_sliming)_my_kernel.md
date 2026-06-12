---
title: "Customizing (see sliming) my kernel"
date: 2008-02-18
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-02-18
I've decided to take this great Monday off to compile my own kernel to take out everything I don't need and see if there is a specific patch for vaio notebooks (if you know of any that work with .24, please share :)). What parts of the kernel can I take out? I'll post the pkgbuild once I get abs going but right now it's not letting me connect.

---

### Post by Crooksey on 2008-02-18
You can take out what you or your hardware dosent require, what else do you want me to say?

---

### Post by K.Mandla on 2008-02-18
When I recompile kernels I usually take a look at lspci -vvv, dmesg and anything else that will give me hardware info. And then anything in the kernel descriptions that doesn't seem to match ... gets disabled. I also leave out the filesystems, networking protocols, etc., and the results are usually quite speedy.

I also try to keep everything compiled directly into the kernel, rather than a module, but I guess there are two different ways of looking at that.

---

### Post by PurposeOfReason on 2008-02-18
Just saying I'm giving it my first go. As this is my first kernel compilation, I just disabled some patches that were for certain features in toshiba notebooks (bluetooth) and threw in a patch that gets the wireless light to work as it doesn't right now. Now I'm waiting for it to finish. I've never gotten this far and was really confused when the blue screen came up with all those options. Didn't know it did that as it usually failed out with me in the past. :)

---

### Post by PurposeOfReason on 2008-02-19
> **K.Mandla said:**
> When I recompile kernels I usually take a look at lspci -vvv, dmesg and anything else that will give me hardware info. And then anything in the kernel descriptions that doesn't seem to match ... gets disabled. I also leave out the filesystems, networking protocols, etc., and the results are usually quite speedy.

I also try to keep everything compiled directly into the kernel, rather than a module, but I guess there are two different ways of looking at that.
Anything in particular to look for? Also, I finally got rid of that dreaded stuck pixel. 18 hours of jscreenfix and some pressure from screen on too off to on. :)

---

### Post by bwtranch on 2008-02-19
> **K.Mandla said:**
> When I recompile kernels...

I also try to keep everything compiled directly into the kernel, rather than a module, but I guess there are two different ways of looking at that.

I think you're always better off compiling into the kernel. I know I've had way more troubles with buggy modules than I did with the core. Actually, I don't think I've ever really had a problem that was related to the actual kernel itself. That's the great thing about Arch and Gentoo...it pretty much opens a door on making your system what you want it to be. The more options have, though, the harder the choices become. (Life is a dichotomous key).

---

### Post by PurposeOfReason on 2008-02-19
After a few tries (I kept trying to rename it and take -ARCH out of it which wouldn't let it boot) I'm took 4 seconds off my boot and everything feels faster. Most people don't think 4 seconds is much; but on an already speedy arch boot it is amazing.

---

### Post by K.Mandla on 2008-02-19
> **PurposeOfReason said:**
> Anything in particular to look for? Also, I finally got rid of that dreaded stuck pixel. 18 hours of jscreenfix and some pressure from screen on too off to on. :)
Nothing in particular comes to mind. It always seems like there's a bunch of bizarre hardware enabled in the vanilla kernel, but that might just be what I'm used to. I also take out the filesystems I don't use, and disable a lot of other stuff. I know I'm being vague, but so much of kernel compilation depends on the machine you're running, I can't really be specific without talking about my particular hardware, and that won't do you any good. :???:

By the way, a four-second difference is very good. :D

---

