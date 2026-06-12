---
title: "&quot;Failed to start the X server&quot;"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Tempshed on 2006-04-25
I've tried to run three versions of the live CD on my PC.
ubuntu-5.10-live-i386.iso
ubuntu-5.10-live-amd64.iso
dapper-live-amd64.iso
Each time I verified the data integrity with MD5SUM and verified the burn with Nero. But each time I tried to run the live version of Ubuntu I got the same error message - "Failed to start the X server".
I'm using a PC with an AMD Athlon64 3200+ cpu, an ATI Radeon X1300 PCIexpress graphics card and a Gigabyte GA-K8NF9 Ultra mobo with 1GB of Corsair memory.
As a total newcomer to Linux I'm understandibly not greatly impressed by this much lauded version of the O/S failing to run on mainstream quality equipment.
I did manage to get the Suse Linux 9.3 live DVD running on my machine but the graphics display was blurry to the extent of being illegible.
I would appreciate some helpful feedback from this forum regarding my not very happy first experience of Linux.

---

### Post by xXx 0wn3d xXx on 2006-04-25
[QUOTE=Tempshed]I've tried to run three versions of the live CD on my PC.
ubuntu-5.10-live-i386.iso
ubuntu-5.10-live-amd64.iso
dapper-live-amd64.iso
Each time I verified the data integrity with MD5SUM and verified the burn with Nero. But each time I tried to run the live version of Ubuntu I got the same error message - "Failed to start the X server".
I'm using a PC with an AMD Athlon64 3200+ cpu, an ATI Radeon X1300 PCIexpress graphics card and a Gigabyte GA-K8NF9 Ultra mobo with 1GB of Corsair memory.
As a total newcomer to Linux I'm understandibly not greatly impressed by this much lauded version of the O/S failing to run on mainstream quality equipment.
I did manage to get the Suse Linux 9.3 live DVD running on my machine but the graphics display was blurry to the extent of being illegible.
I would appreciate some helpful feedback from this forum regarding my not very happy first experience of Linux.[/QUOTE]

I also have this problem with breezy installs and live cds. Try editing xorg by typing the following in terminal. I'm not sure if you need to use sudo on a live cd. Get through the "Can't start X messages and then login so that you are at a terminal prompt.
> sudo nano /etc/X11/xorg.conf
then look for a line that looks like:

> driver: "ati"

and switch it to:

> driver: "vesa"

Then restart gdm:

> sudo /etc/init.d/gdm restart

and then if you need to:

> startx

You may notice that the vesa drivers are slow, laggy, and ugly but you should have a usable desktop and then you can install the offical ati drivers and change your screen resolution.

---

### Post by localzuk on 2006-04-25
This is due to the ATI drivers not supporting the latest and greatest in ATI cards. As MasterCheif says, changing to vesa should do the trick but if you do an install, you can install the official ATI binaries and they should work much better.

---

### Post by deadlychicken22 on 2006-04-25
Will this also work for me?I did a full install of ubuntu 5.10 and have an nvidia geforce 6100 (of course, i would have to search for something like driver: "nv" instead of "ati"). I just built a new computer and installed ubuntu (my new favorite OS) on it and all I can get is a command line because every time I startup it gives me errors about not detecting a graphics device.

Thanks,
-ben

---

### Post by Tempshed on 2006-04-25
Thanks for the prompt response but you'll have to explain how I edit xorg. Is that something I can gain access to using the live CD? You'll have to excuse my ignorance, I'm extremely new to Linux and know zilch.

---

### Post by xXx 0wn3d xXx on 2006-04-25
[QUOTE=Tempshed]Thanks for the prompt response but you'll have to explain how I edit xorg. Is that something I can gain access to using the live CD? You'll have to excuse my ignorance, I'm extremely new to Linux and know zilch.[/QUOTE]
After all the "Failed to start X" messages you will be able to login and edit the xorg file. You can edit it on the live cd because it is held in the ram.

---

### Post by confused57 on 2006-04-25
Tempshed,
  If you can somehow get to a command line, as MasterChief mentioned, type in: sudo nano etc/X11/xorg.conf(lower & uppercase matter in Linux), then hit "Enter" , this should open up the xorg.conf.  Nano is the text editor that the xorg.conf file opens up into, just make the necessary driver changes & save.  Then follow the directions by MasterChief.

Here's a link to some keyboard shortcuts and commands:

[http://www.techenclave.com/forums/linux-shortcuts-and-commands-65415.html](http://www.techenclave.com/forums/linux-shortcuts-and-commands-65415.html)

---

### Post by localzuk on 2006-04-26
Yes it will. Then take a look at [http://ubuntuforums.org/showthread.php?t=139264&highlight=latest+nvidia](http://ubuntuforums.org/showthread.php?t=139264&highlight=latest+nvidia) for info on using the nvidia drivers.

---

