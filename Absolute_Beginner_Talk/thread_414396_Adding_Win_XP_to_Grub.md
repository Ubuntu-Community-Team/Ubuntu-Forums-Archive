---
title: "Adding Win XP to Grub"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2007-04-19
Very long story short, my old hard drive went bad. It's the hard drive that had Grub on it. I installed Grub on to my new hard drive (which has Windows and Linux dual booting), but it only added the menu entries for Linux. I need to know what to put in the menu.lst for Grub to make it load my Win XP also.

Here's the details.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device    Boot      Start         End      Blocks   Id  System
/dev/sda1               1           19316   155155738+   7  HPFS/NTFS
/dev/sda2    *       19317       38631   155147737+  83  Linux
/dev/sda3            38632       38913     2265165    5  Extended
/dev/sda5            38632       38913     2265133+  82  Linux swap / Solaris


Of course, Sda1 is my Windows partition.

Here's my current menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

title		Windows XP
root		
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

I need to know what to put for the root for the Windows XP entry. Or do I need to add anything else?
Thank you everybody.

---

### Post by x64Jimbo on 2007-04-19
Change that last part to look like this:

title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by TekMuzik on 2007-04-19
> **x64Jimbo said:**
> Change that last part to look like this:

title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

I'll give it a try. Thanks.

---

### Post by TekMuzik on 2007-04-19
Got an error..it says 
"NTLDR is missing
Press Ctrl-Alt-Del to restart"

---

### Post by x64Jimbo on 2007-04-19
That's a non-Ubuntu problem. Here's a link that might help you fix it.
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)
I'm subscribed to this thread if you need more assistance with Ubuntu once you've gotten the NTLDR problem fixed...

---

