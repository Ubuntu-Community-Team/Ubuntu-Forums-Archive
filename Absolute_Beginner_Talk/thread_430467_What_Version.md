---
title: "What Version?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-05-02
How can I tell what version of Ubuntu I am using at the present time? I downloaded Feisty but was under the understanding that it didn't work but when I go to updates, It says my operating system is up to date. Upon booting up after POST it gives me the option to log into these operating systems
 
 2.6.20-15 Generic
 2.6.20-15 Generic (Recovery Mode)
 2.6.17-11 Generic
 2.6.17-11 Generic (Recovery Mode)
 2.6.17-10 Generic
 2.6.17-10 Generic (Recovery Mode)
 Memory test
Other Operating Systems
 Windows XP

 I can only log into 2.6.17-10 & Windows XP and cannot figure out how to remove the other versions. And I think I am using Edgy.

---

### Post by oilchangeguy on 2007-05-02
press, alt-ctrl-f1. and to get back press, alt-ctrl-f7.

---

### Post by DrtBikDave on 2007-05-02
Thanks, That was easy. How do I get rid of the non operational versions?

---

### Post by Rui Pais on 2007-05-02
for the kernels:
2.6.20-15 Generic  -> Feisty kernel
2.6.17-11 Generic  -> Edgy kernel

for the base system:
```
cat /etc/lsb-release
```

for the desktop environment, on menus go:
System -> About

Gnome 2.18.1 -> Feisty
Gnome 2.16.X (not sure) -> Edgy

---

### Post by meborc on 2007-05-02
> **DrtBikDave said:**
> Thanks, That was easy. How do I get rid of the non operational versions?

you can delete the kernels you don't use from the synaptic package manager... just search for the version numbers you don't use...

---

### Post by eldepeche on 2007-05-02
If you can't boot into 2.6.17-11 or 2.6.20-15, go into synaptic, and remove linux-image-2.6.17-11-generic or whatever is installed.

---

### Post by Rui Pais on 2007-05-02
> **DrtBikDave said:**
> Thanks, That was easy. How do I get rid of the non operational versions?

What do you mean? delete grub entries? 
```
gksudo gedit /boot/grub/menu.lst
```

Or ensure the kernel packages are removed from your system:
```
sudo aptitude purge <package_name>
``` You can use Tab completion to get the name of package (in your case the kernel image)

---

### Post by Pobega on 2007-05-02
Open a terminal and type **uname -r** to figure out what kernel version you're running.

/etc/issue should be your Ubuntu version, at least that's how it works on Debian.

---

