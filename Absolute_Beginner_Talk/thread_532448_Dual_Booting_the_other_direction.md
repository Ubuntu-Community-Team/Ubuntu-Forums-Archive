---
title: "Dual Booting the other direction"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by redmonster13 on 2007-08-22
I have ubuntu install and need to reinstall windows.

I would like to install it on the second partition of my second hard drive but I dont know how to get it to boot properly on startup.

I dont want to just throw it on and hope for the best becuase that is how I installed ubuntu and the reason I need to reinstall windows :)

---

### Post by lightstream on 2007-08-22
Booting can be a problem area. Why exactly do you need to reinstall? Was your system working before and then started having problems?

If your problems are solely down to booting, ie you have linux and windows installed but cannot choose which to boot try the Grub Super Disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/).

The way I installed was Ubuntu first, then Windows (which is not the right order to do it! I didn't know that then). Trying to sort out grub to let me dual boot failed, in fact I managed to make Windows commit suicide (it managed to mess up its own partitions). So I reinstalled XP, and am currently using the boot disk when I want to boot to linux. 

When I have the time, I'll read up about booting grub from the linux partition - I think this will be best for me.

---

### Post by Jimmyfj on 2007-08-22
The best way, in my opinion, is to install Windows first, then defrag your Windows partition and then install Ubuntu and let GRUB be your boot manager. GRUB is superior to the Win-loader.

---

### Post by Arthur Archnix on 2007-08-22
The good news is that it will boot just fine. Windows that is. Once it does, and you have it up and running, come back here and search the forums for "reinstalling grub". It will tell you how to use your live cd to restore grub and regain dual-boot nirvana.

The reason everyone says windows first is because Windows bootloader can't, ahem - won't,  dual boot, while  Linux bootloaders  can. But it's orders of magnitude easier to install windows and fix Grub than to remove Ubuntu, install windows, then reinstall Ubuntu.

---

### Post by redmonster13 on 2007-08-22
well the reason I have to reinstall is that I screwed up the partition and so I just wiped out windows and I am starting over.

I have windows back on hdd2 on the second partition and my bios set to boot from that hdd, now I just have to figure out how to move grub to that drive and make it boot linux which is on hdd1.

---

### Post by mrfelker on 2007-08-22
What version of Windows are you using?  Many older versions will only install on the first partition of the hdd1.  In either case installing Ubuntu after Windows will install GRUB and create a multiboot boot menu

---

### Post by redmonster13 on 2007-08-23
well for now I can boot into either os by changing my boot priority.

I am using xp, but I would like to move the grub loader to the MBR of the second hdd so I dont have to dig into bios when I want to switch over to play eve-online.

---

