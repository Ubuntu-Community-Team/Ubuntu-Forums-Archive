---
title: "[SOLVED] acessing my Windows HD"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-22
ok im running a 2 hard drive dual boot with Xubuntu and WIndowsXP

Xubuntu lives in a 20gb drive 

the XP drive is in another 20gb drive (2 partitions 5gb and 15gb).  WinXP lives in the 5gb partition, the 15 is storage.

I cannot access the 5gb partition (NFTS format) but i dont care.
The 15gb partition mounts and unmounts and i can access it using my file manager (Thunar).

However, i cannot access it from the applications.  So if i want to use a word document or an mp3 file i have to open the 15bg partition and click on the actual file or right click and use the Open with... 

or some applications will allow me to import folders

or sometimes i need to actually tell the application exactly where it is /media/disk/whateverfolder

is there anyway i can configure it so this 15gb partition shows up under places automatically for all my applications?

im sure theres an easy answer. thanks to anyone who can help.  keep the explanation at newbie level though :)

---

### Post by jken146 on 2007-12-22
edit:  My previous suggestion wasn't so newbie-friendly perhaps.  Try [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows).

---

### Post by StGeorge on 2007-12-22
I might be wrong but I thought Ubuntu and NTFS don't nix.
I have My XP on NTFS and my file storage on Fat32 on my Laptop. Just the 1 HD.
Linux is at the beginning of the 1st Logical Partition, with FAT32 Partitions afterwards for all file storing.
Ubuntu likes Fat32.
I have a Fat32 98SE OS on a 10GB Hard drive.
Another HD with Ubuntu, then Fat32 partitions following that on my 2nd Hard Drive, on my desktop.
Ubuntu sees all.

---

### Post by StGeorge on 2007-12-22
One other thing.
I installed Windows OS's first.
When Ubuntu is installed it looks for other drives and OS's.
Therefore if you want XP, 98SE and Ubuntu then install the windows OS's 1st.

---

### Post by iamclueless on 2007-12-22
> **StGeorge said:**
> One other thing.
I installed Windows OS's first.
When Ubuntu is installed it looks for other drives and OS's.
Therefore if you want XP, 98SE and Ubuntu then install the windows OS's 1st.

yup i installed xubuntu second on a second separate HD

yup i know linux and nfts dont mix without loading up some add-on. my C:\ drive is NFTS i DONT want to access it so thats fine.  the D:\ drive si FAT32... id like to use it regularly from Xubuntu

---

### Post by jken146 on 2007-12-22
As of Gutsy, there is built-in NTFS read and write support.  NTFS and Linux don't match only in that you can't install a Linux distro on an NTFS partition.

---

### Post by StGeorge on 2007-12-22
Well there is the reason to give Windows the BOOT.
I Beleive FAT32 is the best windows format as it can be manipulated unlike NTFS.
I can recover formatted drives.
I can let another OS see it and I can safely delete anything I want to permanent if I so choose.
NTFS is a waste of space.
Plus alot of work.
Merry Christmas everybody.

---

### Post by iamclueless on 2007-12-22
> **jken146 said:**
> edit:  My previous suggestion wasn't so newbie-friendly perhaps.  Try [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows).

thanks man.. i like that site actually.
but my fstab file does not seem to have the windows drives there at all

heres my fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2388    19181578+  83  Linux
/dev/hda2            2389        2498      883575    5  Extended
/dev/hda5            2389        2498      883543+  82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20520493056 bytes
16 heads, 63 sectors/track, 39761 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x3f1a3f19

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10392     5237158+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2           10392       39761    14802354    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hdb5           10392       39761    14802322+   b  W95 FAT32


so it looks like my Windows is hdb1, hdb2, hdb5
i have no idea why there is an hdb2 and hdb5... maybe i never reformatted the D:\ drive when i moved from win95 on to 2000 and to XP. who knows

here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dfe21175-02cc-4376-980f-5c0e7271ec10 /               ext3    defaults,erro$
# /dev/hda5
UUID=9165bb8a-c610-4dfd-932f-5b44751b2ee1 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


i dont see my windows partitions.
i see my other IDE devices... which i cant mount either actually. :(

whats next then?

---

### Post by logos34 on 2007-12-22
> **iamclueless said:**
> 
whats next then?

It's all in the psychocats link.  You want to make a mount point and add a line for hdb5 ('vfat') to fstab...no entry needed for hdb2, that's the extended, or 'container' as it were for logical partition hdb5

---

### Post by dcstar on 2007-12-22
> **iamclueless said:**
> 
.........
i dont see my windows partitions.
i see my other IDE devices... which i cant mount either actually. :(

whats next then?

Install the **pysdm** package, then System-Administration-Storage Device Manager and it will automagically add in the fstab entries when you use it.

---

### Post by iamclueless on 2007-12-22
awesome!

i went with the psydm and created it.  then checked fstab to see the change.

im starting to get this.  i obviously didnt really need psydm... but the GUI makes life easy... but its nothing you cant do from the terminal.  thanks to the last two posts!!!!!!

ok now time to mount my CD and CDRW drives... i imagine it also involves creating mounting points

---

### Post by kool_kat_os on 2007-12-22
huh?

---

### Post by iamclueless on 2007-12-22
> **kool_kat_os said:**
> huh?

im trying to mount my CD and CDRW

---

