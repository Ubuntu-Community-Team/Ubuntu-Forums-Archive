---
title: "windows 7 dual boot mbr messed up?"
date: 2016-12-02
forum: Arch and derivatives
---

### Post by kubensis on 2016-12-02
So honestly i was trying to use arch linux, the reason is because my ethernet drivers or what ever is incompatible with everything but antergos. Their community is not useful, since their main forum requires me to have a successful install.

What i did:
Made 3 partitions 8gb swap, 400mb boot/efi, and a 60gb root by reducing my 1tb. I had enough space.

I assigned everything, i didn't touch grub because im a noob (i don't know if thats what is responsible) and pressed the install button. I got an instant error which told me to restart. I did, my usb got confused like always so it didnt start so my computer tried to boot from my hdd, thats when i realized i messed up.

I get the error of like no bootable media found or something similar. 


I am on my laptop now, i put boot-repair-disk on my flash drive and tried to use that, but i don't get the repair option. I also don't have internet on it, so i can't give you the text document.

It says at the beginning no boot loader is installed in the mbr of dev/sda

syslinux  mbr version 4 is installed in the mbr of dev/sdb (i tried to do something but had no clue how to do anything with syslinux)


boot sector type: unknown

mount system failed unknown mount system type 

this totally sucks idk what to do and my computer has garbage internet issues constantly..... the stuff on my computer is important.

---

### Post by wildmanne39 on 2016-12-02
*Thread moved to **Arch and derivatives**.*

---

### Post by oldfred on 2016-12-02
Do not know Arch, and do not know for sure that Boot-Repair works. But it primarily uses standard Linux commands.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kubensis on 2016-12-02
I wont have internet on anything my computer sucks and is incompatible with literally everything. it seems like everything i do is futile lol. and there is no recommended repair button. I dont have any linux distro now though becuase antergos failed. I replaced it with boot repair on my usb flash drive

---

### Post by oldfred on 2016-12-03
What brand/model system?
What wired Ethernet chip?
Some wireless does not work with live installer and you have to use wired connection to get correct wireless driver.

---

### Post by kubensis on 2016-12-03
Fx6300 cpu
 

970a ud3p motherboard

[http://imgur.com/ZNlWz3N](http://imgur.com/ZNlWz3N)

(old pic, i dont have the live boot of linux anymore)

i dont have a way to use wifi on that computer. only wired.

---

### Post by oldfred on 2016-12-03
Do not know AMD well but many with AMD need IOMMU settings both in UEFI & boot settings.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

