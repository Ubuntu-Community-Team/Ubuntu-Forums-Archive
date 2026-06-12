---
title: "I screwed up my partitions"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-19
I was trying to remove Kubuntu from a Ubuntu/Kubuntu dual install and deleted the extended and swap partitions for Ubuntu instead of Kubuntu. The Kubuntu extended and swap are still there. I am using the live cd to boot from the hard drive now. I get the Debian boot loader screen and can't catch everything, but see something about "trying to load pixellinux". It then goes to an Edubuntu load progress screen and hangs. I have never installed Edubuntu, so I guess that pic was hiding in some folder. The grub is working when I use the live cd.  Can I fix this screw up?

---

### Post by ajgreeny on 2007-03-19
Can we have a look at your partitions as they are at the moment, please.  Let's see what the output of 
sudo fdisk -l
in a terminal is and we can probably sort out the problem.  At the moment I'm a bit confused as to what you had and what you actually want to end up with.  Do you want just ubuntu and scrap kubuntu?  If so you don't really need to worry as you can add ubuntu-desktop to your kubuntu, and then get rid of kubuntu-desktop.

You will need to look for the command to use in a terminal to remove kubuntu-desktop, however, unless you installed it using aptitude, because apt-get or synaptic will only remove the meta-package and not all the programs as well.  You could reinstall the kubuntu-desktop using aptitude, and then uninstall it also using aptitude, as this will remove everything just reinstalled.

Incidentally, why did you separate your ubuntu and Kubuntu? You can just add either ubuntu-desktop to kubuntu, or kubuntu-desktop to ubuntu, and have both available on the one setup.  This is what I have with no problems at all.

---

### Post by zvacet on 2007-03-19
[http://www.psychocats.net/ubuntu/gnome]("http://www.psychocats.net/ubuntu/gnome")

---

### Post by 67GTA on 2007-03-19
This is a screen shot of my current partition:
[ATTACH]27856[/ATTACH]

Ubuntu is recognizing /dev/sda5 as my swap partition(sudo swap-s), but I do not know how to check the extended partition

History of events:
Changed grub to use Ubuntu 
Deleted Kubuntu root partition
Resized Ubuntu partition
Deleted Kubuntu swap
Resized extended so it fit back around sda5(was unallocated hole to left of sda5 where kubuntu swap was and the extended was around both the unallocated and sda5)

Could I have screwed up the extended partition?
Does it have anything to do with booting?

---

### Post by 67GTA on 2007-03-19
I was trying both out to see what I liked. I installed both seperatley from disc. I want to keep Ubuntu and have already deleted Kubuntu partitions. Everything was fine until I went back and deleted the Kubuntu swap and resized the extended partition. That is when Ubuntu stoped booting. 


shawnr@fastback:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10836    87040138+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

---

### Post by 67GTA on 2007-03-19
I am using Ubuntu now, I just have to use the live cd to boot from the hard drive. Grub shows all of my Ubuntu kernels and I can boot the system. It just will not boot on it's own.

---

### Post by ajgreeny on 2007-03-19
The extended partition sda2 is in effect just the virtual partition that contains swap sda5 (note they are both exactly the same size), so don't worry about the sda2, just deal with sda5.  You will also be able to set your current sda5 swap partition to be the one for ubuntu or kubuntu, but you may need to edit your fstab file to do that.  Can you post a copy of that file to see where you are at the moment, please, and what mounts at boot time.

What are you going to do with the 146.99 GB of unallocated space?  You could add it to your ubuntu partition or leave it separate as a storage partition, though you will need to make sure it is in your fstab file so it mounts at boot time and set  permissions so it is yours to write to as user.

---

### Post by ajgreeny on 2007-03-19
> **67GTA said:**
> I am using Ubuntu now, I just have to use the live cd to boot from the hard drive. Grub shows all of my Ubuntu kernels and I can boot the system. It just will not boot on it's own.

What happens when you try to boot from hard disk, do you get a grub error message of some sort?

---

### Post by 67GTA on 2007-03-19
I will probably install other OS's on the unallocated space, and maybe set up a seperate home partition once I get everything configured the way I want it. When I boot from the hard disc I see the debian bootloader screen and something about trying to load pixellinux, and then it goes to edubuntu load screen and hangs up.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0

---

### Post by 67GTA on 2007-03-19
When I try to mount sda2 I get this error:

shawnr@fastback:~$ sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

---

### Post by 67GTA on 2007-03-19
When I try to view mounted I get sda1 errors:

shawnr@fastback:~$ sudo mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-686/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by 67GTA on 2007-03-19
Sorry I posted the wrong fstab file earlier, I don't have any ntfs partitions! It is not listing sda2(extended). How do I tell Ubuntu to use and mount this at startup? Could this be cuasing the trouble?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by 67GTA on 2007-03-19
I am starting to think that the partition change has nothing to do with mt boot problem. The root and swap partitions are being used. The extended partition is busy(at least one logical partition mounted). I guess I will start combing through my boot files.

---

### Post by ajgreeny on 2007-03-19
OK.  Good luck too, I admit I'm out of my depth now and am rather baffled about where you go from here.

---

