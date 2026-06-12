---
title: "Is this box 64-bit or 32-bit?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by admarshall on 2007-09-14
After two decades of forking about with PCs, I'm demoting myself back to Absolute Newb.  

I've got this second-hand box here started up with Ubu' and i don't know how to quickly check whether it's actually running as the 64-bit box it's claimed to be or not.

"uname -a" returns:

[INDENT]Linux vice-h0 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux[/INDENT]

"cat /proc/cpuinfo" says processor 1 and 2 both have "clflush size    : 64".  Is that the ticket?

What the hey, here's all of "cpuinfo":

[INDENT]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.234
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc 
pni monitor ds_cpl cid cx16 xtpr
bogomips        : 6007.14
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.234
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc 
pni monitor ds_cpl cid cx16 xtpr
bogomips        : 6000.39
clflush size    : 64
[/INDENT]

---

### Post by death__machine on 2007-09-14
I think that pentium 4's are 32 bit processors..
Am not sure but i strongly do believe  they are 32 bit..

---

### Post by misfitpierce on 2007-09-14
> **death__machine said:**
> I think that pentium 4's are 32 bit processors..
Am not sure but i strongly do believe  they are 32 bit..


Untrue. While earlier models are 32 bit only... The later 64 bit pentium 4 models are 64 bit capable. Socket 775 is he newer P4 socket fitting. 

[http://www.hardwaresecrets.com/article/105](http://www.hardwaresecrets.com/article/105)


According to that with you at the 630 model maybe it says that all 64 bit P4 models come with 2MB L2 Cache and from what you posted which is  cache size      : 1024 KB = 1MB L2 cache it would seem as though you dont have a 64 bit P4 CPU... ALSO... Your cpuID level is 5 which according to that link shows that ID level 5 is the previous model setup without 64bit. Lvl 6 is the 64 bit line. Quite sure. Sorry :(

I could be wrong but im quite sure I got the homework right.... :( Sorry friend.

---

### Post by bikeboy on 2007-09-14
Later P4's have emt64 (implementation of AMD's amd64). I would expect x86_64 or something along those lines to be in the flags if it was a 64 bit processor.

edit: flags being part of your /proc/cpuinfo output above. But it's not there.

---

### Post by admarshall on 2007-09-14
Thanks all.  But, jeez, i'm still confused, maybe more now than before.  Aren't there one or two simple console commands i can type in to check whether this box is:
1. capable of 64-bit operation or not
2. running as 64-bit now or not

---

### Post by afonic on 2007-09-14
If you installed the i386 version from Ubuntu page then it is running as 32bit. What does uname -a show?

If you have the bandwidth and spare CD to try, download the 64bit ISO:
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64)

If it boots you have 64bit in your CPU, if it gives an error about "this version of Ubuntu needs a 64bit processor" then you have one of the old Intels without 64bit.

---

### Post by hyper_ch on 2007-09-14
> **afonic said:**
> If you have the bandwidth and spare CD to try, download the 64bit ISO:
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64)

That's also what I would have suggested... except that you don't use a spare cd but a RW one.... to have a couple of them is quite nice; it's not necessary to burn for each experiment a blank one ;)

---

### Post by admarshall on 2007-09-14
That's a bit over the top for checking a machine's hardware configuration, don't you think? 

Surely there must be some command-line commands to discover this info. 

"uname -a" and "cat /proc/cpuinfo" appear in the first post of this thread.

---

### Post by admarshall on 2007-09-14
Re. the post by "misfitpierce : 5 Hours Ago"

I should have read your post more closely.  Sorry.  I can see your logic -- and maybe i'm in denial -- but i'm not yet sure the "cpuidlevel: 5" from "cat /proc/cpuinfo" is the same as what that article calls an Intel CPU number starting with "5", as in:
[indent]Pentium 4 processors with 64-bit technology use a numbering system which starts with "6", while the processors without this feature start with "5"[/indent]

Thanks though!  That's a good tip.  

I just still can't quite believe there's not a quick and reliable way to do this from the command line. Oh well... next...

---

### Post by bwhitaker on 2007-09-14
Are you merely trying to determine if you have 64bit capable hardware, or if you're running a 64bit os?


To determine if you are running a x86_64 system:

The easiest way I've found to see if your linux install is 64bit  is checking to see if you have a /lib64, /usr/lib64, /usr/local/lib64  directory.

Also checking uname -a will usually give you the proper arch

