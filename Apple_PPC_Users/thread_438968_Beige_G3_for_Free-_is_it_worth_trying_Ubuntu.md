---
title: "Beige G3 for Free- is it worth trying Ubuntu?"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-10
My mother-in-law has a beige G3 that's going out in the trash if I don't rescue it. I have enjoyed my early experiences with Ubuntu on my PC's, and was thinking that it would be fun to try to get Ubuntu running on the old G3, then possibly donating it to someone in need or a charity that handles stuff like that. But I might just leave it in the trash if the process is going to be really tedious!

I haven't done any research on what the G3's specs are, but reading here on the forums I see that it's not that easy to just pop the Live CD in and install Ubuntu. Now, I don't want anything but Ubuntu on the G3- no Mac OS at all. Is that even possible? 

I know I need BootX or miboot or something to get the G3 to boot from CD or to install, but I'm unclear on exactly what to do with these files. I have another Mac, a G4 emac, that could prove useful in providing the files I need, though it has no floppy drive.

Could someone coach me on what to do? I envision making a floppy with BootX or miboot, getting the machine started, then installing Ubuntu. Sort of like installing Win98 with a boot disk. Am I far off?

Thanks for any assistance. 

JC

---

### Post by stmiller on 2007-05-10
It's possible. You'd need a Mac OS 9 disc, is the only catch. This is required on these old-world macs to set up the partitions correctly. Ubuntu should run great on this machine, granted you get the old-world install pulled off. :)

There's an old-world ubuntu how-to wiki somewhere. Let me find the link and I'll add it to the PPCFAQs (link below).

EDIT: Found the link
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by joshjani on 2007-05-11
Well, I got the beige mac, and have attempted to fire it up. When I turn it on, I get nothing but a white screen. I hear the HD spinning, but can't seem to boot to anything. I have an OS9 CD and another system CD (I can't remember exactly what it is- but it's original) Both of these CD's have printed instructions to hold down C while powering up to boot from the CD, but this does not work. 

Doing a small amount of research, I found that holding cmd-opt-o-f gets me to the OpenFirmware screen, where I can indeed input some instructions. I tried reset-nvram, which did nothing (said command not known or something similar) then reset-all, which booted back to the white screen only and did nothing else.

I suspect that the HD in the machine is fouled up, and so it won't boot. If I can get it to look at the CD, which will have a bootable section, maybe I can get somewhere. I tried following the directions in the link above, but that seems to require that you get your OS9 disk working. I'll take that route, but I can't get the CD to boot right now.

It might be a little far afield to ask for Mac help here in the Ubuntu forums, but ultimately I want to put Ubuntu on it, so I'm asking! Can I enter some commands at the OF prompt to get the Ubuntu PPC or OS9 CD to go? 

Thanks

JC

---

### Post by joshjani on 2007-05-16
OK, I followed the instructions from that link [https://help.ubuntu.com/community/In...n/OldWorldMacs]("https://help.ubuntu.com/community/In...n/OldWorldMacs")

And a few things went awry. Firstly, the instructions say that vmlinux and initrd.gz are going to be in the install folder on the PPC Ubuntu CD. They were not, they were in the casper folder. No Big. It also says that by dropping BootX into the system folder, it will configure itself to appear in the apple menu and run at every boot. It does neither. I PUT my BootX App in the apple menu, and I made an alias, so I can quickly run it when I boot to OS9.

But when I place the Ubuntu CD in and select Linux in BootX, I am unable to install. I get a message on screen during the install process something like this: 

check root+ bootarg cat /proc??cmdline 
or missing modules, devices: ??at /proc/modules ls /dev
ALERT! does not exist, dropping to a shell
/bin/sh: can't access tty; job control turned off

BusyBox v1.1.3 (Debian 1.1.3-3ubuntu??3) Built-in shell (ash)
Enter "help" for a list of commands
(initramfs)

(the ?? indicate a jittering gobbledegook character or two that I can't read)

So what's up! I swear I followed the instructions explicitly, and I only got this far. I have tried both the Edubuntu and Ubuntu 7.04 PPC ISO's, same result.

I would love to get this to work. Please help if you can. Thanks
JC

---

