---
title: "VMWare Tools:  Need to install Kernel Source"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by dopamine5 on 2007-03-28
Hey all,

Down to business:

Used Daemon tools in WinXP to install ubuntu into a virtual machine.  Everything works great so far, however installation of VMware tools requires several things that the default install left out.

So far I added make and gcc etc, but I am now to a point where running the **vmware-install.pl **gets stuck looking for source code in:

**/usr/src/linux/include**

which of course doesn't exist.  (I would be copy pasting right from the VM if I had the tools installed ;) )

Anyway, what I know so far is I run **uname -a** to receive this info:
[I]
1.6.15-28-386[/I]

My kernel version, correct?

Then I am lost when it comes to this command:

**sudo apt-get install put-what-kernel-info-goes-here**


I'm still looking but perhaps not hard enough or in the right places.  I just need MY kernel versioon of source installed is what I believe will fix my problems.

Thanks for any help :)

---

### Post by yabbadabbadont on 2007-03-28
sudo apt-get install linux-source

---

### Post by codejunkie on 2007-03-28
> **dopamine5 said:**
> Hey all,

Down to business:

Used Daemon tools in WinXP to install ubuntu into a virtual machine.  Everything works great so far, however installation of VMware tools requires several things that the default install left out.

So far I added make and gcc etc, but I am now to a point where running the **vmware-install.pl **gets stuck looking for source code in:

**/usr/src/linux/include**

which of course doesn't exist.  (I would be copy pasting right from the VM if I had the tools installed ;) )

Anyway, what I know so far is I run **uname -a** to receive this info:
[I]
1.6.15-28-386[/I]

My kernel version, correct?

Then I am lost when it comes to this command:

**sudo apt-get install put-what-kernel-info-goes-here**


I'm still looking but perhaps not hard enough or in the right places.  I just need MY kernel versioon of source installed is what I believe will fix my problems.

Thanks for any help :)

running the command below in a terminal will install the kernel headers and the basic compilers that's what it's wanting

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by dfreer on 2007-03-28
> 1.6.15-28-386

My kernel version, correct?

Wow. I assume this is a typo, ummm the 1.6.15 kernel would be QUITE old. I think the command you are looking for is:
```
sudo apt-get install linux-source
```
Although I can't be sure, that should install the source code for whatever kernel you are currently running.

---

### Post by dfreer on 2007-03-28
> sudo apt-get install build-essential linux-headers-`uname -r`
Yeah, make sure you install the **build-essential** package, you'll need that :D

---

### Post by dopamine5 on 2007-03-28
> **codejunkie said:**
> running the command below in a terminal will install the kernel headers and the basic compilers that's what it's wanting

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Working perfectly and installing as I type, thank you!

Also, yabbadabbadont, I took his command over your as it took in the direct output of uname, so, thanks anyway :)

This could get addicting fast.  \\:D/

---

