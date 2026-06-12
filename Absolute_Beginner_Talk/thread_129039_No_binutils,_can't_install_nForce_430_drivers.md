---
title: "No binutils, can't install nForce 430 drivers"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by fbg111 on 2006-02-12
Hi all, I've got the following system:

Asus A8N-VM-CSM (nForce 430 + Geforce 6150 integrated gpu + integrated Marvel ethernet)
Athlon 64 3200
1GB RAM
2x SATA hdd

I run the Breezy x64 installer with no problems as long as I specify 'noapic nolapic', however X can't start with my integrated graphics.  The integrated 6150 is not listed among the supported gpu's in X's troubleshooting output.  So I log in at the command line, mount /dev/cdrom, and attempt to install the Nvidia x64 driver ([http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html]("http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html")) from the cd (sudo sh NFORCE-Linux-x86_64-1.0-0310-pkg1.run).  Installation starts, but shortly afterwards an error occurs that says, roughly, 'either binutils are not installed, or ld is not in the path.  Install binutils or add ld to your path.'  I tried grepping through the lib and other directories, but can't seem to find binutils.  Does it come with Breezy?  If so, where is it, and if not, how can I get it without apt-get (Breezy also doesn't recognize the integrated Marvel ethernet controller, which I hope will change after installing the driver)?  Thanks!

---

### Post by CookieOrc on 2006-02-12
These two post can help try Automatix which will install most nVidia drivers for you 
[http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)

or try this one to do it manually 

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+6200](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+6200)

---

### Post by Jason_25 on 2006-02-12
[QUOTE=CookieOrc]These two post can help try Automatix which will install most nVidia drivers for you 
[http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)[/QUOTE]

Automatix doesn't install nvidia nforce drivers.  It also doesn't work on AMD64 kernels.


Do you have nvidia ethernet?  That should work out of the box.  Marvell isn't supported.

---

### Post by fbg111 on 2006-02-12
Thanks, however Breezy fails to connect to my router, so I have no network connectivity and therefore no apt-get.  I assume that's b/c the Nforce driver is required for Linux to use it.  Not sure where to go from here...

---

### Post by fbg111 on 2006-02-12
Not sure what you mean by nvidia ethernet, the integrated ethernet controller on this board is Marvell (Gigabit Ethernet by Marvell 88E1111 PHY), but the MCP is obviously nVidia.

---

### Post by geek.de.nz on 2006-08-24
I just recently got a new computer (AM2 Asus Motherboard with NVIDIA Chipset, NVIDIA LAN etc).

I cannot get the driver installed which is on the Asus CD. It first complained that the binutils package is not installed. Then I checked and there is a package installed called binutils-static. I thought that would do until I get at least my LAN card working, but it didn't. Then I made a symbolic link (/bin/ld) to /bin/ld_static but that gave me a different error:

```

ERROR: Unable to find the system utility 'objcopy'; please make sure you have the package 'binutils' installed. If you do have binutils installed, then please check that 'objcopy' is in your PATH.

          OK

```

However, I cannot find the file 'objcopy' or even a similarly called one anywhere (# updatedb; locate objcopy).

I would really like to run the 64 bit version on this machine. I will still install the 32 bit version for now, but since Windows Vista is coming out as 64 bit version soon, Linux needs some better support for 64 bit architechtures. :-)

---

### Post by najames on 2006-08-24
Try downloading the current version of the Nforce drivers and give it a shot before you abandon for 32bit.  The disk version might be old.  You won't need 6GB RAM to use Ubuntu like you will with Micro$oft Vista.  :mrgreen: 

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by geek.de.nz on 2006-08-26
Well, to be honest, I wasn't intending to install Vista for serious use because I'm so used to Linux now. I just said it, so that someone would answer my post ;-).

Unfortunately, on the NVIDIA website, there are only packages for the following Linux distros:

 Supported Distributions: 
  [LIST]
[*]SLES 9 SP3 (2.6.5-7.244)
[*]SLES 9 SP2 (2.6.5-7.191)
[*]SLES 9 SP1 (2.6.5-7.139)
[*]RHEL4 UP1 (2.6.9-11)
[*]Fedora Core 4 (2.6.11-1)
[*]RHEL 3 UP4 (2.4.21-27)
[*]RHEL3 UP5 (2.4.21-32)
[*]RHEL3 UP7 (2.4.21-40)
[*]RHEL 4 UP3 (2.6.9-34)
[*]Fedora Core 5 (2.6.15-1)
[*]RHEL 4 UP2 (2.6.9-22)
[*]RHEL 3 UP6 (2.4.21-37)
[*]SuSE 10 (2.6.13-15)[/LIST]   
and most of them are RPM packages which makes the problem worse for me. I think I might give Edgy a try and see if that works better. Downloading that now.

My new! Motherboard is a 
Asus M2NPV-MX
Northbridge: NVIDIA GeForce 6150 GPU
Southbridge: NVIDIA nForce 430 MCP

As far as I know, that is quite new Hardware, so I might have to install a bleeding edge distro like edgy. i will give that a shot, but might not succeed.

So far, I've tried to install the drivers manually, which gave me the error:
package binutils missing!

I checked and a (static) package of binutils (binutils-static) was installed. The installer (NFORCE-Linux-x86_64-1[1].0-0311-pkg1.run) from the Asus install CD (woohoo, they actually ship with Linux drivers now) gave me another error:
tool ld not found.

I checked and searched for the ld tool. There was a file called /bin/ld_static, and I thought: "bingo!", made a symbolic link to it (#ln -s /bin/ld_static /bin/ld) and restarted the install. This time I got a slightly different error:
ERROR: Unable to find the system utility 'objcopy'; 
please make sure you have the package 'binutils' installed. 
If you do have binutils installed, 
then please check that 'objcopy' is in your PATH.

          OK

By the way, the LAN card is actually installed in the sense that I can see a device eth0 if I do '#ifconfig' and stuff like that, but it just doesn't work. Now I have to always work from CD on that machine and that's definitely not an option. Bugger, I knew this would happen. Linux is always bad with new hardware.

---

