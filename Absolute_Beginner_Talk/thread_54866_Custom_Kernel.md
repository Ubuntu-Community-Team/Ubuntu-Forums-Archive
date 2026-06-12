---
title: "Custom Kernel ?"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by BrianB on 2005-08-06
I'm having a little trouble trying to compile my own custom kernel. I've read the wiki page about recompiling the kernel but I cant even get past step 1 which says you need to have the kernel-package and build-essential fakeroot packages but I don't have internet acces from ubuntu (which is why I'm recompiling in the 1st place) so can't get them. Also I cant seem to uncompress the linux source that I downloaded from kernel.org from its bz2 archive. Any help? :???:

---

### Post by az on 2005-08-06
If you need to compile a kernel module to enable your internet hardware, you can just use the kernel headers instead. It is way easier and all you need in on the cd.

Install build-essential and linux-headers-2.6.10-5-386

What driver do you need to build?

---

### Post by BrianB on 2005-08-06
Well I want to patch the kernel with a patch I got for my broadcom modem. Which is a winmodem.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=azz]If you need to compile a kernel module to enable your internet hardware, you can just use the kernel headers instead. It is way easier and all you need in on the cd.

Install build-essential and linux-headers-2.6.10-5-386
[/QUOTE]

They are found here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Install this way in terminal (make sure the debs are in your root folder)

sudo dpkg -i packagename.deb

---

### Post by az on 2005-08-06
[QUOTE=BrianB]Well I want to patch the kernel with a patch I got for my broadcom modem. Which is a winmodem.[/QUOTE]


Would you tell me about it?  Do you have a link?

To uncompress a bz2 file you need to install bzip2.  You should use the linux-tree package for the kernel source.  But I have never heard of a kernel patch for a winmodem...  Please let me know about the link...

---

### Post by BrianB on 2005-08-07
Thanks poofyhairguy! Check out [http://www.smlink.com](http://www.smlink.com) and [http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by az on 2005-08-07
If you mean the smartlink modem driver, it is a kernel module, and not a patch.  Just install the sl-modem packages.

You do _not_ need the kernel source to make this module, just use the linux-headers package.

There are precompiled sl-modem-modules available for the stock ubuntu kernel.

---

### Post by BrianB on 2005-08-08
Sorry 'bout that I am a bit of a noob. But where can I get the precompiled sl-modem-modules?

---

### Post by az on 2005-08-08
Either the ubuntuguide or

wiki.ubuntu.com/forum/hardware

---

### Post by BrianB on 2005-08-11
Thanks :) . I can connect to the internet if I use wvdial but when I open firefox it gives me the error message "xxxxx could not be found please check the name and try again" any help?

---

