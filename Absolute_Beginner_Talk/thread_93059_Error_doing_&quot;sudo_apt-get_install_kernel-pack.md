---
title: "Error doing &quot;sudo apt-get install kernel-package&quot;"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by jriff on 2005-11-21
Hi All!

I have just downloaded Ubuntu and are playing around with it a bit. I want to compile a new kernel and have found a lot of guides. They all state that I need to apt-get 3-4 different packages witch I have done and it all worked without any problems. However when I do "sudo apt-get install kernel-package" I get this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package

All the other packages worked (eg. fakeroot) so it isn't my internet connection. Does someone know what I am doing wrong?

BTW. what is the linux variant of the command "ipconfig -renew" and "ipconfig -release"? i know ifconfig but the man page doesn't mention anything about renewing via DHCP.

---

### Post by adwait on 2005-11-21
That just means that there isn't a package by that name. If you are are trying to download a different kernel, try using 
```
sudo apt-get install linux-386
```
That's for the default latest kernel. If you want a particular one,
```
sudo apt-get install linux-image-<version no.>
```

---

### Post by jriff on 2005-11-21
So... the "kernel-package" isn't the name of the package? How do I know what package to apt-get? 

If I type uname -r I get: 2.6.12-9-386
Is the command then: sudo apt-get install linux-image-2.6.12-9-386?

I read somewhere that I should get the 686-kernel since I am using a Pentium Mobile processor. Shouldn't I get that one then? (2.6.12-9-686 perhaps?)

- Jacob

---

### Post by kont.raen on 2005-11-21
[QUOTE=jriff]So... the "kernel-package" isn't the name of the package? How do I know what package to apt-get? 

If I type uname -r I get: 2.6.12-9-386
Is the command then: sudo apt-get install linux-image-2.6.12-9-386?

I read somewhere that I should get the 686-kernel since I am using a Pentium Mobile processor. Shouldn't I get that one then? (2.6.12-9-686 perhaps?)

- Jacob[/QUOTE]

sudo apt-get install linux-686 will do the trick and provide you with a current, 686 optimized, kernel.

---

### Post by jriff on 2005-11-21
Thanks a lot! I can't wait to compile my first kernel :KS 

"linux-686" allways gets me the newest kernel?

Just to be sure: It dosn't matter if I get a kernel that is newer than the one I am using (if I try the same command, "linux-686" in a few months from now)? I can have multiple kernels of different versions on my linux install and then choose witch kernel I want to use at boot time?

I never got an answer to my question about the equivalent of "ipconfig -renew" and "ipconfig -release" in Linux/Ununtu? Anyone?

---

### Post by sevenrechlin on 2005-11-21
Yeah grub will let you choose which kernel to load... 

And you can also search for "linux-image" in synaptic and choose the 686 kernel.
Otherwise,  "$sudo apt-get install linux-686-smp".

---

### Post by jriff on 2005-11-21
I'm sorry, but this dosn't seem to be right. I am not trying to get a new pre-compiled kernel - I want to compile one myself. For this I need the package "kernel-package" but I am not able to apt-get it. 

Am I missing some sources perhaps?

---

### Post by Gustav on 2005-11-21
$ apt-cache show kernel-package
Package: kernel-package
Priority: optional
Section: misc
Installed-Size: 1316
Maintainer: Manoj Srivastava <srivasta@debian.org>
Architecture: all
Version: 9.001ubuntu5
Depends: perl, dpkg (>= 1.4), dpkg-dev (>= 1.4.0.9), gcc | c-compiler, make
Recommends: libc6-dev | libc-dev, bzip2
Suggests: kernel-source, libdb3-dev, libncurses-dev, docbook-utils
Filename: pool/main/k/kernel-package/kernel-package_9.001ubuntu5_all.deb
Size: 361372
MD5sum: 98d6d24f7dbcf6b30aa579518b6a4e25
Description: A utility for building Linux kernel related Debian packages.
 This package provides the capability to create a debian kernel-image
 package by just running make-kpkg kernel_image in a kernel source
 directory tree.  It can also package the relevant kernel headers into
 a kernel-headers package. In general, this package is very useful if
 you need to create a custom kernel, if, for example, the default
 kernel does not support some of your hardware, or you wish a leaner,
 meaner kernel.  It also scripts the steps that need be taken to
 compile the kernel, which is quite convenient (forgetting a crucial
 step once was the initial motivation for this package). Please look at
 /usr/share/doc/kernel-package/Rationale.gz for a full list of advantages
 of this package.
 .
 If you are running on an intel x86 platform, and you wish to compile a
 custom kernel (why else are you considering this package?), then you may
 need the package bin86 as well.  (This is not required on other platforms).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


At least it exists and it's in main.

---

### Post by jriff on 2005-11-21
[QUOTE=Gustav]$ apt-cache show kernel-package
Package: kernel-package
Priority: optional
Section: misc
Installed-Size: 1316
Maintainer: Manoj Srivastava <srivasta@debian.org>
Architecture: all
Version: 9.001ubuntu5
Depends: perl, dpkg (>= 1.4), dpkg-dev (>= 1.4.0.9), gcc | c-compiler, make
Recommends: libc6-dev | libc-dev, bzip2
Suggests: kernel-source, libdb3-dev, libncurses-dev, docbook-utils
Filename: pool/main/k/kernel-package/kernel-package_9.001ubuntu5_all.deb
Size: 361372
MD5sum: 98d6d24f7dbcf6b30aa579518b6a4e25
Description: A utility for building Linux kernel related Debian packages.
 This package provides the capability to create a debian kernel-image
(.....)
[/QUOTE]

So! IT does exist :D But then why, oh, why can't I apt-get it? It should be a pretty normal package, right?

---

### Post by jriff on 2005-11-21
Anyone?

---

### Post by jriff on 2005-11-22
Got it! I just had to uncomment some lines in sources.list!

Now I have compiled a kernel and it booted perfectly - I was just wondering how to delete the kernel again including the grub entries.

---

### Post by codhog on 2005-11-24
We solved this problem on our system by hitting the "Reload" button in Synaptic.

---

