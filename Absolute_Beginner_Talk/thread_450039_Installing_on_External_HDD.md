---
title: "Installing on External HDD"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by ManiacV on 2007-05-20
Here is my setup:

Dell XPS M1710 laptop
LaCie 1TB HDD External connected by firewire 400

What I want to do:
Run Vista from my HDD inside my laptop and keep Ubuntu on a partition inside my external HDD. 

So far I have installed Ubuntu, but the GRUB gave me Error 17, so I reinstalled the MBR from my Vista disc. 

Does anyone know how to install Ubuntu to run from an external HDD? My BIOS can boot from a USB, so that shouldn't be a problem. I just need the GRUB to recognize where Ubuntu and Vista is on my HDD's. 

Thanks

P.S - How exactly should I run the installation with the / and /swap and what else do I need? I am so confused by those....

---

### Post by ManiacV on 2007-05-20
bumpity bump bump bump

---

### Post by confused57 on 2007-05-21
If you still have Ubuntu installed on your external drive, you can use the live cd to install grub to the external drive mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

from the link:
```
sudo grub
find /boot/grub/stage1
```
should return "root (hd1,x)", you would then:
```
root (hd1,x)
setup (hd1)
quit
```

Then reboot your pc to boot first to your external hard drive...you should get a grub menu at boot, if you do highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot....if this works it's temporary, but it can be made permanent in your /boot/grub/menu.lst.

---

