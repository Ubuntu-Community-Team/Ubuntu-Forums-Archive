---
title: "64-bitness on PowerMac?"
date: 2007-05-08
forum: Apple PPC Users
---

### Post by i_a_coops on 2007-05-08
I've seen references to a PPC-64 version of Ubuntu, just want to check is this still continued? I can't find a 64 bit distro for my G5 Mac, the main reason I want to try is simply coz I've been really unlucky recently (I think) in getting Linux working properly (neither Ubuntu or Fedora could get on the internet which was a bit annoying tbh), so i thought I might as well start again with an os that uses the systems capabilities.....Unfortunately PPC Ubuntu in general seems to have been relegated since Feisty Fawn, so i'm not optimistic of finding a 64 bit version of Feisty....!

---

### Post by stmiller on 2007-05-08
Yes, the current feisty ppc disc has both powerpc (32bit) and powerpc64 (64bit) kernels. You press tab at the boot screen and pick the appropriate one. So that one disc works for all macs.

The G5 cpu requires a 64bit kernel. So technically this particular Ubuntu install is a 64bit kernel with a 32bit ppc userland.

---

### Post by stmiller on 2007-05-08
And BTW: I've got a Powermac dual 2 Ghz running Feisty. It's SUPER fast with Linux. It's a night and day difference from OS X on the same machine. Also the cpus run about 10C cooler under Linux, interestingly enough. Apple's own thermal management does not do as good a job on the same hardware as drivers from the free open source community. Heh.

Gentoo has a fully 64bit powerpc version if you are interested in a distro with a 64bit kernel AND 64bit userland. Though some 32bit powerpc apps aren't available when you use that setup.

---

