---
title: "vmware"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-05-30
looking to install vmware workstation 5.5, i have a problem in the installation, after i accept the license agreement the process give the message :
None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

then another message appeared :
Unable to build the vmmon module.

any idea??

---

### Post by Bachstelze on 2007-05-30
do you have the C compiler (aka "build-essential") installed ?

---

### Post by madmetal on 2007-05-30
> **akkad said:**
> looking to install vmware workstation 5.5, i have a problem in the installation, after i accept the license agreement the process give the message :
None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

then another message appeared :
Unable to build the vmmon module.

any idea??

edit : wrong :KS try..

sudo apt-get install  build-essential

---

### Post by taurus on 2007-05-30
Did you install the build-essential (C compiler) package, yet?

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by shanepardue on 2007-05-30
I don't believe any vmware server-type software can be installed through automatix.

try this patch... [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

---

### Post by madmetal on 2007-05-30
> **shanepardue said:**
> I don't believe any vmware server-type software can be installed through automatix.

try this patch... [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

yeap i saw "workstation" a little late...

---

### Post by akkad on 2007-05-30
i installed the packages u told me about but i still have the same problem.
i did this
sudo aptitude update
sudo aptitude install build-essential
gcc -v

but still the same ???

---

### Post by akkad on 2007-05-30
shanepardue's thnx alot the patch really worked.

---

### Post by shanepardue on 2007-05-30
> **akkad said:**
> shanepardue's thnx alot the patch really worked.
Sweet! Glad it worked!!

---

