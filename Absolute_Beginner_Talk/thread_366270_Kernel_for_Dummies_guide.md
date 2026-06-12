---
title: "Kernel for Dummies guide?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-02-20
OK, so I'm brand spanking new to Linux and am very excited.  But woe is me without my DSL internet connection which I can't get to work until I do some seemingly advanced stuff first which is over my head.  [http://ubuntuforums.org/showthread.php?t=1906](http://ubuntuforums.org/showthread.php?t=1906) (xpic's reply) shows the steps I need to take to install my PCI Accessrunner DSL modem.

Step 1 is "To compile [the modem driver] you need the kernel headers. Chose it from Synaptic. Pay attention to choose the header of your kernel. "

OK, Synaptic is a package manager right?  Won't I need a linux based internet connection to use it?  Thus my questions are:

1) What are Linux kernel headers?  Are kernel headers different from kernel source?
2) How can I get the header for my specific build (Kubuntu Edgy, 2.6.11? or something) using my XP based internet connection?  I tried checking on [http://kernel.org/](http://kernel.org/), but can't seem to find any links to older kernels (e.g. older than 2.6.20) and even then I have no idea what I'm looking for since nothing says "Download linux kernel header here" 
3) As an aside, is there a basic guide to understanding how to compile kernels?  What are patches to kernels?
4) What damage can I do by recompiling kernels?
5) Is it common to have to play around with kernels and/or headers?

Thanks!

---

### Post by Bachstelze on 2007-02-20
1) The kernel headers are files required to build kernel modules. They're C headers but I don't think explainong what they actually do would be very useful. Just remember this : you'll need the headers for your current kernel whenever you'll want to build modules for it.

2) *sudo apt-get install linux-headers-$(uname -r)*

3) This explains all the steps you need to run in a nutshell : [http://wiki.debian.org/KernelCompilation](http://wiki.debian.org/KernelCompilation) . Patches are files that will automatically modify the kernel code, to fix bugs or add new features for example.

4) None. If your compiled kernel doesn't work, you can always use the one that came with Ubuntu if you weren't reckless enough to delete it.

5) It is common to have the headers installed because they're used to install most drivers when they're not included in the kernel itself. Using home-compiled kernels is less common - especially in Ubuntu - but not rare either.

---

### Post by mikeescott on 2007-02-20
Here are a few of the headers. Not sure which ones you need which ones you need, but I ma sure it is one of these. They can also be found at:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and searching for what you need.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-generic_2.6.17.11_i386.deb&md5sum=173dc2722ef620f12ccc8ea827f49ce8&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-generic_2.6.17.11_i386.deb&md5sum=173dc2722ef620f12ccc8ea827f49ce8&arch=i386&type=security)

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-386_2.6.17.11_i386.deb&md5sum=7aedfec94ff32e01619e875bf1d52d60&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-386_2.6.17.11_i386.deb&md5sum=7aedfec94ff32e01619e875bf1d52d60&arch=i386&type=security)

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.17%2Flinux-headers-2.6.17-11_2.6.17.1-11.35_i386.deb&md5sum=f82e3ca5823ee3c66164c6e8d10c2620&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.17%2Flinux-headers-2.6.17-11_2.6.17.1-11.35_i386.deb&md5sum=f82e3ca5823ee3c66164c6e8d10c2620&arch=i386&type=security)

---

### Post by cknight on 2007-02-21
HymnToLife,

I've tried your suggestion of using apt-get.  Here's my output:

```
cknight@cknight-desktop:~$ sudo apt-get install linux-headers-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Presumably this means I've already got the headers?  If so, can I skip the step that says get the headers from Synaptic?

---

