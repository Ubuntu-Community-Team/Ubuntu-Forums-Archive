---
title: "Having difficulties booting Windows XP from Grub"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Dician on 2008-04-01
I recently reinstalled Ubuntu 7.10 on my laptop, and haven't been having problems until I went to switch back to my Windows partition. When Grub came up, there was no entry for Windows, so I looked up how to make one. I tried booting this way, but all I got was a "Starting up...." screen for roughly 10 minutes before I did a hard-reset and came here. 

I took a screenshot of my gparted screen, if that helps. 

[http://img528.imageshack.us/img528/3724/screenshotln7.png](http://img528.imageshack.us/img528/3724/screenshotln7.png)

sda1 is Ubuntu, sda2 is the Windows partition I want to boot to, and sda5 is my shared storage partition.

Below are my Grub entries. The last one is the one I modified (obviously :-p)

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=678a0c2d-2810-4d98-b8c9-9bebb7bdef27 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=678a0c2d-2810-4d98-b8c9-9bebb7bdef27 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional Edition
root		(hd0,1)
makeactive
chainloader +1

```

---

### Post by c-ron on 2008-04-01
> 
title		Windows XP Professional Edition
root		(hd0,1)
makeactive
chainloader +1


try changing it to:

> 
title		Windows XP Professional Edition
rootnoverify (hd0,1)
makeactive
chainloader +1


---

### Post by udh on 2008-04-01
Hi,
this page is dedicated to GRUB only, have a look at it: 
> [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Dician on 2008-04-01
changing it to noverify didn't help. I'm reading that other page now.

---

### Post by dsauxier on 2008-04-01
I had a similar problem many moons ago and the problem was that Windows doesn't like it when you change it's boot partition.  Since you've now added several linux partitions, windows needs to know to boot to  the new partition (it uses C:\boot.ini).

From linux, mount the windows drive  and check out the boot.ini file.

Make a copy before making any changes, but my guess is you'll want to use partition(4) 
Since it takes a reboot to make changes to the file if it fails, you might make several alternative boot options in the menu so that you do the trial-and-error test faster.

Here's an uninteresting example of a boot.ini (I added the "Test 4" and "Test 5" lines
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="MS Test 4" 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="MS Test 5"
/noexecute=optin /fastdetect

---

### Post by kushykush on 2008-04-03
The problem appears to be not GRUB but the Windows MBR in the windows XP boot loader.   Windows is booted through its own boot loader.  It will not share any other.  Once Windows MBR is fixed you can then use GRUB to fire Windows boot loader which, in turn, will boot your XP.

---

### Post by dstew on 2008-04-03
Your menu.lst entry looks correct. The behavior suggests that the problem is within Windows. Please post the contents of your boot.ini file from Windows.

---

