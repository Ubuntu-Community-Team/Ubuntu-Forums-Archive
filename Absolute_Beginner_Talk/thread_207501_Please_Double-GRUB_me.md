---
title: "Please Double-GRUB me"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by molly_001 on 2006-07-02
[SIZE=2]Hi, everyone! I am new to Linux and Ubuntu, and thanks to everyone for the helpful guides!![/SIZE]

[SIZE=2]I have tried to do my homework on the situation below, and now I need to edit the GRUB menu.lst file -- but I need some help![/SIZE]
 
Here is what I have accomplished so far:
 
**GOAL: Dual-boot menu option for Vista and Ubuntu. Menu should pause for me to select OS.**
 
1. First, I installed Vista Beta 2 (fresh complete install from DVD). I installed Vista onto the second of two partitions I had made on a new hard drive. (No XP ever on this drive before.)
2. I used the Ubuntu Desktop CD to install Ubuntu 6.06 onto the first partition.
It is my understanding that this allowed GRUB to install in the MBR.
 
 
Now, when I use Ubuntu --> System --> Admin --> Disk, this is what I see there:
a> Part 1 /dev/sda1 file system: unknown path: none 78 GB (no free available)
b> Part 3 /dev/sda3 file system: Ext3 path: / 2.1 GB (44 MiB free)
c> Swap /dev/sda5 file system: Mem Swap 125 MiB
d> Part 2 /dev/sda2 file system: NTFS path:/tmp/disks-conf-sda2 69 GB (59 GB free)
 
As you can see above, Vista is installed into Partition 2.
 
When I look in my GRUB menu.lst file, I can see all of the Ubuntu kernels as root hd(0,2)
 
During my research, it appears I now need to add code to menu.lst similar to this:
 
title Windows Vista Beta 2
root (hd0,0)
savedefault
makeactive
chainloader +1
 
title Ubuntu 
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot
 
... However, I fear that the code above will not give me a menu option. Am I correct?

---

### Post by confused57 on 2006-07-02
I assume you're not able to boot into Vista, but can boot Ubuntu OK?

If that is the case, when your system is booting up, press "Esc" when grub is loading(for now, you can change your menu.lst to extend the time later).
After your grub menu is displayed, press arrow "down" to highlight the Windows entry, then press "e" to edit the boot options.  Try changing the root to something like  root    (hd0,1), & try booting Vista with this option...this is not permanent, but this will let you know if it enables booting Vista.  If it works you can then go into your /boot/grub/menu.lst and change it permanently there.
In your menu.lst you can also change if you want your grub menu displayed at bootup, how long you want it displayed, and which OS to boot by default.

That's what I'd try if I understand correctly what you're trying to accomplish.
Maybe someone else will recommend a better option...

---

### Post by molly_001 on 2006-07-02
Thank you, confused57.  
I followed your pointer along with what I had gathered from various tutorials, and I can now dual-boot my machine to either Ubuntu Dapper or Vista Beta 2.

---

### Post by confused57 on 2006-07-02
Great, I'm glad everything worked out.  You're definitely going about it the right way,  reading and learning from tutorials...then asking questions.
Enjoy your dualbooting system.

---

