---
title: "Virtual PC"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by linuxryan on 2006-09-10
Hey folks, 
I'm a true newbie to linux and Ubuntu. 
How would I installl and run a virtual machine in Ubuntu (my wife won't part with M$).
Is it possible to create a VM and then Ghost an image of my M$ drive to it??
Any sugestions on what version of vm I can use.
Thanks for any help and advice.

---

### Post by scxtt on 2006-09-10
Qemu and vmware are available and you can install either one via aptitude:

```
[FONT="Courier New"]:> aptitude search qemu
p   qemu                                           - fast processor emulator

:> aptitude search vmware
p   vmware-player                                  - Free virtual machine player from VMware
p   vmware-player-kernel-modules                   - vmware-player kernel module dependency package
p   vmware-player-kernel-modules-2.6.15-23         - vmware-player modules for Linux (kernel 2.6.15)
p   vmware-player-kernel-source                    - Source for the vmware-player-kernel drivers.
i   xserver-xorg-driver-vmware[/FONT]
```both have been discussed to death, search the forums ... and check out [EasyVMX](http://www.easyvmx.com/) to create VMs in which you can install XP too ...

---

### Post by linuxryan on 2006-09-10
Thanks Mate, 

You'll definately see me around mre often!!:confused: :confused: :confused:

---

### Post by djsroknrol on 2006-09-10
Hi there...welcome to Ubuntu Forums...check this out for full instructions for a good VM

 [http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by wagerrard on 2006-09-10
Lookng at it from your wife's perspective, it might be better to keep Windows where it is and run Ubuntu in a VM on that OS.

---

### Post by linuxryan on 2006-09-15
Thanks for all your help guys, got Vmware running in windows with Ubuntu installed, now to learn the system#-o #-o #-o #-o

---

### Post by rcatman on 2006-09-15
Awesome. Make sure you try out the different flavors of ubuntu ie kubuntu, xubuntu

I'm partial to kubuntu :)

---

