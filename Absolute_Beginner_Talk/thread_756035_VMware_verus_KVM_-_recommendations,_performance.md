---
title: "VMware verus KVM - recommendations, performance"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-04-15
I'm thinking of utilizing Ubuntu KVM in our Disaster Recovery process.  My thinking is that we can use the next Ubuntu release - 8.04 - and its improved KVM funcationality.  Am I understanding this correctly -- that KVM - Kernel Virtual Machine - functionality will allow us to virtualize a Windows XP environment on top of Ubuntu?  My thinking is that we can provision at our DR site an Ubuntu installation CDROM along with a KVM file containing our virtualized Windows XP and its load of software and configuration and expect it to run on most any PC that utilizes dual core CPU's?

The reason this sounds so interesting is that we have a very complicated workstation setup that takes a lot of time to install manually via a script.

I would appreciate any comments and suggestions.

Thanks

Carl

---

### Post by cardinals_fan on 2008-04-15
How about VirtualBox?

---

### Post by gsmanners on 2008-04-16
KVM is a good choice and it's my personal preference.

```
egrep '(vmx|svm)' /proc/cpuinfo
```

[https://wiki.ubuntu.com/KvmVirtManagerEtc](https://wiki.ubuntu.com/KvmVirtManagerEtc)

The important thing is not how many cores your CPU has, but whether that CPU supports virtualization

---

### Post by cwmoser on 2008-04-16
Of VMware, Virtual Box, and KVM, what are the pros and cons?

A con for KVM is that it requires a special type CPU

Would one expect KVM to allow the virtualized OS to run faster?

How about performance and compatibility between Virtual Box and VMware?

Carl

---

### Post by gsmanners on 2008-04-16
VMs don't require virtualization, but they will run a whole lot slower without it.

If you want a nice comparison, there's always wikipedia:

[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

---

