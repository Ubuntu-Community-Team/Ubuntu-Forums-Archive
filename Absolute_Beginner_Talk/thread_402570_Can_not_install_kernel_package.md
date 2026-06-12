---
title: "Can not install kernel package"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mahmoud Refat on 2007-04-05
Hi, i am very new at this.
i am using kubunt 6.02 and i have been trying to compile the kernel.
i am following this tutorial [http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu)
it's kinda clear and simple, the problem is that when i got to the point where i should downlaod the kernel-package, i got this error:

root@mahmoud-desktop:/# apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package

i've been trying to solve thie problem for 3 days now, and still i can't. any one can help? 
thank you

Mahmoud

---

### Post by chalex on 2007-04-05
I'm not sure what Falko means by "kernel-package".  Try the following commands to find the possible package names 
```

apt-cache search linux-image
apt-cache search linux-headers
apt-cache search linux-source

```
apt-cache show package_name for more info on the package.  You can, of course, do this through the Search button in Synaptic.

---

