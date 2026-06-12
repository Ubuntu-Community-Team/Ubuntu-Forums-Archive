---
title: "Problem with Server Ubuntu"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-22
I installed the Server copy of Ubuntu on a relatively old machine, and I am having a problem booting, according to setup, I installed it correctly, it asked me to remove the disc, I did, then I reset it. It started up, but when it was loading files, it stopped at "Boot" and restarted, anyone know what's up? Thanks

---

### Post by carlosfocker on 2007-03-23
A few question:

Was this computer working before you loaded Ubuntu server? You might want to run the Memtest that the grub menu has. When I had problems like this it was usually because of bad ram, and FSB was clocked to fast(Trying to overclock cpu :) ). 

How old is this system? Found a submitted bug where someone was having this problem. 
[https://answers.launchpad.net/ubuntu/+ticket/3506](https://answers.launchpad.net/ubuntu/+ticket/3506).

---

### Post by az on 2007-03-23
> **Peter1234123 said:**
> I installed the Server copy of Ubuntu on a relatively old machine, and I am having a problem booting, according to setup, I installed it correctly, it asked me to remove the disc, I did, then I reset it. It started up, but when it was loading files, it stopped at "Boot" and restarted, anyone know what's up? Thanks
That's exacly what happens when you try to run a kernel that was made for a 686 CPU on a 386 or 586 CPU.

Depending on the machine, you may have a CPU that is not quite a 686-type processor.  Examples of such CPUs are Pentium I and VIA C3.  The VIA C3 is a relatively modern processor but it lacks a few instructions needed to be fully a 686-class CPU.

Long story short, the server kernel is 686 and the desktop (generic) kernel is 386 or better.

The likely solution to your problem is to install the generic kernel on your system.  The server kernel is only useful if you want to squeeze all the performace you can out of a high-power server box.  The generic kernel will do everything you need it to do.

You can either reinstall using the alternate cd (the alternate cd can install a server system, but it installs the generic kernel).  You can also just reboot the installer cd (any one - they all boot the *generic* kernel), chroot into your installed server that won't boot and install the generic kernel from there:

sudo apt-get install linux-image-generic linux-server*-

(That will install the generic kernel and remove the server kernel)
and then reboot into your server.

---

### Post by Peter1234123 on 2007-03-23
Ahh, the computer has an  AMD K-6 650?Mhz 128mb ram, single chip, and yes, server 2003 and Windows 98 :P ran on it perfectly, should I try the generic Linux  kernel?

---

### Post by carlosfocker on 2007-03-23
i would vote yes

---

### Post by Peter1234123 on 2007-03-23
When I try to install from the disc, it now says "The EXT File System creation of Partition 1 of IDE Master failed"

---

### Post by az on 2007-03-23
> **Peter1234123 said:**
> When I try to install from the disc, it now says "The EXT File System creation of Partition 1 of IDE Master failed"

What cd are you using?

---

