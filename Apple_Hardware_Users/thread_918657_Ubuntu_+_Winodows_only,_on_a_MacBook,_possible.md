---
title: "Ubuntu + Winodows only, on a MacBook, possible ?"
date: 2008-09-13
forum: Apple Hardware Users
---

### Post by MrMonk on 2008-09-13
Today I got bored with my Leopard and decided to install Ubuntu instead and deleate Leopard. That was because I don't really use MacOS due to some work related issues. I installed Ubuntu and in the process deleted the MacOS partition. When I restarted, Windows XP (SP2) would not work nor did Ubuntu.
I read some things online and now Ubuntu Works, but windows gives me an error at start up, basically a blue screen: Unmountable_boot_volume.
Windows starts loading but while still loading I get the blue screen...
Any ideas of how to make Windows work again ?
thanks a lot guys
mM

---

### Post by mabovo on 2008-09-13
You can use the recovery disc from Apple and reinstall MacOSX again.

---

### Post by MrMonk on 2008-09-13
Is that the only way ??? I need windows working... I don't wanna lose that...

---

### Post by cyberdork33 on 2008-09-13
because you messed with the partitions after windows was installed, it has a fit.

Can you post the output of 
```
sudo fdisk -l
```

and 
```
sudo parted /dev/sda print
```

---

### Post by MrMonk on 2008-09-13
sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d627d62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        5497    43945313   83  Linux
/dev/sda3   *        5656        9730    32726064    7  HPFS/NTFS
/dev/sda4            5497        5656     1274414+  82  Linux swap / Solaris

Partition table entries are not in disk order


------------------------------------------------------

sudo parted /dev/sda print

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot 
 2      210MB   45.2GB  45.0GB  ext3                                    
 4      45.2GB  46.5GB  1305MB  linux-swap                              
 3      46.5GB  80.0GB  33.5GB  ntfs         Untitled 2            boot 

Information: Don't forget to update /etc/fstab, if necessary. 


--------------------------


So is it bad ? :)

---

### Post by MrMonk on 2008-09-13
Update:
I read about gParted, made a start up disk, GParted loads up to the point where I'm supposed to chose the keyboard layout and then it's frozen..
I ran GParted from Ubuntu, it works but it says it doesn't know what to do with ntfs partition, maybe because is missing some ntfs tools ?
Bottom line, dead end...

---

### Post by MrMonk on 2008-09-13
Update:
I tried the recovery console from Windows XP. Problem is Windows XP does not recognize that another version is installed and does not give me the option to recover the older version. I thought I was not seing the option so I went all the way and installed XP again.
I still get the same error even with the new Windows installation.

I used the Microsoft support and created a console recovery on the C drive on a different computer, copied the files on my Mac, changed the boot.ini file, but I've got nothing the option for recovery is still not there...

dead end again...

---

### Post by MrMonk on 2008-09-13
Update:
It seems Grub may actually cause Windows to not load properly, something with Single user mode....
I should delete Grub from MBR but so far I don't know how to do...

---

### Post by MrMonk on 2008-09-13
I successfully killed Grub, so now I can't log on Ubuntu, but windows still have the same problem with unmountable crap....

---

### Post by MrMonk on 2008-09-14
No one knows nothing huh ? :) Ouch !
Well was a big mistake to play with Ubuntu and Linux in general.... 6-7 years ago I decided Linux was too young to be worth it, but I see 7 years later nothing has changed :)
Back to Mac + Windows...see you guys in ...6 years maybe ? :)

---

### Post by MrMonk on 2008-09-15
Update:
Leopard is back, Ubuntu is out, WIndows still not working, and I can't see it from MacOs but I still can see it from Ubuntu live CD... I'm getting close to the initial state of affairs... after 36 hours of headache

---

### Post by DGortze380 on 2008-09-15
just out of curiosity, (always check the simple things first), do you have rEFIt installed? or are you at least holding the option key at start up?

---

### Post by MrMonk on 2008-09-15
"rEFIt installed" - yes/ no tried both ways

" or are you at least holding the option key at start up" - yes/ no tried them both

I know what the problem was, something about Windows being "aware" of its environment, but couldn't modify registry..

Anyway, I installed Leopard, played a bit with windows, now both work as they did before all the damage I did... only took me 48 h ...damn it...
Conclusion: don't play with fire if you're not a fire fighter :)

---

### Post by cyberdork33 on 2008-09-15
> **MrMonk said:**
> "rEFIt installed" - yes/ no tried both ways

" or are you at least holding the option key at start up" - yes/ no tried them both

I know what the problem was, something about Windows being "aware" of its environment, but couldn't modify registry..

Anyway, I installed Leopard, played a bit with windows, now both work as they did before all the damage I did... only took me 48 h ...damn it...
Conclusion: don't play with fire if you're not a fire fighter :)

What you wanted to do will probably work, you will probabaly need to install Windows again though.

You can install GRUB to the Ubuntu partition where it won't touch the Windows bootloader, but you will still probably get the same issue.

Alternatively, if you really don't want to use OS X, then you can reformat your entire drive to a normal MBR table rather than the GPT that the Mac uses by default. That would make things a lot easier in the end as the partitioning is a little less picky.


PS Sorry about the delayed answer, I have been out of town with no Internet.

---

### Post by MrMonk on 2008-09-16
Thank you cyberdork33, too bad Ubuntu and the Linux community in general doesn't have more people like you...
Everything is back to normal now, Leopard + Windows both happy campers :)
I'm sure I could have make it work eventually but I needed Windows and couldn't afford to lose the windows partition nor to waste more time trying..
I'm off this forum !

Good luck guys !

---

