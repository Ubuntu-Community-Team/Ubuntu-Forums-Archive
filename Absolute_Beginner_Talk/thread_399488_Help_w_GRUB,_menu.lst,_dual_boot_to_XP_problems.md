---
title: "Help w/ GRUB, menu.lst, dual boot to XP problems"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by ryanryan on 2007-04-02
Hi.  I'm brand new to all this -- I just completed my first successful linux installation on Friday.  

I'm *certain* that my problem is a common one, but I can't seem to find the answer when I search these forums or [Google Linux]("http://www.google.com/linux").  If you can point me to the appropriate post or site, I'd greatly appreciate it.

The problem:
- I can no longer boot to Windows XP after having successfully installed Ubuntu.  
- GRUB gives me two windows options, but when I select either one the screen simply goes black.  No output.  No disk activity.  Nothing.  The computer just hangs, doing nothing.  

My set-up:
- I have a Sony VAIO desktop w/ two internal 250 GB drives, with Windows XP (Meida Center Edition)
- Before I installed Ubuntu, I physically swapped the two drives so that I could keep the "C:" drive intact.  
- My primary drive (i.e. what used to be my "D:" drive before the swap) contains the linux partition(s) on the first 110 GB, and the remaining 128 GB is still an NTFS formatted partition.  
- My secondary/slave drive (i.e. what used to be my "C:" drive before the swap) contains Windows.
- [Click here ]("http://www.paperwindow.com/partitions.jpg")to see what my partitions looked like *prior to* me swapping the hard drives and installing Ubuntu.  

What I've done so far:
- searched online for solutions to this problem
- read through the [GRUB manual ]("http://www.gnu.org/software/grub/manual/")
- ensured that my menu.lst file was using "map" to virtually swap the drives.
- checked my menu.lst file against several other examples online and played around with several of the variables.  
- You can see a copy of my current menu.lst file by [clicking here]("http://www.paperwindow.com/menu.lst.txt").

I'm not sure what to try next.  From what I've been reading, everything *should* be working just fine.  Unfortunately, it isn't.  :confused: 

If you could help (or point me in the direction of help) I'd greatly appreciate it!

Thanks for your time!

Regards,

Ryan

---

### Post by alien21010 on 2007-04-02
Try this (just add it to the end of your /boot/grub/menu.lst file:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

Basically the problem here is that you need to map the hard drives before you tell grub where the root partition is on that hard drive.

---

### Post by dstew on 2007-04-02
I see a couple of problems with your menu.lst. First, put your map statements before your root statement, and make your root statement a rootnoverify:

map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

---

### Post by ryanryan on 2007-04-02
Unfortunately, those didn't work either.  Still the same error.  :( 

I just learned how to use GParted, though.  If it helps to see what my partitions look like I've posted them here:  [hda]("http://www.paperwindow.com/hda.png") and [hdb]("http://www.paperwindow.com/hdb.png").  

Also, here is what "fdisk -l" produces:

[FONT="System"]Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        7161       13773    53118922+  83  Linux
/dev/hda2           14058       30401   131283180    7  HPFS/NTFS
/dev/hda3               1        7160    57512668+  83  Linux
/dev/hda4           13774       14057     2281230    5  Extended
/dev/hda5           13774       14057     2281198+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         784     6297448+  12  Compaq diagnostics
/dev/hdb2             785       30515   238814257+   7  HPFS/NTFS[/FONT]


If anyone knows of anything else I can try, PLEASE let me know... Thanks!

Regards,

Ryan

---

### Post by ajmorris on 2007-04-02
> **ryanryan said:**
> Unfortunately, those didn't work either.  Still the same error.  :( 

I just learned how to use GParted, though.  If it helps to see what my partitions look like I've posted them here:  [hda]("http://www.paperwindow.com/hda.png") and [hdb]("http://www.paperwindow.com/hdb.png").  

Also, here is what "fdisk -l" produces:

[FONT="System"]Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        7161       13773    53118922+  83  Linux
/dev/hda2           14058       30401   131283180    7  HPFS/NTFS
/dev/hda3               1        7160    57512668+  83  Linux
/dev/hda4           13774       14057     2281230    5  Extended
*/dev/hda5           13774       14057     2281198+  82  Linux s
wap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         784     6297448+  12  Compaq diagnostics
/dev/hdb2             785       30515   238814257+   7  HPFS/NTFS[/FONT]


If anyone knows of anything else I can try, PLEASE let me know... Thanks!

Regards,

Ryan

Try putting this in as a new entry (add it right under the memtest86+ entry) : 

```
title		Windows Media center (or whatever you want to call it)
root		(hd1,**1**) 
savedefault
makeactive
chainloader	+1

```
*(it is hd1,1 because grub starts from 0 not 1 so hd1,1 simbolises second hard disk on second partition)
*(also i assumed the automatic entry from you menu.lst file was right so i made it boot your second hard disk on your second partition. 

now reboot and see if you can boot windows through this entry.

---

### Post by dstew on 2007-04-02
I agree with ajmorris, you need to make /dev/hdb2 your root by using **(hd1,1)** in the grub root command. But I also think you still need the map statements.

Also, it might be necessary to make /dev/hdb2 bootable by changing the boot flag. But, the **makeactive** statement in the grub menu.lst item does this for you.

---

### Post by ryanryan on 2007-04-05
Well, over the past several days I've entertained a host of other variations in my menu.lst file.  I've changed 0s to 1s and 1s to 0s and back again.  I've dropped the "map" lines, put them back in.  Tried removing "makeactive", "savedefault".  Changed root to rootnoverify, then back again.  Nothing, thus far has worked.  I'm beginning to wonder if the problem is something other than the menu.lst file.  I checked my device.map file, but the appropriate entries for both drives are there.  

Regardless, I (phsyically) swapped the hard disks back again and, yes, Windows boots just as it always did before.  

Here's what I'm thinking about doing next.  I'm going to try installing linux on the same disk as Windows.  That way, both Windows and Linux will be on hda.  As for hdb, I'll just reformat it and cut it into two partitions -- one NTFS and one EXT3.  

But this leads to anther question:
**Do I need to make any extra partitions on my primary drive so that the /boot partition will be on the first *n* MBs of the disk?**

Thanks again for your help,

Ryan

---

### Post by jhenager on 2007-04-06
Before you give up and reinstall, check out my fdisk and menu.lst and see if it helps. I just solved the same problem on my system. I have a different HD setup, but you can just amend the entries to reflect yours.
Disk /dev/sda: 200.0 GB, 200049647616 bytes [COLOR="Red"]Edgy[/COLOR]
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24133   193848291   83  Linux
/dev/sda2           24134       24321     1510110    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/hda: 20.0 GB, 20020396032 bytes [COLOR="Red"]Dapper[/COLOR]
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041   83  Linux

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3328    26729472    7  HPFS/NTFS  [COLOR="Red"]Vista[/COLOR]

menu.lst
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Other operating systems:
root

title           Windows Vista
root            (hd1,0) 
savedefault
makeactive
chainloader     +1
****************************************
Hope this helps. I fiddled with mine for days, so I feel ya, bud. :)

---

