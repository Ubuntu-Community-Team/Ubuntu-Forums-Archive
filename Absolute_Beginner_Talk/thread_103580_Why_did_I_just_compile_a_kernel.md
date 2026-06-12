---
title: "Why did I just compile a kernel?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by dueY on 2005-12-14
Hey all.  I just read a guide posted here on how to compile your own kernel.  I thought I had to do this because the NVIDIA drivers were yelling at me that my kernel was compiled with gcc3.4 but I was using gcc4.0.  What I think I've learned from this whole ordeal is that you can just type
CC=gcc-3.4
export CC
to switch to gcc-3.4 before compiling something.  So why did I compile my own kernel?  What good does that do me?  I think I enabled DMA on it, not sure if the default kernel I was using before had it enabled.  But other than that, what's the point of compiling your own kernel?  Will it be obsolete next time Linux updates and I'll have to compile another one with the newer version of Linux? :confused:

---

### Post by MartinG on 2005-12-14
Well, you could go back to the standard kernel and use your new-found knowledge (export CC=gcc-3.4) to compile just the nvidia module :-)  If you don't want to do that now, it's OK to do that when a new kernel becomes available.

Note that if you do this you can't use the restricted-modules from the repositories -- they conflict with the compiled module.  And of course to use gcc-3.4 you have to install it -- but I expect you knew that :-)

---

### Post by dueY on 2005-12-14
[QUOTE=MartinG]Well, you could go back to the standard kernel and use your new-found knowledge (export CC=gcc-3.4) to compile just the nvidia module :-)  If you don't want to do that now, it's OK to do that when a new kernel becomes available.

Note that if you do this you can't use the restricted-modules from the repositories -- they conflict with the compiled module.  And of course to use gcc-3.4 you have to install it -- but I expect you knew that :-)[/QUOTE]

Yeah I know I can go back now and compile the NVIDIA module with those commands now.  So I feel like I wasted thirty minutes or so compiling my custom kernel when there are no benefits to having done it, unless I am not realizing something.

Are you saying I will have to reinstall the NVIDIA drivers every time a new kernel version is released if I decide to use the newest versions instead of my custom one?

---

### Post by Estariel on 2005-12-14
Well, you didn't waste your time, you learned something (how to compile a kernel)

There are situtations when this knowledge will come in handy (when you want to apply some weird patches to the kernel for example). 

For your specific example though, it was indeed not necessary to recompile the kernel. (If you only enabled the options for your specific hardware though, you might end up with a smaller kernel which boots faster...)

---

### Post by MighMoS on 2005-12-14
From a purely functionalist standpoint, compliling your kernel allows you to select the options that are good for _you_ instead of the community.  I must say that Ubuntu does provide good support though, with a wide variety of kernels to choose from.  

But compiling a custom kernel can be done if you use a certain patchset instead of Ubuntu's (for example, I use -ck, which is great for desktop performance), or you just think you know your machine better than the upstream guys and can make something better for it.

---

### Post by MartinG on 2005-12-14
[QUOTE=dueY]Are you saying I will have to reinstall the NVIDIA drivers every time a new kernel version is released if I decide to use the newest versions instead of my custom one?[/QUOTE]

I suppose the answer is yes :-(  What I am saying is that if you want to use the new kernel, you can use the NVidia driver that is included with it, with a minimum of hassle. If you want to use a newer driver, then you will need to build a custom kernel module to go with it (and leave off the new restricted-modules).  Once you've got the hang of it it's pretty easy and quick using the NVidia install script (well, it was for me :-) ), so your experience is not wasted!

---

### Post by dueY on 2005-12-14
[QUOTE=MartinG]I suppose the answer is yes :-(  What I am saying is that if you want to use the new kernel, you can use the NVidia driver that is included with it, with a minimum of hassle. If you want to use a newer driver, then you will need to build a custom kernel module to go with it (and leave off the new restricted-modules).  Once you've got the hang of it it's pretty easy and quick using the NVidia install script (well, it was for me :-) ), so your experience is not wasted![/QUOTE]

The NVIDIA drivers that came with the kernel didn't work for me (assuming you're talking about the nvidia-glx or whatever from Synaptic.)  Changing my driver to "nv" (which I guess is the open-source version of NVIDIA's drivers?) while reconfiguring X didn't work either.  Only "vesa" worked.  "nvidia" works now that I compiled the propietary module from the NVIDIA website.

It's probably a good idea to keep my Linux kernel updated I assume. If there weren't fixes/improvements then they wouldn't be updated in the first place?

---

### Post by MartinG on 2005-12-14
[QUOTE=dueY]It's probably a good idea to keep my Linux kernel updated I assume. If there weren't fixes/improvements then they wouldn't be updated in the first place?[/QUOTE]

Yes, though not every fix is relevant to every user, and it seems to be a law of computing that every upgrade brings a new bug :-) .  So, if you're happy with your system think twice about upgrading.  (That's what "they" say, but I must confess I always upgrade!)

---

