---
title: "Location of Kernel"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by dashifen on 2006-06-08
Greetings all,

The wireless network at my office requires a VPN client to use.  A VPN client is provided for download and installation but during the installation of the client, it asks where the kernel can be found.  I expected it to be in /usr/src/linux (or some variant thereof) but it wasn't I hunted around a bit, but didn't see anything.  So, my question for you is simply:  Where is it?

Thanks all,
       Dashifen

---

### Post by taurus on 2006-06-08
Maybe you didn't have the source for your kernel installed!  So, you need to download it (if you use apt-get, it should be in /usr/src), unpack it, and link /usr/src/linux to it.  Then, build and install whatever you want after that...

---

### Post by az on 2006-06-08
No.  You need to install build-essential and linux-headers-386 (or whatever arch)

The linux-headers provides the headers you need to build extra modules for your running kernel so you don't have to download, comfigure, compile and then install a kernel just to be able to add one module.

---

### Post by dashifen on 2006-06-08
According to the record of installed packages in Synaptic, the kernel is installed somewhere, there's just no symlink in /usr/src.  I tried installing the build-essentials, which when using Synaptic automatically included the linux headers as well, but that didn't seem to add anything either.

Where would the kernel be so that I can create the necessary symlink.  

In case it matters, a screenshot of the instalation script during which the request for the kernel is made is attached.

---

### Post by az on 2006-06-08
You need the kernel headers, not the kernel image.  It just means that you need to install the linux-heraders-386 package.  The use the /usr/src/linux-headers-2.6.15-23-386 directory.  linux-headers and linux-header-386 are different packages.

---

### Post by dashifen on 2006-06-08
That did it.  Thanks for your help!!

---

### Post by dashifen on 2006-06-08
That did it.  Thanks for your help!!

---

### Post by dashifen on 2006-06-08
Wow ... don't know why I got the duplicate replies there.  Sorry for the spam.

---

### Post by nitin_mz on 2006-06-08
I was having the same problem - build errors because I was trying to use linux-src-2.6.15 instead of linux-headers.. Thanks!

---

