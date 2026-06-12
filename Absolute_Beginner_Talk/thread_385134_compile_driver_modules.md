---
title: "compile driver modules?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by travm on 2007-03-15
Hi, Im trying to install a driver I have found for some old apparently unsuported hardware, a voodoo 3 3500 tv.  I have got the display adapter working, now i want to try and get the tv-input working.  I have found a driver called v3tv, however it tells me I must compile the drivers as modules in the kernel.  This means (i think) that i need to recompile my kernel, with some patches applied to it (supplied from the v3tv website).  My problem is I have no idea where to start with these drivers since there is little to no documentation.
website is
[http://www.gilfillan.org/v3tv/](http://www.gilfillan.org/v3tv/)
If someone more knowlegable than me could have a look at this and maybe point me somewhere or get me started it would be great.
my system is currently running edgy, and is an old athlon 500mhz 128mb pc100, with a voodoo 3 3500 tv and a dlink lan card.  Everything else works.

my kernel version is 2.6.17, but i think i need to back up to 2.6.15 for the v3tv drivers to work? any idea?

---

### Post by quark_77 on 2007-04-04
Hi travm,

Building a new kernel or indeed an old kernel is going to be a complex job in itself and may create more problems. The guide I followed to compile a kernel is here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158). I'd advise using your current config file /boot/config-2.6.17-11-generic or something similar then make oldconfig to update/downgrade it.

There is an alternative with respect to kernel building - download the edgy kernel sources, its a package called linux-source complete with all the changes/drivers Ubuntu make. An explanation for how to build this can be found here: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild).

In either case, you will be working from /usr/src, so this is where you need to download your patches to. To apply a patch, use this:
```
cat <patchname> | patch -p0 --dry-run
cat <patchname> | patch -p0
```
If the top one succeeds, you are safe to use the bottom one (which actually applies the patch as opposed to simulating it).

As for building modules, assuming you have got gcc & build-essential, you then need a package called module-assistant which can be downloaded as usual using synaptic. Download the kernel module you want to build to /usr/src, then try the following:
```
sudo module-assistant prepare,update
sudo module-assistant build,install modulename

```
replacing module name with the name of the archive containing the module in /usr/src minus the archive extension eg tgz, tar.bz2 etc

Just one thing to note - module-assistant will build & install the module for your current kernel. If your current kernel has the necessary code built in so that you don't need to patch it, you don't need to rebuild it, just use module assistant and reboot.

If you do have to rebuild the kernel, assuming you are following the master kernel thread, you have the following option - extract the archive containing your kernel module. It should extract to /usr/src/modules/modulename. This is all you have to do. You'll notice that there is a modules_image option supplied to make-kpkg - this builds everything in /usr/src/modules if it can.

I apologise if this explanation is a little over-complicated but this is a complicated issue - take a look at the master kernel thread (linked above) and you'll see it's no mean feat compiling a kernel!! If you need me to clarify any of the above I'll try my best - I've only just successfully built my own custom kernel!

Good luck & hope this helps,

Quark_77

---

