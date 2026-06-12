---
title: "Live cd trouble"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by merike on 2007-04-30
I've tried two different cds and two live cds from different sources and it hasn't made any difference. After loading Ubuntu I'm not able to see hard disk partitions with gparted, it just hangs at scanning. I'm also not able to install, it hangs right after choosing language. Before the problems appeared I was organising my partitions with gparted and after a new boot I got all those problems. Did something go wrong with partitioning? It sure seemed ok, all changes seemed to be applied with no problems, although it did hang couple of times after it finished applying changes.
I'd really like to keep my existing windows installation, but my boot loader got messed up and I can't load it. I was to delete all Ubuntu partitions and install Edgy again (had feisty but it didn't work as expected for me), because I thought it would create grub again and therefore I could access windows again as well as to have working Ubuntu installation.
Cd and memory check both return no errors.

---

### Post by Najand on 2007-04-30
> **merike said:**
> I've tried two different cds and two live cds from different sources and it hasn't made any difference. After loading Ubuntu I'm not able to see hard disk partitions with gparted, it just hangs at scanning. I'm also not able to install, it hangs right after choosing language. Before the problems appeared I was organising my partitions with gparted and after a new boot I got all those problems. Did something go wrong with partitioning? It sure seemed ok, all changes seemed to be applied with no problems, although it did hang couple of times after it finished applying changes.
I'd really like to keep my existing windows installation, but my boot loader got messed up and I can't load it. I was to delete all Ubuntu partitions and install Edgy again (had feisty but it didn't work as expected for me), because I thought it would create grub again and therefore I could access windows again as well as to have working Ubuntu installation.
Cd and memory check both return no errors.

Ok, open a terminal or just push Ctrl+Alt+F1 and run ```

sudo fdisk -l

```
see if you can see the existing partitions or not? If you can see them there, there would be a chance to retrive both your windows and your ubuntu partitions.

---

### Post by merike on 2007-04-30
Now I'm confused. What I last had in gparted was:
hda1 - NTFS
hda2 - FAT32
hda3 - FAT32
hda4 - extended
hda5 - FAT32 in extended

What I get now:
hda1 - NTFS
hda2 - Linux
hda3 - FAT32
hda4 - extended
hda5 - FAT32

What I had in gparted is how I planned it. hda5 was all free and I expected Ubuntu automatically resize it and install there. Oh and I'm not interested in getting back Ubuntu's former partitions, there wouldn't be correct info anyway since my partition table was different when it was installed. The only partition at the same place is hda1. It is also marked as boot partition in fdisk.

---

### Post by Najand on 2007-04-30
So, can you install ubuntu now? or you still have problem with the installer?

---

### Post by merike on 2007-04-30
I don't think I can, because from last try nothing in partitioning has changed. If fdisk showed those partitions now it would have shown the before the same way. I anything has changed then the installer has got even slower than last time. After launching and waiting for several minutes I still have nothing but title bar and white window.

---

### Post by Najand on 2007-04-30
Well... probably the easiest solution might be giving the alternative CD a try. You can find it at:
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by merike on 2007-04-30
I saw the alternate option when downloading Edgy's iso, but it says there text-based which sort of scares me. Anyone to describe it?

---

### Post by Najand on 2007-04-30
It is text-base but, if you follow the guidence there is nothing to be scared of... If you doubt something ask us here.

---

### Post by merike on 2007-04-30
I'm afraid it picked up the remains of previous installation, because when it created boot loader it said it already found Windows and Ubuntu from my hard drive (Although I had deleted Ubuntu's partitions before..). As far as I could understand it tried to create boot loader with Windows and 2! Ubuntus. Of course after booting it turned out that the boot loader is invalid.
Would deleting all partitions except hda1 and recreating others make it better? I'd need to be able to run gparted for that and I have no idea how to make it work..

---

### Post by merike on 2007-04-30
Hm, after alternate install I was able to use gparted on live cd again. So I did. Of course in the end of applying changes it hung, again. I assumed it had still applied them and booted with alternate cd. I was able to install again and this time it only found one OS prior to Ubuntu I was installing. I was already keeping fingers crossed when it finished installing, but when I booted I still got "hard disk boot sector invalid". So, I think I have two operating systems installed yet I can't boot into neither of them.

Any more solutions?

I need to be able to use windows on Wednesday so I'm afraid I have to give up my current Windows installation and format whole hard disk if I can't find solution soon :(.

---

### Post by merike on 2007-04-30
I might have found a solution from here: [http://simos.info/blog/archives/593](http://simos.info/blog/archives/593).
It seems that Ubuntu got installed in extended partition not in primary one and since BIOS looks for primary partition with boot flag then it gives error. I am able to boot using boot from first hard disk in live cd's menu. If I can now get gparted to play nice again then I just have to move Ubuntu to primary partition or assign boot flag to some primary partition to make it work.
I didn't plan triple-posting, though :O

---

