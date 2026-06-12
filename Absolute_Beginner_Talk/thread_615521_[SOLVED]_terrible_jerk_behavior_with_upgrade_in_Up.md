---
title: "[SOLVED] terrible jerk behavior with upgrade in Update Manager"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by larry wales on 2007-11-17
Hi, 

I recently tried to update feisty to gutsy through the Update Manager.  After this fails (see [<this post>]("http://ubuntuforums.org/showthread.php?p=3787613#post3787613")), the next time I start my computer, I notice that my Windows XP option has been deleted from the list.

How can I get entry back?  If I can't recover the entry, what other solutions are there?  (i.e. what would a default entry to start Windows XP look like?, how could I access Windows XP w/o going through Grub?).

thanks in advance for any advice!

larry

---

### Post by Arthur Archnix on 2007-11-17
Post the output of this:
```
sudo cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by larry wales on 2007-11-17
Hi, 

thanks so much for responding!  My grub list contains the following:
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

```

And when I run   ```
sudo fdisk -l
```  I get the following output:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        7235    19045057+  83  Linux
/dev/sda3            7236        7296      489982+  82  Linux swap / Solaris
```

As of yesterday, Windows XP was the default boot option.

thank you,
larry

---

### Post by Arthur Archnix on 2007-11-17
Ok, well that's not all of your grub output, so I can' t be sure I'm not missing something, but it looks from that like you're missing your entry for windows. Try adding this to grub:
> title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

To edit that file, do
```
gksudo gedit /boot/grub/menu.lst
```

Put it underneath the last Linux entry or before the first one. Depending on the rest of your file, this may affect your default booting OS.

---

### Post by larry wales on 2007-11-17
thanks man!  

Adding 

```
title Windows
root (hd0,0)
savedefault
makeactive
chainloader +1 
```

fixed the matter right!  :grin:

---

### Post by Arthur Archnix on 2007-11-17
Great, glad to hear. Please mark the thread solved to help future users with a similar problem. You can use the thread tools to do this.

---