i.e. on your's the i686 at the end should mean you are running a 32bit kernel.

here is the output from a 64bit SLES system I have in production, note the x86_64(thats the arch of your running system) at the end:
```

Linux devbox1  2.6.16.21-0.8-default #1 Mon Jul 3 18:25:39 UTC 2006 x86_64 x86_64 x86_64 GNU/Linux

```

To tell if the hardware is capable harder, the only sure fire way I've found is trying to boot the 64bit installer, when it attempts to execute 64bit code it will error.

---

### Post by PmDematagoda on 2007-09-14
I don't know why this happens but if I try and see if my computer can support 64-bit while in a 32-bit system, the 32-bit system keeps trying to convince me that the processor is 32-bit though I know that my processor supports 64-bit, anyway, could you post the model of your processor?

For example mine is:-

Family 15 Model 4 Level 1

---

### Post by rsambuca on 2007-09-14
> **misfitpierce said:**
> Untrue. While earlier models are 32 bit only... The later 64 bit pentium 4 models are 64 bit capable. Socket 775 is he newer P4 socket fitting. 

[http://www.hardwaresecrets.com/article/105](http://www.hardwaresecrets.com/article/105)


According to that with you at the 630 model maybe it says that all 64 bit P4 models come with 2MB L2 Cache and from what you posted which is  cache size      : 1024 KB = 1MB L2 cache it would seem as though you dont have a 64 bit P4 CPU... ALSO... Your cpuID level is 5 which according to that link shows that ID level 5 is the previous model setup without 64bit. Lvl 6 is the 64 bit line. Quite sure. Sorry :(

I could be wrong but im quite sure I got the homework right.... :( Sorry friend.

It sure looks to me like he has 2 x 1MB L2 cache.  If you have the actual part number written on the cpu itself I could let you know for sure what processor you have.  I am thinking that you do have a 64bit processor - Prescott maybe?

---

### Post by RomeReactor on 2007-09-14
Hi. To determine if your processor is 64 bit capable, try running:
```
sudo lshw -C processor
```
There are a couple of things to look for; here's mine, for instance:
```
  *-cpu                   
       description: CPU
       product: AMD Sempron(tm) Processor 2800+
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Sempron(tm) Processor 2800+
       slot: Socket 940
       size: 1600MHz
       capacity: 3GHz
       **width: 64 bits**
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt **x86-64** 3dnowext 3dnow up pni lahf_lm
```

Note the first entry in bold tells you it's running a 64 bit OS; in case you're running a 32 bit OS, the second entry tells you it is indeed capable. I could be mistaken, though; I only have Feisty 64 bit in my system at the moment, so I couldn't check what the output is on a 32 bit system.

---

### Post by rsambuca on 2007-09-14
> **RomeReactor said:**
> Note the first entry in bold tells you it's running a 64 bit OS; in case you're running a 32 bit OS, the second entry tells you it is indeed capable. I could be mistaken, though; I only have Feisty 64 bit in my system at the moment, so I couldn't check what the output is on a 32 bit system.

Good call on the lshw command.  

Just for reference, I have run the command on both my 32bit and 64bit systems.  It was the same on both (I have an AMD Athlon64).  They both indicated 64 bit width.

---

### Post by RomeReactor on 2007-09-14
> **rsambuca said:**
> Just for reference, I have run the command on both my 32bit and 64bit systems.  It was the same on both (I have an AMD Athlon64).  They both indicated 64 bit width.

Hhhmmm... so I guess that would leave using lshw only to check if the processor is 64-bit capable, and **uname -m** to verify which architecture is actually running...

---

### Post by admarshall on 2007-09-15
Hey RomeReactor, [FONT="Fixedsys"]lshw[/FONT] does indeed seem to be The Solution.  Great tip!!!   Just what i was looking for -- plus, the Ubu' alternative to SuSE's "hwinfo", (HardWare Info) command, which i was also looking for.  Thanks!

> **RomeReactor said:**
> Hi. To determine if your processor is 64 bit capable, try running:
```
sudo lshw -C processor
```

I'd never heard of "Hardware Lister" before:
```
madm@vice-h0:~$ whatis lshw
lshw (1)             - list hardware
```
It's help and man pages don't tell you much about how to use it, but it's [project wiki page]("http://ezix.org/project/wiki/HardwareLiSter") does.  From "man lshw": [http://ezix.org/project/wiki/HardwareLiSter]("http://ezix.org/project/wiki/HardwareLiSter"). 

You wrote:
> **RomeReactor said:**
> Note the first entry in bold [in the lshw output in RomeReactor's post, above] tells you it's running a 64 bit OS; in case you're running a 32 bit OS, the second entry tells you it is indeed capable... Feisty 64 bit... couldn't check what the output is on a 32 bit system.

In comparison to RomeReactor's "lshw" output (in his post above) mine also seems to say my CPU has 64-bit capability.  (See BeLow.)

But i also tried "sudo lshw -C **system**", listing another "class" described at the project web page as "used to refer to the whole machine", and "system" says "32-bit".  

That seems to be saying that the operating system, Ubuntu Feisty, is running as 32-bit, but the hardware (CPU, at least) is capable of 64-bit operation.  Make sense?  

Note: someone else suggested looking for /lib64, /user/lib64 or /usr/local/lib64.  I only have this:
```
madm@vice-h0:~$ ls /usr/lib64/libfakeroot/
libfakeroot-sysv.so  libfakeroot-tcp.so
```

Anyway, using **bold** as RomeReactor did for relevant output, here's my "lshw" output:
```
madm@vice-h0:~$ sudo lshw -C **system**
vice-h0                   
    description: Computer
    **width: 32 bits**
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=75BD3125-C4B0-11DA-999B-00112FEBB9DF
madm@vice-h0:~$ sudo lshw -C **processor**
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) 4 CPU 3.00GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 15.4.9
       serial: 0000-0F49-0000-0000-0000-0000
       slot: J2E1
       size: 3GHz
       capacity: 3060MHz
       **width: 64 bits**
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **x86-64** constant_tsc pni monitor ds_cpl cid cx16 xtpr
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          **width: 64 bits**
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
madm@vice-h0:~$ 

```

The [Hardware Lister project page]("http://ezix.org/project/wiki/HardwareLiSter") has a section on interpreting it's output.  

I've still got to read more of that page, but **NOW** it does indeed seem like time to **specifically** download a 64-bit version of Ubuntu for trial and, likely, later replace the current Ubu' version installed.  

Thanks again!  Thanks also to a lot of informative posts from others, too!

Just a bit more from the [lshw project page]("http://ezix.org/project/wiki/HardwareLiSter"):
> lshw (Hardware Lister) is a small tool to provide detailed information on the hardware configuration of the machine. It can report exact memory configuration, firmware version, mainboard configuration, CPU version and speed, cache configuration, bus speed, etc. on DMI-capable x86 or EFI (IA-64) systems and on some PowerPC machines (PowerMac G4 is known to work).

PS: "hwinfo", "hardinfo", "procinfo" and "discover" are also available via Ubuntu repositories.  Just installed them all -- plus "sensord" to hopefully monitor my hard-drives' state of reliability.  But only "hardinfo", a GUI application, seems as quick and easy to use and almost as comprehensive as "lshw".  Unfortunately under it's "Processor" section, "hardinfo" ignores the "x86-64" capability flag output by "lshw" on this machine and it says nothing about the bit level under its "Operating system" section.

---

### Post by RomeReactor on 2007-09-15
Glad you could sort it out! Looks like your processor is 64-bit capable after all. Following your suggestion I also ran **lshw -C system**, and although I have Feisty 64-bit, the width showed up as 32:
```
ubuntu                    
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0016-0000EC566FDC
```

That was odd. Anyaway, when in doubt you can use **uname -m** to find out which architecture you're currently running.

If you *do* decide to use the 64-bit version, you'll need these packages to get Java going in Firefox 64-bit:
```
sudo apt-get install java-common java-gcj-compat java-gcj-compat-plugin sun-java6-bin sun-java6-jre sun-java6-fonts j2re1.4 j2re1.4-mozilla-plugin
```
To get Flash working, you can use [this script by Kilz]("http://ubuntuforums.org/showthread.php?t=476924&highlight=flashplayer").

---

### Post by admarshall on 2007-09-15
Thanks for the added tips.  

But what is **uname -m** returning on your box?  It simply returns "i686" on this box.

Re the output from **lshw -C system**,  I'm now thinking this reflects the bit-level of the mainboard's bus.  Try **lshw -C bus** and i suspect you'll also see "width: 32" with each bus-entry output.  

To me, this means that even though the CPU is 64-bit, the system is running at 32-bit because the mainboard's bus is only capable of (or set to run as?) 32-bit -- which might suggest a short-sighted choice of motherboards when building this box?  :(  ;)

Here's the first part of the **lshw -C bus** output on this box:```
  *-core
       description: **Motherboard**
       product: D915GAV
       vendor: Intel Corporation
       physical id: 0
       version: AAC64134-404
       serial: LAAV61418019
       slot: J5A1
  *-usb:0
       description: USB Controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
       vendor: Intel Corporation
       physical id: 1d
       bus info: pci@00:1d.0
       version: 03
       **width: 32 bits**
       clock: 33MHz
       capabilities: uhci bus_master
       configuration: driver=uhci_hcd latency=0
       resources: ioport:c800-c81f irq:20
       [... cut ...]
```

What the overall impact of all this means is still unclear to me.  After nine months of running Ubuntu (6x then 7.04), i'd yet to run into any question of what "bit width" this box is using until i had to choose between downloading the latest **pidgin** IM application, as either 64-bit or 32-bit, to replace **gaim**.  

The existence or not of the 64-bit library paths mentioned by bwhitacker also makes me suspect the impact of 64-bit operation is still very limited.

> **bwhitaker said:**
> The easiest way I've found to see if your linux install is 64bit  is checking to see if you have a /lib64, /usr/lib64, /usr/local/lib64  directory.

As i mentioned before, i only had **/usr/lib64** and it only contained to object-code library files (***.so***): ```
madm@vice-h0:~$ ls /usr/lib64/libfakeroot/
libfakeroot-sysv.so  libfakeroot-tcp.so
```

When i searched for "64-bit" or "64 bit" in **synaptic**, only a couple dozen packages were listed and only **lib64z1**, a 64-bit compression library seemed potentially newbie useful and safe to install/uninstall.  It required **libc6-amd64**.  When i installed both, voila, i had all three paths bwhitaker listed with a few dozen new *.so* files.  

Though i didn't try testing compression ("gzip and PKZIP" only, according to **lib64z1**), there was no noticeable difference in performance, including in **hardinfo** benchmark tests.  

So, because both **lib64z1** and **libc6-amd64** describe themselves as "Architecture: i386" and **libc6-amd64** says it's "meant for AMD64" (while my CPU is Intel), i simply removed both libraries (which seemed sensible, i hope... - not-a-hardware-guy):
```
madm@vice-h0:~$ dpkg -s lib64z1 libc6-amd64
Package: lib64z1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 136
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
**Architecture: i386**
Source: zlib
Version: 1:1.2.3-13ubuntu4
Replaces: amd64-libs (<< 1.4)
Depends: libc6-amd64 (>= 2.5-0ubuntu1), libc6-amd64
Description: compression library - 64 bit runtime
 zlib is a library implementing the deflate compression method found
 in gzip and PKZIP.  This package includes a 64 bit version of the
 shared library.
Original-Maintainer: Mark Brown <broonie@debian.org>

Package: libc6-amd64
Status: deinstall ok installed
Priority: standard
Section: libs
Installed-Size: 9496
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
**Architecture: i386**
Source: glibc
Version: 2.5-0ubuntu14
Depends: libc6 (= 2.5-0ubuntu14)
Conflicts: amd64-libs (<= 1.2)
Description: GNU C Library: 64bit Shared libraries for AMD64
 This package includes shared versions of the standard C library and the
 standard math library, as well as many others. This is the 64bit version
 of the library, **meant for AMD64 systems**.
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
```

---

### Post by RomeReactor on 2007-09-16
> **admarshall said:**
> But what is **uname -m** returning on your box?  It simply returns "i686" on this box.

I get:
```
romereactor@ubuntu:~$ uname -m
x86_64
```

I used to get i686 when I had Ubuntu 32 bit.

> Re the output from **lshw -C system**,  I'm now thinking this reflects the bit-level of the mainboard's bus.  Try **lshw -C bus** and i suspect you'll also see "width: 32" with each bus-entry output.  

I also get 32 bit width. Hmm...

> As i mentioned before, i only had **/usr/lib64** and it only contained to object-code library files (***.so***): ```
madm@vice-h0:~$ ls /usr/lib64/libfakeroot/
libfakeroot-sysv.so  libfakeroot-tcp.so
```

Running **ls /usr/lib64/libfakeroot** here returns nothing, but:
```
romereactor@ubuntu:~$ locate lib64
/usr/lib64
/lib64
```

---

