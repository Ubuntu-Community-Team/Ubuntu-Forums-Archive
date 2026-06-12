---
title: "Broken x-server ubuntu removed my nvidia drivers"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Raatikainen on 2006-11-04
Ubuntu removed my xgl drivers while updating packages and installed another nvidia driver. Now this older version is stopping me from getting the nvidia glx drivers. Desperate pea for help and that thank you in advance.

raati@raati-laptop:~$ sudo apt-get install nvidia-glx
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

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9625
E: Broken packages

---

### Post by rianquinn on 2006-11-04
I have the same problem. Its from the Repo

```
deb http://amaranth.selfip.com edgy lrm
```

I commented this out and ran

```
apt-get install nvidia-glx
```

and apt installed the old nvidia drivers which works fine. However, I would like the new ones and am confused why this repo is broken.

Rian

---

### Post by buckweat420 on 2006-11-05
Hello,
I was having the same issue with this, I installed Nvidia-glx and nvidia-kernel-common. I tried to run the nvidia-glx-config enable command and i get this error. 

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

I also tried to Edit the xorg.conf file manually but when i change nv to nvidia i break xserver and i have to change it back.

I am using 6.10 Edgy of ubuntu, What am i doing wrong? Is there anything i am missing.

---

### Post by DanSchnell on 2006-11-05
> **rianquinn said:**
> I have the same problem. Its from the Repo

```
deb http://amaranth.selfip.com edgy lrm
```

I commented this out and ran

```
apt-get install nvidia-glx
```

and apt installed the old nvidia drivers which works fine. However, I would like the new ones and am confused why this repo is broken.

Rian

I have the exact same problem.  I really think there is a problem with the amaranth repo.

I also have the original poster's kernel problem while trying to install nvidia-glx

---

