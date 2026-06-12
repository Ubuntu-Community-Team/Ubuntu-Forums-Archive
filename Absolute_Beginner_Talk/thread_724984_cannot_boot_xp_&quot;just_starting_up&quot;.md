---
title: "cannot boot xp &quot;just starting up&quot;"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-03-15
the grub message is just
```
Starting up
_
```

and blinking "_". I have waited for 5 minutes, still the same.:(

this is my grub menu.lst
```

title Windows XP
root (hd1,0)
makeactive
chainloader +1

```

---

### Post by erginemr on 2008-03-15
Can you please post the outcome of the following commands from the terminal:
```
blkid
```
```
sudo fdisk -l
```

---

### Post by oliviacond on 2008-03-15
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b1e8b1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f644f63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

```


blkid
```

/dev/sda1: UUID="1717F9C951347499" TYPE="ntfs" 
/dev/sdb1: UUID="4287ba4b-3534-405f-a0e0-1106f088a78d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="6be40842-5869-4a7e-a114-c6d66af57782" TYPE="swap" 

```

---

### Post by erginemr on 2008-03-15
According to this information, your Windows XP partition resides in sda1, which means (hd0,0) in grub "menu.lst". 

1. So, back up your original file first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.mybackup
```

2. Edit the file with:
```
gksudo gedit /boot/grub/menu.lst
```

Change the line that belongs to Windows and says:
```
root (h1,0)
``` 
to 
```
root (h0,0)
```
Save and exit.

3. Reboot and try to boot into Windows. 

Good Luck.

---

### Post by oliviacond on 2008-03-15
grub error occured
```

Error 13 : Invalid or unsupported executable format

```

ops, i forgot this
```

map                (hd0) (hd1)
map                (hd1) (hd0)

```

---

### Post by erginemr on 2008-03-15
So... It works now?

I suggest you to try removing, or better off, commenting out (#) the two map commands and still use (hd0,0). Reboot and see if that one fixes the problem. 

Otherwise, could you please post your entire menu.lst file here?

For more info on the map command:
[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by erginemr on 2008-03-16
If the above des not work, I suggest you to give a try to Super Grub Disk:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

which pledges to fix Windows MBR with a Grub perspective.

If it doesn't work either, you may start suspecting that your Windows partition bootloader has been corrupted and turn your attention to fixing it by using a Windows Installer CD and the command "fixmbr". Then, you will need to reinstall Grub, for which you can still wield the Super Grub Disk above.

---

### Post by oliviacond on 2008-03-22
the map solved my problem.

---

