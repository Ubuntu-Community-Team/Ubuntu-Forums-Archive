---
title: "I need help installing WMware Server"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-11-11
I am trying to install VMware Server on Ubuntu Studio 7.10.  I can go so far in the download and then I encounter questions that I don't know how to response.

Below is a copy  of when I am in the installation process:


The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 


 Please advise as how I should proceed.

Thanks,

Explorer716

---

### Post by erginemr on 2007-11-11
Hello,

Your linux header files is in: /usr/src/linux-headers-2.6.22.14
Well, this is mine actually, but you may eaisly learn the correct directory name by browsing your file system via Nautilus (Gnome file manager).

On a side note, you may learn your kernel version by issuing the following command from the console:
uname -r

And you can check whether your kernel header files have been installed (they should have been installed by default, as far as I know), by using synaptic and searching the keyword: "linux-headers".

Good luck with the installation.

P.S. For virtualization, you may also try Virtuabox ([http://www.virtualbox.org/](http://www.virtualbox.org/)), which is also very good performance-wise. They have Gutsy Debian package on their site, so the installation should be more hassle-free.

---

### Post by veloce on 2007-11-11
> **explorer716 said:**
> I am trying to install VMware Server on Ubuntu Studio 7.10.  I can go so far in the download and then I encounter questions that I don't know how to response.

Below is a copy  of when I am in the installation process:

 Please advise as how I should proceed.

Thanks,

Explorer716

There are two dependencies that need to be installed before the vmware installer will work.  You should run:

```
sudo apt-get install build-essential xinetd

```

If your gutsy is 64 bit, then you also need the 32 bit libraries - sorry can't remember the package name.

With these installed, the vmware installer will be able to build the kernel specific bits as it installs.

---

