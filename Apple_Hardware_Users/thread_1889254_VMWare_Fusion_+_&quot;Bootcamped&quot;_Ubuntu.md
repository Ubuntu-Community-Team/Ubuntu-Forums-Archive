---
title: "VMWare Fusion + &quot;Bootcamped&quot; Ubuntu"
date: 2011-12-01
forum: Apple Hardware Users
---

### Post by Geek 2.0 on 2011-12-01
Hello,

I am running a triple boot Mac OS/Windows/Ubuntu, but not using rEFIt. I have two internal hard drives, so rEFIt is unnecessary, because Ubuntu is on the non-boot drive. Everything is working fine for just booting into each system individually.

However, I am trying to set up my computer to allow me to use VMWare Fusion from Mac OS to run either of the other two systems. This feature is supported  by VMWare for running a Windows Boot Camp, but not for Ubuntu, seeing as Apple does not support it. However, I know it is possible, as many people have done it before.

I have not run into any issues creating my rawdisks or getting VMWare to find the disk. However, I've hit a huge roadblock. Upon booting through VMWare Fusion, I get the error (immediately):
```
error: no such partition
grub rescue>
```
And I am unable to get it to do anything. I can boot Ubuntu from a LiveCD in the VM.

As much as I want to figure out how to fix it, I'm just as concerned with what's going on. I have a very shallow understanding of MBRs and bootloaders and such. Does anyone know what is going on or what the error even means? It seems somewhat common, but most people just suggest deleting the Ubuntu partition and reinstalling it, but I find that quite pointless in my situation seeing as it still boots normally when not run through VMWare Fusion.


Thanks,
Joshua Franz

---

### Post by Geek 2.0 on 2011-12-03
Would it be better for me to post this somewhere else?

---

