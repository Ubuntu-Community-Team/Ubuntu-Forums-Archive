---
title: "Recovering diskspace"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-03-28
I was using dual booting dapper and XP, when I accidentally crashed my Dapper by accidentally formatting one of the partitions on my hard disk.
I have since installed Edgy using the automatic partitioning facility.
Now how do I recover the disk space previously used by Dapper?
Would appreciate any help from Ubuntu gurus.

Have attached a screenshot of gparted,

Thanks,

J

---

### Post by chewearn on 2007-03-28
I assumed hdc6 and hdc7 were your previous Dapper installation.
Simply delete them from GParted.  If the disk assignment for Edgy (hdc8 and hdc9) changes after the delete, modify menu.lst, else grub will not be able to find it.

Then, the easier way to recover the freed space is either create another partition there.  Or resize hdc2 extended partition to end of hdc9, then resize hdc3 to fill the space in front of it.

---

### Post by jagannath on 2007-03-29
Thanks AstalaVista,

But I'll need some more help. 
I am posting below the relevant parts of the menu.lst

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc8 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc8 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc3.
title		Ubuntu, memtest86+ (on /dev/hdc3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


I would like to know the following:
  1. Will I have to use Gparted Live CD for repartitioning and recovering my Dapper disk space?
  2. Can I safely delete hd6, hdc7, and hdc3?
  3. If after the deletion the partitions get renumbered, what should I do to make sure Edgy boots up and runs properly. 

I am rather scared to fiddle around with the partitions and mess up everything and so the extra caution.

Thanks,

J

---

### Post by chewearn on 2007-03-29
First, make a backup of the menu.lst, in case you made a mistake and need to recover it.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```Then, edit the menu.lst:
```
sudo gedit /boot/grub/menu.lst
```You can delete everything below the line with "chainloader +1" of the Windows XP section, as they refer to the previous Dapper installation:
>  title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

<delete everything below here>
Then, you can use GParted to delete hdc3 (this will not affect the dev assignment).

Finally, you can delete hdc6 and hdc7.  Here is where I'm not sure if it will affect dev assignment (if anyone else in this forum reading this knows the answer, please chip in; I will be glad of the assistance :D).  There are two possibility:
1. hdc8 and hdc9 is unaffected; in which case, you don't have to do anything else (this is likely the case)
2. hdc8 and hdc9 becomes hdc6 and hdc7; in this case, you need to change the menu.lst; replace all (hd0,7) with (hd0,5).

If all of the above went without a hitch, you can reboot and Edgy should be back without problem.  Note: since Edgy uses uuid for fstab entries, you shouldn't have to change anything there.

Post back how it went, especially on the part whether hdc8/9 changes to hdc6/7 or not.  I'm curious to know.:)

Oh, and there is no need to use the livecd to do this, as the partitions you are deleting is not locked (ref. lock icon next to the hdc8 and hdc9).

---

### Post by jagannath on 2007-03-29
Thanks a lot Alta Vista.
I'll just wait till later this evening, just in case a few others on this forum feel like chipping in.
Looks like there shouldn't be any probs. But just in case...

Thanks again,

J

---

### Post by raffytaffy on 2007-03-29
quick question...why do u have 2 swap partitions?

---

### Post by jagannath on 2007-03-29
I'm not too sure, but I think it was created during the Dapper install.

J

---

### Post by raffytaffy on 2007-03-29
well you can use one swap partition for more then one linux install. just point them all toit. im not gonna recomend merging them ..since they are as is..but ehh..for future ref.

---

### Post by jagannath on 2007-03-29
Wel then AstalaVista,

Marked hdc3 for deletion. The partition is shown now as 'unalloted'.
But when trying to delete hdc6 or hdc7, I get a message like this:
"Unable to delete /dev/hdc6!
Please unmount any logical partitions having a number higher than 6"
The same message when trying to delete /dev/hdc7, only the 6 is replaced with 7.

Any ideas??

J

---

### Post by chewearn on 2007-03-29
Ok, it looks like it wants to reassign hdc8/hdc9, when you ask it to delete hdc6/hdc7.  But it can't reassign the hdc8/hdc9 partitions while they are mounted; so it just refuse to delete.

You can either keep hdc6 and hdc7: reformat them, and use them as data partitions;

Or if you still want to delete them, you will have to boot from a GParted livecd.  The hdc8/hdc9 will get reassigned after you delete hdc6/hdc7; so you need to make the correction I mentioned earlier for menu.lst

---

### Post by jagannath on 2007-03-29
That sure clears up things a bit.
How do I format hdc6 and hdc7 (ext3?) to bring them into the Edgy file system? 
And also how to bring the old hdc3 partition, which is now showing as unallocated, for use under Edgy?
Thanks,
J

---

### Post by chewearn on 2007-03-29
> **jagannath said:**
> That sure clears up things a bit.
How do I format hdc6 and hdc7 (ext3?) to bring them into the Edgy file system? And also how to bring the old hdc3 partition, which is now showing as unallocated, for use under Edgy?
Thanks,
J

You can use GParted, right-click over the partitions, select "Format to", and choose a filesystem.  Here is a tutorial on how to mount the partitions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jagannath on 2007-03-30
Thanks a lot AstalaVista.
Am heading right away to Psychocats.

---

