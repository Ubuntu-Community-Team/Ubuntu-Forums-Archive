---
title: "ntldr"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by harshasunder on 2007-06-11
hey,
i had an mbr problem on my comp , and so wrote on this forum for help. was told to put the win disk in and do fix mbr and fix boot. now after doing that, now im getting a different error message(earlier it was grub 17) which says NTLdr onot detected .whats do i do>?

---

### Post by deeteesbeard on 2007-06-11
Basically NTldr is a file that boots up Windows NT/2000/XP it's usually pointed to by the masster boot record, if it's missing windows can't boot.
Could you give a bit more detail of your situation please?
Such as...
How many disks/partitions do you have?
What operating systems are on the disks/partitions and where?
What caused your mbr problem as far as you can tell?

Ta

---

### Post by harshasunder on 2007-06-12
hey thanks for replying.Basically, i installed Ubuntu a few days ago and went along with the option which said ubuntu would automatically resize and install on a partition( while installing)  and the new partition was about 5.1 gb.Then when i restarted i got a grub 17 error.so i posted here ([http://ubuntuforums.org/showthread.php?t=464902](http://ubuntuforums.org/showthread.php?t=464902)) and was told to run fixmbr and fixboot.As far as I know Ive installed linux on hd0,2 .now about partitioning, i dont know lots, but i have one 40 gb hard disk, and it shows as two 20 gb ones in win xp, so i assume its partitioned into 2, and then there s this linux partition.I read somewhere that ([http://psychocats.net/ubuntu/installingdapperedgy](http://psychocats.net/ubuntu/installingdapperedgy)) while doing a dual installation you need to make the size of the partition zero which i didnt do. maybe thats what screwed up the mbr..
sorry if this sounds unclear.can you tellm e where to find out the other specific info if you need any?
thanks

---

### Post by logos34 on 2007-06-12
can you boot from the live cd and run
sudo fdisk -l

post it.  at least that'll show how your partitions are laid out.

While you're there you could just try reinstalling grub.

sudo grub 
find /boot/grub/stage1
(enter the output in place of 'y' on the next command)
root (hd0,y)
setup (hd0)
quit

---

### Post by harshasunder on 2007-06-12
hey this is what i got when i typed sudo fdisk -l (doesnt look promising to me)

""
Disk  /dev/hda : 40.0 GB 40020663240 bytes.
16 heads, 63 sectors/tracks, 77545 cylinders
Units = cylinders of 1008 x 512 = 516096 bytes

This doesnt look like a partition table.
Probably you selected the wrong device.

Device               Boot          Start                  End              Blocks               Id             System
/dev/hda1            ?             1854932         2022283       84344761          69           Unknown
Partition 1 does not end on cylinder boundary.

/dev/hda2          ?               1688016          3543057      93494073+         73            Unknown
Partition 2 does not end on cylinder boundary.

/dev/hda3           ?                   3                        3                   0                    74           Unknown
Partition 3 does not end on cylinder boundary.

/dev/hda4                                  1               3407851        1717556736           0          Empty
Partition 4 does not end on cylinder boundary.


Partition Table entries are not in order
""



Also when i try and do a grub install, when i type" find / ... " i get error message 15, no such file can be found.
but then i did an earlier fix mbr and fix boot no? so shouldnt all of ubuntu stuff on the mbr have gotten erased?  Earlier, before i did a fixmbr and fixboot when i typed find /boot/grub/stage1 i used to get (hda0,2)
Infact i tried to do a setup then itself but things didnt change and i still got an error message
hope this helps to help you help me
thanks

---

### Post by harshasunder on 2007-06-12
hey
i seem to have found out more about my problem.I googled 'missing ntldr' and found a site which said i could copy ntldr and ntdetect from the win xp cd to my harddisc which would fix the problem.This i did.But still the comp didnt work.then the site said check the boot.ini file as that is probably the problem.However, that file was missing on my comp! so then i tried to replace it with the command bootcfg/rebuild in the recovery console but i got the error message there- "Failed to successfully scan disks for Windows installations.This error may be caused by a corrupt file system which could prevent bootcfg from succesfully scanning.Use chkdsk to check for disk errors" . So then back again to the net, which told me to go to the win xp disk and do a repair install. so i did that and after the agreement screen i got this screen which i dot know what to do with-
 "the following list shows the partitioned and unpartitioned space ont his computer." then there are three options-
install xp on that partition
delete the partition
create a partition in the unpartitioned space (?)
and then theres a box which says
32252 MB Disc 0 at Id 0 on bus 0 on atapi [MBR]
C:/ partition 1  [FAT] 32254 MB <1 MB Free>

so now what do i do? can you infer whats on this partition somehow?can i delete it?
harsha

---

### Post by logos34 on 2007-06-12
Not sure I can make heads or tails of this, but it looks like any number of things went wrong:
-when specifying the size of the partitions in the ubuntu installer you did not tick the 'round to cylinders' box (so they do not end cleanly on boundaries--hence the fdisk errors)
-shrinking the windows partition corrupted the partition tables so you can't boot because ntldr can't find the path to boot.ini, etc. (which may still be there after all)
-the ubuntu install did not go very well (an understatement) so grub can't find root hda3

> "Failed to successfully scan disks for Windows installations.This error may be caused by a corrupt file system which could prevent bootcfg from succesfully scanning.Use chkdsk to check for disk errors"

Did you run chkdsk frm the recovery console?
**chkdsk /r**
OR
**chkdsk c:/r**

That's usually the first thing that happens immediately upon reboot into windows after installing ubuntu in which the windows ntfs partition has been resized.  That *might* fix things so at least you could do fixmbr again and be able to boot into windows.

> options-
install xp on that partition
delete the partition
create a partition in the unpartitioned space (?)
and then theres a box which says
**32252** MB Disc 0 at Id 0 on bus 0 on atapi [MBR]
C:/ partition 1 [FAT] 32254 MB <1 MB Free>

The size looks right: 37GB (actual disk size) minus the 5.1GB linux partition = ~32GB.  But the last line looks suspect.  And I don't know how to square that with this:

> and the new partition was about 5.1 gb.Then when i restarted i got a grub 17 error.so i posted here ([http://ubuntuforums.org/showthread.php?t=464902](http://ubuntuforums.org/showthread.php?t=464902)) and was told to run fixmbr and fixboot.As far as I know Ive installed linux on hd0,2 .now about partitioning, i dont know lots, but i have one 40 gb hard disk, and it **shows as two 20 gb ones in win xp, so i assume its partitioned into 2, and then there s this linux partition**.

Maybe you could select the repair "install XP on that partition" option...never done a repair install, but I assume it leaves My Documents files intact.  If not, your going to have try to reinstall ubuntu so you can access windows partition to back up your files. 

Or:
If chkdsk seems to fix the errors but you still can't boot into xp, use the live cd to see if you can correctly detect and mount windows partition.  Then you could backup your files to a usb flash drive.  Or else just go ahead and reinstall ubuntu and try to mount xp partition and save files to your home directory.

If on the other hand you don't care about losing whatever is on windows, do a fresh install of XP with full format (not quick) on a NTFS partition, leaving enough remaining disk space for your linux installation.  Delete all the partitions first, then carve out the NTFS partition and full format it.  That'll leave the remainder as raw/unallocated space.*  (which means when you install ubuntu you won't have to resize windows again and thus avoid problems). Next install ubuntu, creating out of the remianing disk space an ext3 root (/) and a 512mb -1GB swap partition (/swap).  

*you could also use gparted on the ubuntu live cd to first carve up and format the partitions for xp and linux, then do the installs.

Hope that helps.

EDIT: Another option is TestDisk to repair your windows partition, and SuperGrub for help in booting it.

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)  
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

