---
title: "Tried to manually run configure but got another error"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by DarthChili on 2007-11-25
I want to use synaptic package manager but after i type in my passoword i get this error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I opned up a terminal and put "sudo dpkg --configure -a" in and got the following

jen@jen:~$ sudo dpkg --configure -a
[sudo] password for jen:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

I wanted to get 3D desktop but it got me into this error stuff. I went here to figure out how to install 3D desktop: 

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) 

when i got to this part: Now a dialog should ask you to reload your repositories, click Reload. 

Then I got told to manually configure.

In the software sources I've since removed the third party software and authentication key that I put in by following the instructions. But I don't think that did anything. 

I can't remember if I did anything else.  

How do I fix this? Any help appreciated, I've been searching google but not found anything i can use or at least understand :(

---

### Post by dwhitney67 on 2007-11-25
> **DarthChili said:**
> 
jen@jen:~$ sudo dpkg --configure -a
[sudo] password for jen:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

Upon examining the error messages above, it is odd that the mkinitramfs could not find getopt.  Can you verify if you have getopt in /usr/bin.  An easy way to do this is:

```
$ ls /usr/bin/getopt
```

or

```
$ which getopt
```

---

### Post by DarthChili on 2007-11-25
tried this

jen@jen:~$ ls /usr/bin/getopt
ls: /usr/bin/getopt: No such file or directory

---

### Post by dwhitney67 on 2007-11-25
Like I said, that's odd.  Have you deleted anything recently from your system?

Look under Synaptic (System -> Administration -> Synaptic Package Manager) and select for install the package "util-linux", or perhaps easier yet:
```

$ sudo apt-get install util-linux
```

---

### Post by DarthChili on 2007-11-25
jen@jen:~$ sudo apt-get install util-linux
[sudo] password for jen:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I prolly have deleted something :S but I couldn't tell you what, this is all very new to me cause this is the first time I've ever used linux.

---

### Post by DarthChili on 2007-11-25
I decided to look at: places > home folder > file system > usr > bin 

then i scrolled down and didn't come across getopt, so i assume i need to aquire i, where can i get it?

---

### Post by dwhitney67 on 2007-11-25
Here's the problem... Ubuntu, as does many other Linux distros, depend upon a package manager to keep tabs on applications installed on one's system.  It would seem that your package manager is functional, however your system as a whole is missing a critical package (or a subset of a package).

I do not know if you accidentally deleted just "getopt" or the entire package that contains it.  Either way, it appears that it is impossible to even restore the package using the package manager because of a chicken-egg problem.

Maybe an Ubuntu guru can advise you on how to sort out this problem.  IMO, I would just reinstall the OS.

---

