---
title: "[SOLVED] [TriBoot Intel x86] Doubt reinstalling XP"
date: 2008-08-31
forum: Apple Hardware Users
---

### Post by Telémakhos on 2008-08-31
Hi all, I've a triboot system (XP, OSX, Ubuntu) in the same HDD. Now I need to reinstall XP and I dont know how could I save the GRUB configuration since I think that the XP bootloader will overwrite it. Here are my partitions (quite simple as you can see):

> Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  161GB  161GB   primary   ntfs         boot 
 2      161GB   322GB  161GB   primary   hfs+              
 3      322GB   344GB  21.5GB  primary   ext3              
 4      344GB   500GB  157GB   extended                    
 5      344GB   462GB  118GB   logical   ext3              
 6      462GB   500GB  38.4GB  logical   fat32



> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36eb36ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sda2           19582       39162   157284382+  af  Unknown
/dev/sda3           39163       41773    20972857+  83  Linux
/dev/sda4           41774       60801   152842410    5  Extended
/dev/sda5           41774       56133   115346668+  83  Linux
/dev/sda6           56134       60801    37495678+   b  W95 FAT32


Once formatted and reinstalled XP in sda2 I suppose that I won't can load Mac and Ubuntu. Then, If I reinstall GRUB and I copy the actual /boot/grub/menu.lst would be enough to get the triboot wotking another time? 

If not, how could I accomplish it?

---

### Post by ajgreeny on 2008-08-31
Just go ahead and reinstall XP as normal to the same partition as it is now, not sda2, as you say, but sda1.  I think sda2 is probably your OSX install..  This will overwrite the MBR where you probably installed grub at the installation of Ubuntu.  After XP is back, you will not have a grub menu appear but we can get that back easily as follows:-
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

The new grub install will still point to /boot/grub/menu.lst in your Ubuntu install, but it is possible thet the UUID for windows partition will have changed so you may need to edit the menu.lst to take account of that fact.  You can find the UUID with the command ```
sudo blkid
```and compare the output with the menu.lst entry for windows.

---

### Post by Telémakhos on 2008-08-31
Thank you sooo much ajgreeny! I'll follow this. 

BTW you're right, sda2 is OSX and sda1 XP  (sorry it was a typo)

---

### Post by cyberdork33 on 2008-08-31
The EFI bootloader will see GRUB if it is installed to the Ubuntu partition and then Windows won't overwrite it. This will also allow you to select windows from refit and not have to go through the GRUB menu.

---

### Post by Telémakhos on 2008-08-31
Done, and working like a charm. Thanks guys!

---

### Post by ajgreeny on 2008-08-31
Just out of interest, which way did you do it?  I have no knowledge of OSX so didn't know about the other suggestion.

---

### Post by Telémakhos on 2008-09-02
> **ajgreeny said:**
> Just out of interest, which way did you do it?  I have no knowledge of OSX so didn't know about the other suggestion.

I tried your way... :)

---

