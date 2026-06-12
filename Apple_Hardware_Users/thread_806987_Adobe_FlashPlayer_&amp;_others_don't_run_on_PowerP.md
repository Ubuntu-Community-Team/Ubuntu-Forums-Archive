---
title: "Adobe FlashPlayer &amp; others don't run on PowerPC"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by Scientia on 2008-05-25
I'm using an ancient (700mhz) iBook powerpc, and the architecture doesn't support all sorts of apps, more prominent ones being Adobe Flash Player and all Java apps. Any fix for this or am i stuck.


Bear in Mind,
I'm a Noob.
Thx.

---

### Post by Phonan on 2008-05-25
> **Scientia said:**
> I'm using an ancient (700mhz) iBook powerpc, and the architecture doesn't support all sorts of apps, more prominent ones being Adobe Flash Player and all Java apps. Any fix for this or am i stuck.


There is no flash plugin for powerpc linux, but you can install alternatives, like gnash. Gnash is a free flash player. It doesn't have nearly as much support for files as the actual Flash Player, but it is one of the closest alternatives. Just type "sudo apt-get install gnash mozilla-plugin-gnash" in a terminal to install both gnash and the plugin for firefox. Also, you can open Synaptic (System-Administration-Synaptic Package Manager) and search for and install both "gnash" and "mozilla-plugin-gnash."

On the Java front, there is a free alternative- IcedTea. To install this and its firefox plugin, type "sudo apt-get install icedtea-gcjwebplugin" in a terminal, or use Synaptic and search for "icedtea-gcjwebplugin." Like Gnash, though, I wouldn't expect everything to work with this plugin.

A lot of this information on plugins, etc for the PowerPC version of Ubuntu can be found at the PowerPC FAQ on the Ubuntu wiki- [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Good luck with Ubuntu!

---

### Post by frog_pilot on 2008-05-25
you can also add ibm-java to your system. go to [www.medibuntu.org](www.medibuntu.org). there you can find more reference for adding this repository to your sourcesand what multimedia support is given by the medibuntu programs.

e.g. youtube is running smoothly with gnash + ibm-java.

---

### Post by Phonan on 2008-05-26
By the way, as far as I can tell, this: [http://packages.medibuntu.org/pool/non-free/i/ibm-j2re1.6/ibm-j2re1.6_1.6.0-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/i/ibm-j2re1.6/ibm-j2re1.6_1.6.0-0medibuntu1_powerpc.deb)

is the download you're looking for, if you don't want to go to the hassle of installing medibuntu repositories. If you have the repositories enabled, it still should be found under "ibm-j2re1.6"

---

### Post by Scientia on 2008-05-26
Thanks, i've installed the ibm version. But i cannot run frostwire, terminal tells me i don't have a valid JRE. Any help?
Thanks a bunch.

---

