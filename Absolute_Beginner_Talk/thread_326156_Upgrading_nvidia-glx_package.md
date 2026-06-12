---
title: "Upgrading nvidia-glx package"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by barnjo on 2006-12-27
Hi all, managed a while back to get the nvidia drivers installed on my Edgy Eft PC using the guide at albertomilone.com and his repos

Now when I try to upgrade it gives this message:

```
jonny@jonny-ubuntu:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: nvidia-kernel-1.0.9629
E: Broken packages
jonny@jonny-ubuntu:~$ aptitude search nvidia-kernal
jonny@jonny-ubuntu:~$ aptitude search nvidia-kernel
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.8776          -                                           
v   nvidia-kernel-1.0.9626          -                                           
v   nvidia-kernel-1.0.9629          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source
```

Is it safe just to install the nvidia-kernel package, because at the moment my grub menu only has linux-2.6.17-10-generic kernel header to boot up from.

Previous attempts to install the drivers had resulted in an extra header being added to the grub boot menu, namely a -386 as well as -header.

When this happened X server wouldn't start when selecting -header and my wireless dongle wouldn't start when selecting -386.

Thanks in advance for any help

---

### Post by tzulberti on 2006-12-27
> **barnjo said:**
> Hi all, managed a while back to get the nvidia drivers installed on my Edgy Eft PC using the guide at albertomilone.com and his repos

I don't know why did you use external Repos. You should have enable Universe and Backports, and there is an nvidia-glx package

> 
Now when I try to upgrade it gives this message:

[code]jonny@jonny-ubuntu:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: nvidia-kernel-1.0.9629
E: Broken packages


This is happening because apt could not install the nvidia-kernel-X. Even if you try to install it, it would fail. My advice: enable backports and universe, and then try to install nvidia-glx...

---

