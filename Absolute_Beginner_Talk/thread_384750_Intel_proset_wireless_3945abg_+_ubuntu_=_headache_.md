---
title: "Intel proset wireless 3945abg + ubuntu = headache for a noob"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by mlapaglia on 2007-03-14
ok here's what i have:

intel proset wireless 3945abg
ubuntu, kernel 2.6.17-11-generic

ubuntu sees the card, but does not have the appropriate drivers installed.
intel supports linux, and has drivers that work with linux, but you can to "compile" them yourself, and im having some trouble doing it on my own. im wondering if anyone else has had the same problem as me, or no hows to fix it lol.

i get all kinds of errors when i try to follow the instructions that intel has incorporated with their release, and there dosen't seem to be anything on the web either.

any help is appreciated, i can get you any information you want, but i dont know what to list for you. thanks

---

### Post by andreas64 on 2007-03-15
Hi,

just install linux-restricted-modules-generic via Synaptic, boot your machine and everything should work....

Andreas

---

### Post by mlapaglia on 2007-03-15
when im looking at the synaptic window, after searching for "linux restricted", all of the restricted options are already selected. any ideas?

---

### Post by Bachstelze on 2007-03-15
According to [http://packages.ubuntu.com](http://packages.ubuntu.com) the ipw3945 driver is available only for the 2.6.17-10 kernel. You can either install it or build the driver from source, which is quite easy too.

---

### Post by mlapaglia on 2007-03-15
can you point me in a general direction on figuring out how to compile a kernel? thanks a lot :)

---

### Post by SendDerek on 2007-03-15
I have the same wireless card, and although I'm not sure which kernla I'm running, I'm running Edgy Eft and I was able to get the wireless to work by using Network-Manager from the repositories.  

I don't know if it will work for you as well, but it's easy and worth a shot!

---

### Post by Bachstelze on 2007-03-15
mlapaglia > you won't need to compile anything if you decide to use a 2.6.17-10 kernel as it is available from apt. Just do

```
sudo apt-get install linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic
```

Then reboot your system and choose the 2.6.17-10 kernel from the GRUB menu.

---

### Post by mlapaglia on 2007-03-15
ya, the network-manager couldn't see my card, when i installed the gui addon to the program (i think), it said there were no wireless adapters.

i guess im going to have to recompile my kernel?


i've tried messing around with the drivers from intel's site, but i kept getting errors saying i didn't have the right kernel or something.

---

### Post by mlapaglia on 2007-03-15
thanks hymmtolife, i'm doing a fresh install of ubuntu and then i'll try that, be back in a bit.

---

### Post by mlapaglia on 2007-03-15
```
mlapaglia@mlapaglia-laptop:~$ sudo apt-get install linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  linux-doc-2.6.17 linux-source-2.6.17 nvidia-glx nvidia-glx-legacy avm-fritz-firmware-2.6.17-10
The following packages will be upgraded:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic
2 upgraded, 0 newly installed, 0 to remove and 134 not upgraded.
Need to get 30.7MB of archives.
After unpacking 844kB of additional disk space will be used.
Get:1 http://security.ubuntu.com edgy-security/main linux-image-2.6.17-10-generic 2.6.17.1-10.34 [23.0MB]
Get:2 http://security.ubuntu.com edgy-security/restricted linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1 [7682kB]                                             
Fetched 30.7MB in 1m34s (326kB/s)                                                                                                                                       
Preconfiguring packages ...
(Reading database ... 88191 files and directories currently installed.)
Preparing to replace linux-image-2.6.17-10-generic 2.6.17-10.33 (using .../linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb) ...
The directory /lib/modules/2.6.17-10-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.17-10-generic ...
Running postrm hook /sbin/update-grub .
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

E: Sub-process /usr/bin/dpkg received a segmentation fault.
mlapaglia@mlapaglia-laptop:~$ 
```

not quite sure what a segmentation fault is.. did it install correctly or should i try something else? im afraid to restart lol.

---

### Post by mlapaglia on 2007-03-15
ok, restarted, ran all the updates, installed network-manager, and the graphical interface for it, everything is working now.

thank you very much for your help! i appreciate all the hard work you guys do for the linux n00bs :) :popcorn: :guitar:

---

