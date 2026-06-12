---
title: "Dual Booting with Vista problem"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by littledude565 on 2007-12-15
hey all i have 2 HDD's a 200gb with Vista already installed and a blank 120GB i wanted to re-use Ubuntu since i loved it so much, and i decided to Dual boot again but it has gone horrifically wrong.
1st i decided to install Ubuntu to the 120gb its all good Ubuntu is fine but now i cant use Vista, when i go to the vista option on GRUB it didnt load up at all. so i backed everything up accidentally Deleted the Windows folder >_> and i tried putting in a Vista boot CD but i cant boot into it. help please :(:confused::(:confused:

---

### Post by Ub1476 on 2007-12-15
Post the result of 

```
sudo fdisk -l
```

---

### Post by littledude565 on 2007-12-15
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aa7ba4f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006195

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14334   115137823+  83  Linux
/dev/hdb2           14335       14946     4915890    5  Extended
/dev/hdb5           14335       14946     4915858+  82  Linux swap / Solaris

---

### Post by Ub1476 on 2007-12-15
Vista is there, so no worries. Try [Super Grub]("http://supergrub.forjamari.linex.org/") to fix it.

---

### Post by seventhc on 2007-12-15
I had vista on my sony before i took it off, but I made the back up disks first and it took 2 dvd's. If you have more than 1 disk are you sure your putting in the correct disk??I ask because nothing in grub should effect booting off a cd/dvd. 
One thing you might try would be to look in Aplications>Add/Remove make sure that 'all open source applications' is set in the upper right corner then do a search for boot, there is a boot manager in there it might help.

---

### Post by littledude565 on 2007-12-15
> **Ub1476 said:**
> Vista is there, so no worries. Try [Super Grub]("http://supergrub.forjamari.linex.org/") to fix it.
but i Deleted the Windows folder
:cry::cry::cry::cry:

---

### Post by seventhc on 2007-12-15
is this a real windows vista cd or just your files that you put onto a cd???
I assume your bios is still set to boot from cd since you were able to boot ubuntu from cd.

---

### Post by littledude565 on 2007-12-15
Yes it is a Vista Ultimate CD, and yes the BIOS is set to boot from CD

---

### Post by clonne4crw on 2007-12-15
I dunno. What can you  expect from Windows? Especially Vista. This was the original reason I ditched Windows in the first place. :???:

---

### Post by littledude565 on 2007-12-15
Help me please someone :cry:

---

### Post by littledude565 on 2007-12-15
For Some reason i can boot into any of my windows discs for vista i get Windows Boot Manager

Windows failed to start. This may be due to hardware or software changes.....
...

File: \Boot\BCD

Status: 0x000000f

Info: An error occured while attempting to read the boot configuration data.

and for XP it keeps rebooting

---

### Post by seventhc on 2007-12-15
You said you have 2 hdd's, was 1 of them just added? I think it might not be connected correctly.
If you just added a second hard drive, I would take it out and test if vista will then boot properly.

...wait...what the heck is BCD?? Boot CD?? Is that from microsoft??? or are you using EasyBCD??

---

### Post by dstew on 2007-12-15
It sounds like the VIsta boot sector and initialization files are no good. You might need to use the Recovery Console to fix Vista before you can boot it. [Here]("http://windowshelp.microsoft.com/Windows/en-US/Help/2b3724d1-f4ad-5b26-16dc-3e9e66f4be5e1033.mspx") is a link you might look at.

---

