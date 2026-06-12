---
title: "How to prevent Ubuntu from updating kernels?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-29
I was running a custom compiled kernel when I did the upgrade to 2.6.20-16. After rebooting I could see 3 kernels in the grub list (2.6.20-15, 2.6.20-16 and my custom kernel). None of them worked after the upgrade :( The loading bar on the boot screen always got stuck at the beginning and stayed like that for ages. All 3 kernels did the same thing!! I had to restore my system using a backup but now Ubuntu again ask me if I want to update.

Basically I don't want to update kernels in Ubuntu because I always apply patches (undervolting etc) to kernels (mostly Vanilla) so I really don't want Ubuntu to update my kernels or add a new one to the list. Is there a way to prevent Ubuntu from proposing kernel updates yet still making all other updates in update manager available?? I'd like something permanent that would keep me from having to constantly watch for kernel updates in the update manager to unselect them...

Thanks

---

### Post by klytu on 2007-05-29
In Synaptic's GUI you can highlight each installed kernel then go to Package>lock version. See sample screenshot attached.

---

### Post by TheMono on 2007-05-29
The package that pushes updates to you is linux-generic. It is a metapackage that depends on the most recent kernel + its restricted modules. When a new kernel comes out, they upgrade that package so that it pulls down the others.

The above trick doesn't quite work because kernel upgrades are additions of another kernel, not pure upgrades.

Instead, uninstall the metapackage, and you will be fine. You won't be pushed any more upgrades.

There is a different metapackage which depends on the kernel alone, and not the restricted modules, you may have to remove that too.

---

### Post by TheMono on 2007-05-29
The metapackages are 

linux-generic
linux-headers-generic
linux-image-generic

Will be different if you are using server kernels, or Xen, etc.

---

### Post by kilou on 2007-05-29
Thanks for the tips guys! TheMono, I uninstalled linux-generic, linux-headers-generic and linux-image-generic packages and the update manager doesn't ask for these to be updated: great :) However there are still the following packages in the update list:

- linux-libc-dev
- linux-restricted-modules-common
- linux-restricted-modules-generic
- linux-source-2.6.20

Is it OK not to update the kernel itself but still update the restricted modules? I'm not using restricted modules on my current laptop but since there is a way to use restricted modules with a custom kernel (see [http://ubuntuforums.org/showthread.php?t=441013&highlight=howto+restricted+modules](http://ubuntuforums.org/showthread.php?t=441013&highlight=howto+restricted+modules)) I'd like to install the latest restricted modules. 

Also what about the linux-source-2.6.20 (I installed this package and build/patched my current kernel from it so what will this do if now I update linux-source.2.6.20 ???). 

Really I prefer doing kernel updates manually :)

---

### Post by kilou on 2007-05-29
...and what is the purpose of linux kernel headers for development (linux-libc-dev)???

---

### Post by kilou on 2007-05-29
up

---

### Post by TheMono on 2007-05-29
Sorry, my mistake. There are apparently more metapackages than I noticed! 

Yes, linux-restricted-modules-generic, But not linux-restricted-modules-common and linux-libc-dev

It is your option whether you want to uninstall the kernel source, makes no difference one way or the other.

---

### Post by kilou on 2007-05-31
> **TheMono said:**
> 

Yes, linux-restricted-modules-generic, But not linux-restricted-modules-common and linux-libc-dev



Sorry, do you mean that I can uninstall linux-restricted-modules-generic but not the other packages or is it just the opposite?

---

