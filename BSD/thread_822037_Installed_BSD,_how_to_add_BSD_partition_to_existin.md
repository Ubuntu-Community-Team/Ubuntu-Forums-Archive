---
title: "Installed BSD, how to add BSD partition to existing grub?"
date: 2008-06-07
forum: BSD
---

### Post by disappearedng on 2008-06-07
Hi everyone.
I installed Ubuntu like half a year ago and recently I have decided to give BSD a try. I formatted my windows partition and successfully installed BSD on that partition. When prompted to use BSD's boot manager, I picked no because I like the way grub functions.

So here's the tricky question:
How do I add my BSD partition as a boot option into my grub menu?
I am in my Ubuntu right now, and I don't know how the system will automatically be able to detect 

This is my grub menu file: "

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5a780324-ac66-4eb0-a75d-54f433b9c677 ro acpi_sleep=s3_bios
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5a780324-ac66-4eb0-a75d-54f433b9c677 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a780324-ac66-4eb0-a75d-54f433b9c677 ro acpi_sleep=s3_bios
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a780324-ac66-4eb0-a75d-54f433b9c677 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
"

Now windows vista no longer exists. How do I add my BSD partition onto it?
What are the commands?

---

### Post by scottro on 2008-06-07
This should work (untested for years though, as these days I use GAG if multibooting).

title FreeBSD
root (hd0,0)
chainloader +1

In other words, it should still work, you're just chaging the title (and the makeactive is probably unnecessary.) 

The other way, which also used to work (though at one point, GRUB was unable to detect UFS2, but I believe that was fixed years ago)

title FreeBSD
root (hd0,0,a)
kernel /boot/loader

I repeat, I haven't tested either of these for years, but even if they don't work, they won't damage anything.

---

### Post by disappearedng on 2008-06-07
But bsd has so many paritions that comes with it. 
How do I know which is the one that I should boot?

How do I find out which /dev/? is my BSD partition?

Thanks

PS: How is GAG coming along? Would you recommend it? is it easy to manipulate? Do I have to give up my existing grub bootloader menu for GAG?

---

### Post by Sef on 2008-06-07
Moved to BSD discussions.

---

### Post by Bachstelze on 2008-06-07
First things first. *Which* BSD did you install ? Also, please paste the output of

```
sudo fdisk -l
```

---

### Post by scottro on 2008-06-07
My bad, in two places, I assumed FreeBSD, and mental shorthand.

From your post, I gathered that you put the BSD in the partition that had belonged to Windows, in other words, what grub sees as hd0,0.  

As for BSD partitions, in general (I'm pretty sure this is for all of them, but at the moment, I only have a FreeBSD one to check, it would be something like

/dev/ad0 is the entire disk
ad0s1 is the BSD partition.  
ad0s1a is root
ad0s1b is swap
ad0s1c is the raw partition, don't worry about it. 
As a rule d is /var/, e /tmp and f /usr but this might differ.

At any rate, IF you put FreeBSD in the partition that had been the Windows one, the syntax I gave you should work as written. The /boot/kernel part is on slice a, the root partition. 

Now, rereading your post I see you had two Windows partitions.  I'm not sure which one is used for BSD, but the syntax I gave you should work--just, if you put it in the partition that Windows had, that was hd0,1 just replace the hd0,0 that I wrote before with hd0,1 and it should work. 
Hopefully, I've been clearer this time, if not, post again, (though I'm going to sleep now, so probaby won't see it till the morning.)  :)

---

### Post by disappearedng on 2008-06-08
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         816     6549504   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         816        4486    29483267   a5  FreeBSD
/dev/sda3            4487       19089   117293400   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           19089       19457     2955960    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           19089       19457     2955928+  82  Linux swap / Solaris

---

### Post by Bachstelze on 2008-06-08
So the two suggestions scottro made in post #2 should work, with hd0,1 instead of hd0,0.

---

### Post by disappearedng on 2008-06-08
Alright! everything works! thanks alot!

---

