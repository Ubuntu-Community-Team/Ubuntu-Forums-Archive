---
title: "Accessing NTFS drive"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by unwoken on 2005-11-08
Hello,

First post!

My apologies as i know this question has been asked before, but i have tried a number of possible solutions and none seem to be working.

FYI i am dual booting from seperate hard drives (XP and Ubuntu).

I've never used Linux or Ubuntu before, and have been checking these forums for ~6 weeks reading as much as i can (here and elsewhere).  I finally installed with my new 12mbit connection, and the Install went perfectly! Unfortunately i am having no success with my first attempt at doing anything! :( 

so anyway, i will give what info i can, forgive me if some is not relevent. (ubuntuguide has been followed).

'fdisk -l' looks like this:

anubis@cynopolis:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         243     1951866    5  Extended
/dev/hdb2             244        2067    14651280   83  Linux
/dev/hdb3            2068        9729    61545015   83  Linux
/dev/hdb5               1         243     1951834+  82  Linux swap / Solaris

Disk /dev/hdd: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2490    20000893+   c  W95 FAT32 (LBA)

........

'mount' looks like this:

anubis@cynopolis:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hdb3 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hdd1 on /media/hdd1 type vfat (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
anubis@cynopolis:~$

.........

'fstab' looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                /proc           proc    defaults        0       0
/dev/hdb2       /                        ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home               ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdd1       /media/hdd1     vfat    defaults        0       0
/dev/hdb5       none                 swap    sw              0       0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0          /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

........

if i try to mount the drive (for this session(?)) this happens:

anubis@cynopolis:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1

..........

and finally, when i click on the icon for hda1 (on the desktop) i get this message:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "hda1".

Other attempts to access the drive also fail.

..........

what does this all mean?  i have tried rebooting, and get a message that mounting local drives failed (or something to that effect).

do i not have permission to access the drive?  if that is the case, can anyone tell me how i can get it?  i am willing to try pretty much anything given instruction (no previous history with command line although have some past DOS history).

thanks for reading, hopefully there is a simple answer and somebody can point me on the way to a windows free life!

cheers,
u.

---

### Post by jdong on 2005-11-08
/dev/hda1 needs **user,noauto** option in fstab. Note that you've declared /dev/hda1 twice in /etc/fstab. That's not allowed. Make up your mind :)

---

### Post by unwoken on 2005-11-08
[QUOTE=jdong]/dev/hda1 needs **user,noauto** option in fstab. Note that you've declared /dev/hda1 twice in /etc/fstab. That's not allowed. Make up your mind :)[/QUOTE]


thanks jdong, i will give it a go.

btw all i did was add the last line as instructed by the ubuntu guide when i could not access the drive.  the first line was already there (i assume??).

i will just delete the line i inserted then, and will try what you suggested.

thanks!

---

### Post by jdong on 2005-11-08
Try:

(1) Deleting that latter entry and adding the options to mine, or

(2) Deleting your first entry and just using the Guide's


Both should work well. When you have duplicate entries, the first one takes precedence in fstab. Your first entry mounts the hard drive with root permissions. My additions will mount the drive with the permissions of the user issuing the mount request. The Guide's solution mounts the drive as root, but with a restricted permission set. As you can see, both solutions would work well, if they're given the chance to work their magic :)

---

### Post by unwoken on 2005-11-08
don't know if you're still there jdong, but something seems to be wrong.

this is now fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,user,noauto       0       0
/dev/hdd1       /media/hdd1     vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

.....

did i add your lines in the right place?  i left the defaults part, put ',user,noauto'
after that, and deleted the line from the ubuntu guide.

when i rebooted, i did not get the error message about failing to mount local drives, but i have obviously done something wrong.

can you help?

---

### Post by jdong on 2005-11-08
Remove defaults... sorry, I totally forgot about that. defaults conflicts most additional options!

---

### Post by unwoken on 2005-11-08
thank you so much, i now have access to my windows drive. :D :D 

just as a test i copied a jpg file and pasted it onto the destop.  It appears to only have read and execute properties.  I can 'check' the 'write' box in permissions (of properties), but is this normal?  If i copy any file and paste from NTFS to my ext3 drives, will they remain unwritable until i change this option?

i understand that my NTFS drive is unwritable under my current setup, and this is the way i would prefer it, but i assumed that pasting a compatible file into my ext3 drives would automatically give me full access.

it's not a big deal, just curious.

thanks again, i am eternally grateful :D :razz: 

regards,
u.

---

### Post by jdong on 2005-11-08
Add **rw** to the list of options :)

---

