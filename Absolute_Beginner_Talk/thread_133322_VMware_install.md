---
title: "VMware install"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-20
I have tried several other post for trying to install .rpm and .tar.gz progams and no solution has been found I do not know what to do with this. I am using the VMware player so I can still use windows... Am I going about this right or not? If  so how do I install either of these types of problems. I am using KDE but can swith to Gome...

---

### Post by cilynx on 2006-02-20
First off:  VMWare Player only supports running virtual machine images that were created elseware.  Unless you have a Windows VMWare image laying around, it's not going to help you much.  However, VMWare recently released a product they call VMWare Server which is also free that allows you to create your own virtual machine images.  This is probably the route you want to go.  Anyways...

VMWare has a quasi-magic installer...

Get the VMWare tarball (VMware-player-1.0.1-19317.tar.gz or VMware-server-e.x.p-20925.tar.gz or whatever).  Decompress it to a folder on you desktop.  Open up a terminal and change to the directory on your desktop that you just made.  Run the vmware-install.pl script with root permissions.  The install script will hold your hand from there.  Accepting the default values should be fine.  Make sure you have the linux-headers for the kernel you're running as well as the general development tools (gcc, make) installed before you run the VMWare installer as it needs to be able to build some new kernel modules.

Assuming you made a directory on your desktop called VMWare and the decompressed the tarball there:

```

rcw@pyth:~$ cd Desktop/VMWare/vmware-server-distrib/
rcw@pyth:~/Desktop/VMWare/vmware-server-distrib$ ./vmware-install.pl 

```
That should take care of you...
As for my setup, after doing the install, "VMWare Server" showed up under Applications -> System Tools.  This is under Gnome.  I assume it would work in KDE as well.

---

