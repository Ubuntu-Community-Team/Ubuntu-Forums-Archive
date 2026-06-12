---
title: "PowerBook G4 - Sound Issues (Fiesty Fawn)"
date: 2007-05-02
forum: Apple PPC Users
---

### Post by GoLoGo on 2007-05-02
I recently just installed Ubuntu Dapper Drake PPC Edition (6.04) and had many errors on the PowerBook G4 Laptop. I then Updated, then Upgraded the system to 7.04 (Fiesty Fawn). Everything is working flawlessly, except for the sound. It tells me that either my sound card is not installed, or I do not have the correct GStreamer Plug-ins installed. I am still very new to Ubuntu. I tried messing with the sound settings under System,  but got nowhere. Any help is appreciated, Thank you.

---

### Post by stmiller on 2007-05-02
Is this a TiBook? There is a bug with the newer kernel and the alsa driver with this notebook. See this thread:

[http://ubuntuforums.org/showthread.php?t=412151&page=4](http://ubuntuforums.org/showthread.php?t=412151&page=4)

Basically, fetching and installing the last edgy powerpc kernel deb from packages.ubuntu.com will give you a kernel that works with sound, for now.

---

### Post by GoLoGo on 2007-05-02
How exactly would I do this? Installing the Edgy PowerPC Kernel from packages.ubuntu.com that is. Would I have to re-install everything? Since im using 7.04, im assuming some of the packages already installed... will be incompatible with the old kernel.

---

### Post by stmiller on 2007-05-03
Package versions are irrelevant to the kernel version.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=powerpc&file=pool%2Fmain%2Fl%2Flinux-source-2.6.17%2Flinux-image-2.6.17-11-powerpc_2.6.17.1-11.37_powerpc.deb&md5sum=3b51a60619de26b6dba8a4dcd7375f9c&arch=powerpc&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=powerpc&file=pool%2Fmain%2Fl%2Flinux-source-2.6.17%2Flinux-image-2.6.17-11-powerpc_2.6.17.1-11.37_powerpc.deb&md5sum=3b51a60619de26b6dba8a4dcd7375f9c&arch=powerpc&type=security)

Just download this deb, and double click on it to install. Then reboot and sound will work. You might have to first add

snd-powermac

to the file
/etc/modules

Click tab at the boot screen to make sure to select this kernel. (It will probably be set as default after install that deb, most likely.)

Otherwise, you'll have to compile your own kernel from kernel.org. See my post at the bottom of this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/)

---

### Post by GoLoGo on 2007-05-03
All I did was cd /etc/ sudo nano modules, added the line snd-powermac, restarted, the sound works, thanks for the exellent help stmiller, i really appreciate it. thank you.

---

### Post by anders_gud on 2007-05-03
> **GoLoGo said:**
> All I did was cd /etc/ sudo nano modules, added the line snd-powermac, restarted, the sound works, thanks for the exellent help stmiller, i really appreciate it. thank you.
Hi GoLoGo!
Can you please specify your Powerbook model:

```
cat /proc/cpuinfo
```

A lot of us PB users have sound problems, and we like to know which models are affected...
Cheers
Anders

---

### Post by GoLoGo on 2007-05-03
PowerBook G4 Information is as follows from /proc/cpuinfo :
> [B]
processor       : 0
cpu             : 7455, altivec supported
clock           : 533.000000MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 66.26
timebase        : 33280414
platform        : PowerMac
machine         : PowerBook6,1
motherboard     : PowerBook6,1 MacRISC3 Power Macintosh
detected as     : 287 (PowerBook G4 12")
pmac flags      : 0000001a
L2 cache        : 256K unified
pmac-generation : NewWorld
[/B]

---

### Post by anders_gud on 2007-05-03
Thanks!
Seems that [THE BUG]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652") is Titanium PB only... Yours is a 12" Aluminium, right?

---

### Post by GoLoGo on 2007-05-03
Yes, 12'' Aluminum. Hope it helps.

---

### Post by pulk on 2007-05-26
thx for that tip! I also just added the line to the /etc/modules and sound worked after restart. here is my info:

> processor       : 0
cpu             : 7455, altivec supported
clock           : 667.000000MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 66.56
timebase        : 33330403
platform        : PowerMac
machine         : PowerBook3,5
motherboard     : PowerBook3,5 MacRISC2 MacRISC Power Macintosh
detected as     : 80 (PowerBook Titanium IV)
pmac flags      : 0000001b
L2 cache        : 256K unified
pmac-generation : NewWorld


---

