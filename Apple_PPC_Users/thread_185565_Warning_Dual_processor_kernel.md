---
title: "Warning: Dual processor kernel"
date: 2006-05-31
forum: Apple PPC Users
---

### Post by autocrosser on 2006-05-31
OK--I've been using Dapper from mid-Nov (I'm a early adopter:-D) & I'll warn everyone that has a Mirror-Door G4 than the current SMP kernel WILL NOT WORK--There is a long-standing bug with the -smp kernel (anything past the -11-smp kernel) causing a clock issue with the processors--currently there is NO work-around unless you want to run single proccessor:-?--YOU HAVE BEEN WARNED--I'll update this as each new kernel becomes available--think of it as a "heads up" for the Dual G4's-- I DO miss using my second proccessor:(---But I am loyal to Ubuntu & will beta test until my fingers are but stubs:-k
 
***OK--I think that this thread can be closed***

---

### Post by joshuapurcell on 2006-05-31
I'm not familiar with this problem. I'm assuming you could still compile a kernel from kernel.org and not have this same problem, correct?

---

### Post by autocrosser on 2006-05-31
Well--I tried to do a 2.6.16.1 with the .config from my broken -23-smp kernel...still had a broken kernel after:???:--I re-loaded Dapper in mid-March & lost the -11-smp that was the last one that worked (was issued in mid-Dec)--If you want to try it, go ahead, but there is no current config that works.

Note: look at Launchpad bugs# 29420 & 37553

---

### Post by hotani on 2006-06-01
Yep, it bit me pretty hard when I tried it. This was on a fresh install so I "fixed" it by reinstalling.

---

### Post by BoneKracker on 2006-06-03
There are usually significant changes between major versions (like 2.15 > 2.16).  I know they recommend you don't use "oldconfig" in those cases.  Maybe you shouldn't reuse your configuration?

---

