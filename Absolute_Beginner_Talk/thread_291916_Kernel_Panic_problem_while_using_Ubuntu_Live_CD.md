---
title: "Kernel Panic problem while using Ubuntu Live CD"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by WonderingWanderer on 2006-11-03
Hi, 

I have a 1GB Intel Dual Core machine running Windows XP. I wanted to run the Live CD only to start Ubuntu but NOT install it. So, I changed my boot sequence in BIOS to have CD Drive come before Internal HDD so that I could run the Live CD before my machine booted WinXP.

I restarted my machine with the Live CD in the CD Drive and sure indeed I got the Ubuntu Menu right up. I selected the "Start and Install Ubuntu" option which then gave a "Loading Linux Kernel" message window. This window remained for 10 minutes on my screen with the Live CD making screeching noises from the CD drive. After the 10 minutes, I got a black screen with the following messages - 
-------------------------------------------------
Uncompressing Linux .. OK. booting the kernel.
[4294672.192000] invalid compressed format (err=2)
[4294672.193000] kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
--------------------------------------------------
And, nothing happens. I am wondering -
1. Could the screeching noise made by the Live CD mean the CD is corrupted, thereby causing the above problem
2. Is there some settings in my computer that I have to change to be able to run the Live CD.

Looking forward for some help on this. Thanks in advance.

---

### Post by dmizer on 2006-11-03
lol ... the cd made a "screeching" noise?  i'd certainly suggest testing it.  what speed did you burn the cd at?  since the iso burns a completely full cd, it's important to burn it at a slower speed than you would otherwise.  somewhere around 4x or 8x is much more reliable when you pack that much data onto a cd.

there is an option in the boot to test the cd for errors, if it finds errors, chuck it and try again.

if not, try typing "acpi=off" next to where it says "boot"

---

### Post by copeland on 2006-11-03
my live cd has given me tons of trouble...I tested it and it turned out fine, but I still find at times when loading it it will hangup at certain areas, like where you described, or int he ubuntu boot screen when it first begins to load the kernel and other apps...

I had just assumed it was ubuntu being unstable...

---

### Post by dmizer on 2006-11-03
no, if it hangs during boot/loading, that usually means that one of the modules (usually acpi or video) doesn't agree with your hardware, so you should try some of the alternative boot options available to you.

just hit f6 for "other options" when you see this screen: [http://debianadmin.com/copper/displayimage.php?pid=734&fullsize=1](http://debianadmin.com/copper/displayimage.php?pid=734&fullsize=1)

---

