---
title: "Another dualboot grub question"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by MadsRH on 2007-03-17
Hi
I'm trying to make my computer dualboot between XP and Ubuntu. I've searched the web and edit the menu.lst as I think it should be, but I'm getting this error:
[B]
Filesystem type unknown, partition type 0x5
Error 12: Invalid device requested[/B]

Here is my menu.lst:
[ATTACH]27674[/ATTACH]

Any help is welcome - thanks
*MadsRH*

---

### Post by rsambuca on 2007-03-17
You have everything in the wrong order.  You have to put this entry```
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```at the end after the line that says ```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by MadsRH on 2007-03-17
I will just try that right now. Thank you for the fast reply :)

---

### Post by rsambuca on 2007-03-17
You'll also have to change the default number from zero to whatever you want.

---

### Post by MadsRH on 2007-03-18
Witch zero?
It's not working, I get the same error as before and now XP is at the bottom. I would like to boot into XP default.

---

### Post by -pod- on 2007-03-18
This zero ```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

you should change it with the right kernel number with which you'd like to start
(so if xp is the 6th kernel listed on your grub menu, you should change it with a 6)

---

### Post by MadsRH on 2007-03-18
Okay, thanks
I will edit that right away, but doesn't that just fix the boot order? Will I get the same error as before with XP?

---

### Post by -pod- on 2007-03-18
the *default number* just sets the kernel which has to be loaded by default, it doesn't change the order in which they are listed.

If you want to do that, you have to cut&paste the kernel entry for XP and put it before (or after) the other kernel entries

---

### Post by MadsRH on 2007-03-18
Okay, but I'm still getting the **Error 12: Invalid device requested**

---

### Post by -pod- on 2007-03-18
but do you succeed in booting or not?

anyway the bad device error should probably come from wrong settings in here
```
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```

*root (hd0,1)* refers to the first hard disk (0), first partition(1)
so if you have Win on another hd or partition, you should change those numbers accordingly to that

---

### Post by MadsRH on 2007-03-18
Okay, so if XP is the slave it has to say:
*root (hd1,0)*

I'll just try that!

---

### Post by -pod- on 2007-03-18
> **MadsRH said:**
> Okay, so if XP is the slave it has to say:
*root (hd1,0)*

I'll just try that!
quite right, but i'm not sure.
It depends on how you partitioned your disks it could be as well (1,1) but you got the point :)

---

### Post by MadsRH on 2007-03-18
I didn't succeed in booting into XP. Ubuntu works fine and still runs default.

I've edited the file like this now:
```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1
```

Still crashes, but now I'm getting 0x7 in:
**Filesystem type unknown, partition type 0x7**
and the *press any key...* is gone!

---

### Post by rsambuca on 2007-03-18
I think because you have XP on the secondary drive, you will have to re-map your drives to trick XP into thinking that it is the primary drive.

---

### Post by dbeckham32 on 2007-03-18
FYI, I have my machine set up with dual boot for Windows XP. Here's a snippet from my menu.lst:


## ## End Default Options ##

title		Custom kernel 2.6.20
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20 root=UUID=6661de12-a73b-476d-ad09-ee8691bda13c ro pnpacpi=off quiet
initrd		/boot/initrd.img-2.6.20
savedefault
boot

title		Custom kernel 2.6.20 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20 root=UUID=6661de12-a73b-476d-ad09-ee8691bda13c ro pnpacpi=off single
initrd		/boot/initrd.img-2.6.20
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=6661de12-a73b-476d-ad09-ee8691bda13c ro pnpacpi=off quiet
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=6661de12-a73b-476d-ad09-ee8691bda13c ro pnpacpi=off single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Freespire Ver. 1.0.13  (on /dev/hda6)
root 		(hd0,5)
kernel 		/boot/vmlinuz-2.6.14-gratis  root=/dev/ide/host0/bus0/target0/lun0/part6 rootdev=0x0306 ramdisk=35392 video=vesafb:nomtrr jiffymount=noatime resume2=swap:/dev/hda6:0x44000 vga=0x311
initrd 		/boot/initrd-2.6.14-gratis.gz


title		Fedora Core 5 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1.2054_FC5smp root=/dev/hda7 ro quiet 
initrd		/boot/initrd-2.6.15-1.2054_FC5smp.img
boot

title		Windows XP (on /dev/hda3)
rootnoverify	(hd0,2)
makeactive
chainloader 	+1

title		This list is loading from the boot partition on hda2
root

---

### Post by tza on 2007-03-18
I don't know if your needs are similar to mine,  but I found this post very helpful for dualbooting an XP machine.
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by tza on 2007-03-18
just to follow up - 

having followed the instructions linked to in my previous post (disconnect the XP drive option), I have WinXP installed on what is now the second hard disk device (as slave), and ubuntu is installed on the first device (master, recently installed), however, GRUB boots into WinXP by default, and presents the option to select ubuntu.  

Everything works perfectly, although it did take XP nearly 10 minutes to fully load as it decided what to do with the newly installed hard drive.

I hope you have found good results.

---