### Post by autocrosser on 2006-06-03
I followed the PPC Wiki (didn't use "oldconfig")--I tried compiling several 2.6.15 kernels & a couple of 2.6.16 kernels--no joy in any case--if you compile a working kernel I'm interested.

---

### Post by autocrosser on 2006-06-11
Just got this info from the kernel maintainers--

** Attachment added: "Possible fix for powerpc SMP systems."
   [http://librarian.launchpad.net/3024561/git-0c2aca88bdac4254a13466fb108733d243a118b6.patch]("http://librarian.launchpad.net/3024561/git-0c2aca88bdac4254a13466fb108733d243a118b6.patch")

** Bug 44040 has been marked a duplicate of this bug

** Bug 37553 has been marked a duplicate of this bug
AND THIS FROM Ben Collins!!!

Patch applied.

** Changed in: linux-source-2.6.15 (Ubuntu)
       Status: Confirmed => Fix Committed
       Target: None => dapper-updates


Strange clock behaviour on powerpc-smp
[https://launchpad.net/bugs/29420]("https://launchpad.net/bugs/29420")

KEEP YOUR FINGERS CROSSED!!!!

---

### Post by dmoore7 on 2006-06-13
[QUOTE=autocrosser]Just got this info from the kernel maintainers--

** Attachment added: "Possible fix for powerpc SMP systems."
   [http://librarian.launchpad.net/3024561/git-0c2aca88bdac4254a13466fb108733d243a118b6.patch]("http://librarian.launchpad.net/3024561/git-0c2aca88bdac4254a13466fb108733d243a118b6.patch")

** Bug 44040 has been marked a duplicate of this bug

** Bug 37553 has been marked a duplicate of this bug
AND THIS FROM Ben Collins!!!

Patch applied.

** Changed in: linux-source-2.6.15 (Ubuntu)
       Status: Confirmed => Fix Committed
       Target: None => dapper-updates


Strange clock behaviour on powerpc-smp
[https://launchpad.net/bugs/29420]("https://launchpad.net/bugs/29420")

KEEP YOUR FINGERS CROSSED!!!![/QUOTE]


Does this mean that a new download of Dapper will have the patch applied to it?

---

### Post by robbyt on 2006-06-15
anyone try this patch out yet? (or better yet, make up some .debs?)

---

### Post by nkbj on 2006-06-15
The updated kernel (2.6.15-25) has hit the update repositories.

---

### Post by Deohgee on 2006-06-20
Hmmmm I'm new to the whole Linux on PPC thing but I'm willing to tackle this too.  I'd love to have my Dual G4 roll with two instead of one

---

### Post by osuwirelesshd on 2006-07-21
Hey just wondering 2 things:

How do I check to see if I am running dual proc kernal? I looked at the activity monitor and there is only one graph under the cpu usage. Am I to interpret this as only running off 1 proc?

Has there been any developments on this issue in the past 4 weeks?

Thanks.

---

### Post by autocrosser on 2006-07-22
Well--I don't know--I have sold my Mirror-Door & went the "new" Steve Jobs way--I'm now in the Intel camp with a custom-made Dual 2.8 unit--(no Windozs in sight)--only Linux inside8)

---

### Post by hotani on 2006-07-24
osuwirelesshd: go to system monitor, click the 'Resources' tab. Under the top graph for CPU History there should be something like "CPU 1" and "CPU 2." If it just says "CPU" and shows the usage percentage, then you're still on one.

BTW, I have since upgraded as well - to an AMD dual core 'X2' - said 'bye-bye' to Apple. I still have the G4 and will work on getting it up and running soon but may end up selling it.

---

### Post by dlaroe on 2006-07-30
SMP works for me it seems.
Fresh install of 6.06 LTS, I'm a new owner of a used Sawtooth G4 the previous owner swapped a dual 500MHz daughterboard into.

Update Manager suggested a updated kernel, 2.6.15-26-powerpc.
Using Synaptic I installed the SMP version  2.6.15-26-powerpc-smc.
It was still using the original kernel from the OS install.
Hmm, I don't have grub, I have yaboot and it is looking in /boot/ for its vmlinux sym-link but Synaptic put the sym-link in /.
Telling yaboot.conf to look in / and running ybin -v and a reboot made everything work.(Holy Penguin Pee, :D the priceless value of Free software!) 

System Monitor shows two processors as well.

-Dale

Fyi...

dlaroe@whatamac:~$ cat /proc/cpuinfo
processor       : 0
cpu             : 7400, altivec supported
temperature     : 30-32 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.66

processor       : 1
cpu             : 7400, altivec supported
temperature     : 31-33 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.66

total bogomips  : 99.32
timebase        : 24907667
machine         : PowerMac3,1
motherboard     : PowerMac3,1 MacRISC2 MacRISC Power Macintosh
detected as     : 65 (PowerMac G4 AGP Graphics)
pmac flags      : 00000004
L2 cache        : 1024K unified
pmac-generation : NewWorld
dlaroe@whatamac:~$ dmesg |head
[    0.000000] Total memory = 512MB; using 1024kB for hash table (at cff00000)
[    0.000000] Linux version 2.6.15-26-powerpc-smp (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Mon Jul 17 19:59:02 UTC 2006
[    0.000000] Found initrd at 0xc1900000:0xc20c9000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x07
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 2, mapped at 0xfdf40000
[    0.000000] PowerMac motherboard: PowerMac G4 AGP Graphics
[    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
dlaroe@whatamac:~$

---

### Post by glogau on 2006-08-09
Patch doent work

---

### Post by FNM on 2006-08-24
I've got both processors running great with the 2.6.16 SMP kernel on Debian testing. It's the G4 "Gigabit Ethernet" model, circa June 2000 to be exact. 

Also, to the person wondering why their System Monitor is only showing one processor, it could be because you're using a kernel that is not aware of the other processor. If you're using a dual G4, with a SMP kernel, you'll see two processors show up under cat /proc/cpuinfo, or System Monitor.

```
processor       : 0
cpu             : 7400, altivec supported
temperature     : 34-37 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.66

processor       : 1
cpu             : 7400, altivec supported
temperature     : 30-32 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.66

total bogomips  : 99.32
timebase        : 24907950
machine         : PowerMac3,3
motherboard     : PowerMac3,3 MacRISC Power Macintosh
detected as     : 65 (PowerMac G4 AGP Graphics)
pmac flags      : 00000014
L2 cache        : 1024K unified
pmac-generation : NewWorld

```

---

### Post by Pza3.14159 on 2007-05-25
My 64 bit emachines laptop finally showed its true (emachines) nature. I picked up this dual G4 450 for a song at a garage sale and had no problems putting feisty on it. Has anyone tried using this "2.6.16 SMP kernel" to enable the second processor in such an environment? I like Feisty, but would like it to be little more zippy. Upgrading the video card is my second option, but enabling the second processor would be free as in beer (and speech).

---

### Post by stmiller on 2007-05-25
This thread is out of date. Mods please 'unstick' this sticky!

---

### Post by RealG187 on 2007-10-21
So those new iMacs w/ Dual Core dont work?

---

