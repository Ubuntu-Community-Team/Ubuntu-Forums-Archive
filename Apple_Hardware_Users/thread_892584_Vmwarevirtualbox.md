---
title: "Vmware/virtualbox"
date: 2008-08-17
forum: Apple Hardware Users
---

### Post by hvc123 on 2008-08-17
Hey all 

i have ubuntu hardy server (only/no dualboot) on my christmas pud (powerpc imac g4 usb2)

im having trouble installing vmware server i.e. it wont instal li get a error of 
"Your processor does not support the ^cpuid instruction. VMware Player will not
run on this system.

Your /proc/cpuinfo is:

processor       : 0
cpu             : 7455, altivec supported
clock           : 1249.999995MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 82.94
timebase        : 41600571
platform        : PowerMac
machine         : PowerMac6,1
motherboard     : PowerMac6,1 MacRISC3 Power Macintosh
detected as     : 287 (Flat panel iMac)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld
Execution aborted.
"
when i try to compile VirtualBox i get " 
Checking for environment:
  ** Cannot determine system!"
this is my kernal :- 2.6.24-16-powerpc

is there a way of getting vmplayer/server to install.

thanks

---

### Post by bogdanbiv on 2008-08-17
I downloaded [http://vmware.com/pdf/server_datasheet.pdf](http://vmware.com/pdf/server_datasheet.pdf) and it does not mention PPC architecture at all.
Actually, if the VMWare player is not supported for PowerPC processors why would the VMWare server support it? Have you got a technical manual saying that the server does work?
Could you post a link to it? (like find the web version of it and post the link here)

Regarding VirtualBox, please read this:
[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)
> This page is for end users who are looking for information about how to download and run VirtualBox.
In order to run VirtualBox on your machine, you need:
    * Reasonably powerful x86 hardware. Any recent Intel or AMD processor should do.

As it says, it does not support the PowerPC architecture.

---

### Post by hvc123 on 2008-08-17
no i just got a vmware application(prebuilt vm) and what to run it.

what a mare if you cant install vmware or vbox.. wonder if qemu can run vms

---

### Post by bogdanbiv on 2008-08-17
From a Google ad:
> Run Windows on Your Mac.
Try Free or Order Online Today!
[www.VMware.com/Mac](www.VMware.com/Mac)

I was googling for [http://www.google.ro/search?q=qemu+powerpc](http://www.google.ro/search?q=qemu+powerpc)
I have found a site on topic, but the information is kinda old - try your luck though

---

### Post by hvc123 on 2008-08-17
just installed qemu

ran qemu vmware.vmdk and it WORKS!!!!!

well so far its taking a while to boot...


qemu works but is VERY VERY SLOW, KVM does not install is there a way to install kvm (accelerated qemu)

---

### Post by ssam on 2008-08-17
kvm only got ported to powerpc in kernel 2.6.26
[http://kernelnewbies.org/Linux_2_6_26](http://kernelnewbies.org/Linux_2_6_26)
hardy has 2.6.24, and intrepid (ubuntu 8.10) will have 2.6.26

are you wanting the guest to be powerpc? if you want to have a x86 guest then you need emulation, rather virtualisation. qemu can do this, but it wont be fast.

---

