---
title: "VMware-Player install"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by garyduane on 2007-10-22
When I run VMware-config .pl everything runs fine until:
 None of the pre-built vmmon modules for VMware player is suitable for your running kernel. Do you want this program to try to build the vmmon module for your system (you need to have a C complier on your system)? [yes]

using complier "usr/bin/gcc

what is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

of course the vmware-config.pl stops. I have updated and installed all of the available packages for Ubuntu via "sudo apt-get install build-essential.

Can anyone give me the information to continue the config of VMware player?

 Thanks.

---

### Post by TheAL76 on 2007-10-22
There's a patch you need.

It's called vmware-any-any-update113 I believe. Google it.

---

### Post by sremington on 2007-10-22
You also need to have the kernel headers installed besides the build environment. Try this at a terminal prompt:

```
sudo apt-get install linux-headers-$(uname -r)
```

-Seth

---

### Post by garyduane on 2007-10-23
> **sremington said:**
> You also need to have the kernel headers installed besides the build environment. Try this at a terminal prompt:

```
sudo apt-get install linux-headers-$(uname -r)
```

-Seth

This solved the problem very nicely. Just what was needed. 

Thanks

---

### Post by garyduane on 2007-10-23
> **TheAL76 said:**
> There's a patch you need.

It's called vmware-any-any-update113 I believe. Google it.

Thank you for your help.

---

