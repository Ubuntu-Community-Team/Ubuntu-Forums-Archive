---
title: "Dual boot with 3 physical HDs"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by baytuni on 2006-04-12
Hello. I had ubuntu installed on my computer for 5 months and it is pretty satisfying. But I couldn't completely figure out the "grub concept" how it sees the physical drives and partitions. I had two hd's, one was sata and the other one was ide. I had an ext3 partition on sata and the grub on its boot sector. I easily managed to dual boot the 3 operating systems one of them being linux and the rest were windowses on two distinct physical drives. Here is my old menu.lst
```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

title Windows
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Windows
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1
```

According to this menu my sata drive is (hd0) and my ide is (hd1).Now my question is. I bought a third drive (sata) and i moved the windows on my ide drive to th new one. Also i moved the linux partition from my sata1 to my old ide.  I didn't have to change the commands for windowses they're both fine. But I couldn't manage to reach my linux partition.(ide). 
  I think i wrote pretty confusing.:-k

---

### Post by Herman on 2006-04-12
Try reading [this thread ]("http://ubuntuforums.org/showthread.php?t=158956&highlight=grub+command+line")and especially slug's posts there where slug did an excellent job of explaining how to use GRUB's Command Line  to get GRUB itself to look around for the partition and or disk that you want to boot.
This [web-page]("http://www.users.bigpond.net.au/hermanzone/p15.htm") has an illustration or two that might help a little too.
Regards, Herman :D

---

### Post by baytuni on 2006-04-13
Here comes another question. Last time i had copied my linux partition to  another drive. But I think i couldn't copied the boot sector. I used gag 4.6 but
it said no boot sector. What can i do to bring back my ubuntu.

---

### Post by Herman on 2006-04-13
You could try [installing Lilo]("http://ubuntuforums.org/showthread.php?t=96920")  to your Ubuntu partition or [reinstalling Grub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29"). 
To boot with GAG, pick one of the methods that will install GRUB to your Ubuntu partition, rather than to MBR.
Good luck (Herman)

---

