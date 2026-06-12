---
title: "Updating to OS X El Capitan in a Ubuntu system WITHOUT Refilt"
date: 2015-10-11
forum: Apple Hardware Users
---

### Post by vsanchez1961 on 2015-10-11
Hi,

I want to upgrade my OS X to the El Capitan version. I am afraid to do so because I understand that I will loose the ability to boot to my Ubuntu (Kubuntu) OS. I did not upgrade to Yosemite for the same reason. I need to do it now, so I need to learn to recuperate the Ubuntu OS. I have seen many instructions but all refer to systems using rEFIT. I do not use it anymore since I have my MacPro 11,2, since I use the efibootmgr.

1. This "lost" of the capability to boot Ubuntu ONLY happens to those who are still using rEFIt?? So that I can proceed without a problem?
2. If it will happen to me... are there any instructions on how to recover in that case without resorting to rEFIt??? 

I have a Macbook PRO 11,2 (2013) running 15.04. 

Thanks very much!

---

### Post by Jethro_Borsje on 2015-10-13
Today I upgraded to El Capitan and I have the problem you are afraid of. Before the upgrade my MacBook Pro from early this year always booted in to GRUB from where I decided to start either Linux or OS X. Now my MacBook boots OS X straight away and does not give me the option to start Ubuntu. When I boot while holding the Alt key I only see the drive which has OS X on it. I can not select anything else.

Is there a solution for this?

---

### Post by Jethro_Borsje on 2015-10-14
Just an update: it is easily fixeable, first install the EFI Boot Manager:

```

sudo apt-get install efibootmgr

```

Then check on which partition Ubuntu is installed:
```

$ sudo efibootmgr
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0080,0080
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Mac OS X
Boot0082* 
BootFFFF*

```

Fix the bootorder:
```
$ sudo efibootmgr -o 0000,0080
```

Now GRUB is showing again.

---

### Post by vsanchez1961 on 2015-10-14
Thanks Jethro_Borsje. How did you manage to boot in Linux. Did you manage to boot a live version from a USB stick? O did you use a CDROM?

---

### Post by Jethro_Borsje on 2015-10-14
Live version from USB.

---

