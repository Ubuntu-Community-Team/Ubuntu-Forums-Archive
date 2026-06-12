---
title: "Grub error 17 on dual boot machine"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Jchord.b on 2007-02-19
Hello All!!

Well I have a machine that I set up with xp and ubuntu 6.10 there are two harddrives one sata 120gb and one sata 80gb. well I installed xp on the pirmary 120gb and then i installed ubuntu on the secondary 80gb with grub on the 120bg everthing worked fine on both opperating systems untill I started to do the updates on the xp so i can use it for games (that is all it's good for) after a few reboots i finialy got to the pre sp1 updates and after they installed all i get is this error 17. :confused: :mad: :mad: so ya... i need help cause i don't want to reinstall xp and ubuntu and if left on my own that's what im gona do. :(

if it helps the harddrives are going through my mobo's sis 964

---

### Post by dbbolton on 2007-02-19
check here [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

---

### Post by poohbear1616 on 2007-02-19
Might also try this link. It tells how to reinstall grub from live disk....which is (imho) opinion your easiest fix.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

### Post by Jchord.b on 2007-02-19
all I got from that was:

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

but I still have no clue how to fix that!!

---

### Post by Jchord.b on 2007-02-19
> **poohbear1616 said:**
> Might also try this link. It tells how to reinstall grub from live disk....which is (imho) opinion your easiest fix.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

i will try that

---

### Post by Jchord.b on 2007-02-19
well i tried that and it worked (grub its self is fine) bit still get the error 17 so I guess that is:

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What can i do to fix it?

---

### Post by Jchord.b on 2007-02-20
bump

---

### Post by mikewhatever on 2007-02-20
If I understand correctly, you get GRUB error 17 when trying to boot Windows. Can you post the output of the two commands:
sudo fdisk -lu
sudo gedit /boot/grub/menu.lst

---

### Post by Jchord.b on 2007-02-20
no I get that error at stage 1.5 so I never see the boot list list but I will do that and post the output. (from the live cd)

---

### Post by Jchord.b on 2007-02-20
All this was done from the live cd.

```
sudo fdisk -lu
```

Makes

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   150239879    75119908+  83  Linux
/dev/sdb2       150239880   156296384     3028252+   5  Extended
/dev/sdb5       150239943   156296384     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 163.9 GB, 163927556096 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320171008 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   320143319   160071628+   7  HPFS/NTFS

```


```
sudo gedit /boot/grub/menu.lst
```

opens an empty file

and when go to /boot there is 5 files and no folders.

---

### Post by Jimcanoa on 2007-02-20
I have the exact same problem as Jchord. I've been playing around with Super Grub Disk and it permits you to boot from any bootable partition in your system, and I have managed to succesfully boot from the XP partition, but whenever I try to boot from Ubuntu it gives me an error message saying that it is unable to boot from that partition. I wonder if the problem lies with a faulty formatting of the partition (altho I've tried 3 times!), any ideas on how could that be checked?

When I boot from my Ubuntu 6.10 LiveCD! the directory /boot/grub doesn't exist, so evidently I cannot find menu.lst. The installation of Ubuntu doesn't give me any errors and I already have installed Ubuntu on another computer with the very same CD.

Thanks for the help! I'm about to start banging my head against the wall!!

---

### Post by urk_nono on 2007-02-20
When I booted up my comp and tried to enter Ubuntu from the dual-boot window it read as usual.

What I did, I entered command-line by pressing "c" over Ubuntu in the dual-boot window, and entered:

root (hd0,5) (You have to find out which partition your Ubunutu is installed at)
setup (hd0,5)

instead of reboot, I simply pressed "esc" untill I got back into the dual-boot window, and pushed "enter" over Ubuntu. That worked for me..

---

### Post by Jchord.b on 2007-02-20
well it turns out my problem was caused by grub reading every drive and my external was going bad so i unplugged it and it works. so for me the problem is solved.

---

### Post by mikewhatever on 2007-02-20
You don't seem to have GRUB installed on you Ubuntu partition (dev/sdb1). When reinstalling GRUB as shown in the link above, did you get any output to this grub> find /boot/grub/stage1? It should have been (hd1,0). How do you know that GRUB is fine?

---

### Post by Jimcanoa on 2007-02-21
mikewhatever, I have managed to boot the ubuntu partition by going into the command-line of Super Grub List and telling it to boot the system in (hd1,0), so now I know Linux works. If i get into the grub console, and execute your command it says:

```
grub> find /boot/grub/stage1
 (hd1,0)
```

So I believe GRUB is indeed correctly installed to the MBR.

Anyways, since GRUB wasn't working and I wasn't getting anything new from it, I tried to install Lilo, and this is what I got:

```
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.
    
    WARNING!
        Your /etc/fstab configuration file gives device UUID=8501e683-195d-433d-87da-5db91fc88fbb as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle. 

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

```

This is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=8501e683-195d-433d-87da-5db91fc88fbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=08D052EED052E20C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hde1
UUID=C2A412AEA412A547 /media/hde1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdf1
UUID=208C9CCA8C9C9BBA /media/hdf1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdg1
UUID=FCCCEB91CCEB450C /media/hdg1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=78488AF8488AB502 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=44387680387670B2 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=04506ED1506EC94E /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=1fabe0e4-bbcd-4f24-89d5-99b15fec3bb6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by confused57 on 2007-02-21
If you still have grub installed to your mbr & get a grub menu at bootup, you could try highlighting the Ubuntu entry, press "e" to edit, see if the line with root is pointing to (hd1,0)...if not, then change it, press "b" to boot...if you can successfully boot to Ubuntu, you'd need to make it permanent in your /boot/grub/menu.lst.
Added:  I should have mentioned earlier, since this isn't permanent, you can experiment & try different root (hdx,x) & find which one works.

Since you're able to boot Ubuntu with SGD, just open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list.


Grub can always be reinstalled with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by Jimcanoa on 2007-02-22
OK, so I've almost tried everything that I've seen out there but I still can't manage to boot the Ubuntu.

I have executed the command:
```
# grub-install hd1
```

and after that (if I set the BIOS to boot from hd1) I can finally see the GRUB OS select menu. But, if I select Ubuntu it says: "Error 17: Cannot mount selected partition"
If I press 'c' so I can enter the grub console and I type:
```
grub> configfile (hd1,0)/[TAB] 
Error 17: Cannot mount selected partition
grub> configfile (hd1,0)/boot/grub/menu.lst
Error 17: Cannot mount selected partition
```
But the weirdest thing is that if I boot from my Super GRUB Disk, I press 'c' so I can get into the GRUB console. I enter the same command as before
```
grub> configfile (hd1,0)/boot/grub/menu.lst
```
I can access the menu and if I tell it to boot, it actually works!

Does anyone know why this could be? Is there a way to set the partition as bootable so I can boot directly to it selecting the correct HD in the BIOS? Erasing GRUB from the MBR and all? That will do, I will principally use Ubuntu, and I don't care if I have to enter the BIOS to boot XP.

thanks!

---

### Post by Jimcanoa on 2007-02-22
I finally managed to make it work!!! I got my solution from

[http://www.ubuntuforums.org/showthread.php?p=2193575#post2193575](http://www.ubuntuforums.org/showthread.php?p=2193575#post2193575)

I hope this will help to future generations  of  **GRUB Error 17 Royal Club**

Thanks to everyone!

---

### Post by mikewhatever on 2007-02-22
Thanks for the update and glad you could solve it:)

---

