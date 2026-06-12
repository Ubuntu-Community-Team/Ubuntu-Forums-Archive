---
title: "dual boot problems"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by mummra1 on 2007-12-27
I just installed Kubuntu 7.10 on a Toshiba laptop that already had an NTFS partition for Windows XP.  I had done this before, on a PC, and easily achieved dual booting with grub.  However, I am now unable to boot into XP, I believe b/c the XP partition has something called Pointsec, an encryption application.  I manually added the Windows option into menu.lst, but it just kicks back to Kubuntu.  When I try to mount the partition (/dev/sda1), it gives me the error:

```
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

This same error message appears when I do a recovery boot into Ubuntu. Apparently, it REALLY doesn't want to mount that partition.  Can someone please help?  Thanks!

---

### Post by blueridgedog on 2007-12-27
You receive the error when trying to mount the partition in Linux?

Try the dual booting tips here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by mummra1 on 2007-12-27
I can boot into Kubuntu just fine.  The problem is that I cannot boot, nor mount, the windows partition, /dev/sda1

---

### Post by blueridgedog on 2007-12-28
Ok, 

what happens when you select windows from you boot menu?

Can you post your /boot/grup/menu.lst file?  You can access it with:

```
cat /boot/grub/menu.lst
```

Can you post the output of:

```
sudo fdisk -lu
```

and 
```

cat /proc/partitions
```

and finally 

```
mount
```

---

### Post by mummra1 on 2007-12-28
Thanks for all the help everyone, but I got it to work.  It turns out that at the grub menu, the FIRST time I select 'Windows XP', it loads the encryption for that partion (PointSec), but doesn't boot up.  It kicks me back to the grub menu, and if I select Windows again, it boots up no problem.  Kind of strange, but since I can reproduce it and it doesn't really cause a headache, I can easily live with it.  Thanks again!

---

