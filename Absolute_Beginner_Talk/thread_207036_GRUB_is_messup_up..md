---
title: "GRUB is messup up."
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by XLostSpartanX on 2006-07-01
Ok here is my configuration.  I have 2 HDD's, both 160 gb's.

On HD 1:
Windows Partition
Ubuntu Partition

On HD 2:
Free Space Partition
SuSe Partition

Now, I had windows installed first, then I intstalled SuSe.  It was working great.  Then I installed Ubuntu, and Windows won't appear in GRUB.  All the different Ubuntu versions are there, and even SuSe, but not Windows.  I really need help. :mad: 

-Nick

---

### Post by richbarna on 2006-07-01
Take a look at this (post #3 by aysiu):-
[http://www.ubuntuforums.org/showthread.php?t=205163&highlight=add+windows+grub]("http://www.ubuntuforums.org/showthread.php?t=205163&highlight=add+windows+grub")

Don't panic, it's a common question :)

---

### Post by XLostSpartanX on 2006-07-01
Hmm ok.  I dont really knwo where my Windows partition is.  I did the fdisk thing and this is what I got.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15527   124720596    7  HPFS/NTFS
/dev/sdb2           15528       19457    31567725    f  W95 Ext'd (LBA)
/dev/sdb5           15528       15624      779121   82  Linux swap / Solaris
/dev/sdb6           15625       17163    12361986   83  Linux
/dev/sdb7           17164       19457    18426523+  83  Linux


I dont see windows anywhere in there?  Help?:confused: 


-Nick

---

### Post by richbarna on 2006-07-01
[QUOTE=XLostSpartanX]Hmm ok.  I dont really knwo where my Windows partition is.  I did the fdisk thing and this is what I got.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdb1               1       15527   124720596    7  HPFS/NTFS[/COLOR]
/dev/sdb2           15528       19457    31567725    f  W95 Ext'd (LBA)
/dev/sdb5           15528       15624      779121   82  Linux swap / Solaris
/dev/sdb6           15625       17163    12361986   83  Linux
/dev/sdb7           17164       19457    18426523+  83  Linux


I dont see windows anywhere in there?  Help?:confused: 


-Nick[/QUOTE]

So you need to put sdb1 in the menu.lst

> title           Microsoft Windows XP Home Edition
root            ([COLOR="Red"]sdb,1[/COLOR])
savedefault
makeactive
chainloader     +1

---

### Post by XLostSpartanX on 2006-07-01
That still dosn't work.  It gives me Error 23: Error while parsing.

-Nick

---

### Post by richbarna on 2006-07-01
Are you using the ubuntu grub boot or the suse grub boot?
In ubuntu try this command :-
> sudo update-grub
And reboot.
If that fails, maybe you could try doing the same thing on suse.

Read this also :-
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

### Post by confused57 on 2006-07-01
Your menu.lst Windows entry should probably look something like this:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Here's an excellent link explaining grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by XLostSpartanX on 2006-07-01
[QUOTE=confused57]Your menu.lst Windows entry should probably look something like this:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Here's an excellent link explaining grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)[/QUOTE]
That didn't work eitehr.  It said that the NTLDR is missing.  And tehn said to press Ctrl+Alt+Del to restart.

---

### Post by confused57 on 2006-07-01
[QUOTE=XLostSpartanX]That didn't work eitehr.  It said that the NTLDR is missing.  And tehn said to press Ctrl+Alt+Del to restart.[/QUOTE]

Are you able to boot Windows at all?  NTLDR is the Windows boot manager & if you can't boot Windows, it may be corrupted.  If that is the case you'd need to startup the computer with the Windows installation cd(not a recovery cd) and go into recovery mode(press "r") and type in  fixmbr    to repair the Windows NTLDR.   
I don't know for sure, someone more experienced with this may be able to give you a solution.

---

### Post by XLostSpartanX on 2006-07-01
[QUOTE=confused57]Are you able to boot Windows at all?  NTLDR is the Windows boot manager & if you can't boot Windows, it may be corrupted.  If that is the case you'd need to startup the computer with the Windows installation cd(not a recovery cd) and go into recovery mode(press "r") and type in  fixmbr    to repair the Windows NTLDR.   
I don't know for sure, someone more experienced with this may be able to give you a solution.[/QUOTE]
Well, before I installed Ubuntu I could boot Windows.  So if I fix the mbr, how will I get grub back?  And more importantly, get windows onto grub?

---

### Post by confused57 on 2006-07-01
From Ubuntu, try posting the output of:
```
cat /boot/grub/menu.lst
```
the menu.lst is short for menu.list, not menu.first.

or at least post where the root is for the OS that boot,
for example, since Ubuntu boots OK, list that...I believe it may 
be "root  (hd0,0)"...if Suse boots OK, list it's root.  I think that may
tell us something to go on?

---

