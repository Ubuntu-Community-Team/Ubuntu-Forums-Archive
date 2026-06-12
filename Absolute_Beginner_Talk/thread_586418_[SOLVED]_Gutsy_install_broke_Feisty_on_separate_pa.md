---
title: "[SOLVED] Gutsy install broke Feisty on separate partitions"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-10-22
[FONT="Comic Sans MS"]I've got Feisty on sda1, all my files on sda6, Gutsy on sda7. 
I can no longer access any but the home partition on either Feisty or Gutsy. Annoying to say the least.

At first Gutsy had some problems with gnome but it seems to have settled that now and in the process I lost access, first to my usb drives and now to my internal hdd's.

Feisty has this error at startup;
> fsck failed   unable to resolve UUID=33c8d809-711e-4eb9-abc4-90b55113286
exit status 8
> a maintenance shell will now be started
..blah blah, then 
> apt-get not installed
enter apt-get install apt

then>  root@backyard~#udevd-event[4106] waiting for /sys/device error -71

there is quite a bit more on this particular screen but these seemed to be the relevant things.

I enter [COLOR="Red"]/etc/init.d/gdm start[/COLOR] to get my screens and this error pops up > failed to initialize hal

I tried [COLOR="#ff0000"]apt-get install apt [/COLOR]but it said [COLOR="Magenta"]command not recognised[/COLOR][/FONT]

(the fsck failed on the UUID of sda7 - which is Gutsy)

I have partimage backups but they're on the partitions and usb drives I can't access!:confused:
I thought that having separate partitions would protect me from this.:(

[FONT="Comic Sans MS"]here is fdisk and fstab;[/FONT]
ramses@backyard:~$ sudo fdisk -l 
Password: 
Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
  Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1401    11253501   83  Linux 
/dev/sda2            1402       19452   144994657+   5  Extended 
/dev/sda5           19069       19452     3084480   82  Linux swap / Solaris 
/dev/sda6            2531       19068   132841453+  83  Linux 
/dev/sda7            1402        2530     9068629+  83  Linux 
Partition table entries are not in disk order 
Disk /dev/sdb: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
  Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       38913   312568641   83  Linux 
Disk /dev/sdc: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
  Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1       19457   156288321   83  Linux

# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1 
UUID=2f52b535-785c-4511-a105-bfb767f9e27d  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda6 
UUID=19e7639e-b0dc-472e-9426-ed049d7e12a9  /media/sda6    ext3         defaults                    0  2  
# /dev/sda7 
UUID=33c8d809-711e-4eb9-abc4-90b559113286  /media/sda7    ext3         defaults                    0  2  
# /dev/sdb1 
UUID=c2884395-5ced-483f-a151-2692073907f5  /media/sdb1    ext3         defaults                    0  2  
# /dev/sda5 
UUID=6a04acf7-931e-4581-b068-94cf598021ac  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sdc1                                  /media/sdc1    ext3         defaults                    0  0  

[FONT="Comic Sans MS"]Help! I've been trying to nut this out but my noodle is now knackered.[/FONT]
finally the log
 ;Log of fsck -C -R -A -a 
Mon Oct 22 17:16:52 2007

fsck 1.40-WIP (14-Nov-2006)
MainPartition: clean, 15325/16613376 files, 9230511/33210363 blocks
achilles: clean, 385/39075840 files, 38081672/78142160 blocks (check in 2 mounts)
fsck.ext3: Unable to resolve 'UUID=33c8d809-711e-4eb9-abc4-90b559113286'
fsck died with exit status 8

Mon Oct 22 17:16:52 2007

---

### Post by carloslosgrande on 2007-10-24
[FONT="Comic Sans MS"]To the Gutsy team - my apologies. My system wasn't broken by Gutsy but by systemrescue cd:(

Completely bust!:(:(

I lost all access even to the system setup, then even to the OS!

Did a reinstall of Gutsy and luckily had a copy of SuperGrubDisc to save the day!
I'm now setting up again. Only real casualty seems to be my second hdd.[/FONT]

---

