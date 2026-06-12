---
title: "Dual Boot"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by ajsemple on 2006-03-28
I have just loaded Ubuntu onto a Windows machine. I loaded onto a separate HD. Ran the installation everything OK.

Except when I restarted Grub came up but it will not boot into XP saying no cylinders not supported by BIOS.

It is also noted that Grub list all options twice.

Any thoughts on how to recover the situation other than a re-load of XP.

Thanks in advance.

Tony

---

### Post by trent dillman on 2006-03-28
Post your /boot/grub/menu.lst

Your xp section should look like this:

```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by belikralj on 2006-03-28
Also you may want to tell us on what partition you have windows installed. To find this go to System->Administration->Disks type in your password when prompted if prompted. and have a look at your hard drives partitions tab. Windows XP should have a "Windows NTFS" filesystem type or "Windows Virtual FAT" or "Windows FAT32".

---

### Post by ajsemple on 2006-03-29
[QUOTE=belikralj]Also you may want to tell us on what partition you have windows installed. To find this go to System->Administration->Disks type in your password when prompted if prompted. and have a look at your hard drives partitions tab. Windows XP should have a "Windows NTFS" filesystem type or "Windows Virtual FAT" or "Windows FAT32".[/QUOTE]
XP Pro is loaded on a 40Gig HD partitioned into 2x20Gig NTFS

Ubuntu is on a separate 40Gig HD format ext3

Does this help.

Tony

---

### Post by Akli on 2006-03-29
Well, the same thing happened to me, ubuntu has changed your "boot.ini" file and your hard drives letters.

What you should do is:

-boot the computer with the windows Xp installation cd,
-check the new hard drive names : c=1, d=2, e=3.
-check where is your windows xp (1 , 2 or 3)

then edit the boot.ini file (it's in the c drive), and replace the stars by your number

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(****)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(****)\WINDOWS="Microsoft Windows


If that might interest you, I'll tell you how my config was:

2 hard drives : "0","1"
"0" was partitioned into 3 partitions ("c" for Windows ME (meaning 1 in boot.ini), "d" for Windows Xp(meaning 2 in boot.ini), and the third was free space reserved for ubuntu).

"1" was not partitioned (hard drive name was "e").

After installing ubuntu, everything changed, "d" swap with "e" and the boot.ini file changed,

Since windows Xp changed from d (i.e 2) to e (i.e 3), I changed this in the boot.ini and everything worked.

BTW: Use ubuntu to edit the "boot.ini" file, it's easier.

---

### Post by ajsemple on 2006-04-02
Now sorted thanks to all who contributed.

Tony

---

