---
title: "One more reason I have to keep windoze"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-04-27
Ubuntu only recognises my 1gb sd card as read only? I copied some data to it all ok this morning, plugged it back in this afternoon and all folders are locked.  I cannot change any permissions as it says the card is read only.  I know it is not the lock messed up as windoze reads and rights to the card perfectly.  If i stick another sd card into Ubuntu it reads that fine.  It is just an issue with one card, that ubuntu used to read/write to perfectly.  
Anybody come across this, any ideas?

I was sooo close to ditching windoze, but there always seems to be another thing crop up.

---

### Post by taurus on 2007-04-27
What filesystem is on that drive?  If it's ntfs, then you need to use ntfs-3g driver to read and write to it.  But if it's fat32/vfat, then you just remount it with write permission for yourself.

---

### Post by YolaGP on 2007-04-27
You have to install the ntfs-3g driver.  Type **ntfs** in the search box of the Synaptic installer (sorry, I don't remember the exact name in English) and you can download a tool for managing ntfs.  That tool lets you enable read-write for all your internal and external drives.

---

### Post by n00blar on 2007-04-27
Are these drivers fully functional now? Last time I read about these, those drivers were early beta still and some people were reporting lots of bugs.

---

### Post by whee on 2007-04-27
> **n00blar said:**
> Are these drivers fully functional now? Last time I read about these, those drivers were early beta still and some people were reporting lots of bugs.

They are no longer beta and are final now. I've been using them for a while now without any problems. You can find ntfs-3g in the Add/Remove applications list.

PS: We're not sure yet if his SD card uses NTFS.

---

### Post by Campingman on 2007-04-27
I have been away from the PC apologies.  
It is FAT16.  Ubuntu has written to it numerous times in the past.  I transferred a file earlier on today, unplugged it,  put it my pda for a while, back in the card reader and then it is suddenly read only?

---

### Post by locke.dragon on 2007-04-27
if you plug it into a windows computer, you have to unmount it safely using the little icon in the taskbar.  i have the same problem with some of my cards.  plug it back in to windows, safely disconnect it (right click on icon, select device, safely remove hardware) and then see if it works in ubuntu.

---

### Post by Campingman on 2007-04-27
> **locke.dragon said:**
> if you plug it into a windows computer, you have to unmount it safely using the little icon in the taskbar.  i have the same problem with some of my cards.  plug it back in to windows, safely disconnect it (right click on icon, select device, safely remove hardware) and then see if it works in ubuntu.

No joy with that one, still read only. 
Ubuntu will not let me change read/write permissions as it tells me the drive is read only?
Windoze reads/writes OK

---

### Post by locke.dragon on 2007-04-27
just another quick suggestion.  you could try it using root.

```

sudo -i

```

that might work.  just make sure you leave open the terminal you typed that into while you're doing it, once you close that terminal, you'll go back to having your regular privileges.

---

### Post by anaconda on 2007-04-27
what if you try with root rights.
if you start nautilus from terminal:
```
sudo nautilus
```

do you have rw-rights then?

---

### Post by Campingman on 2007-04-27
Hi 
I have tried it with sudo nautilus and still get the same message
Couldn't change the permissions of "disk" because it is on a read-only disk
I can take things off the disk but cannot write to it.
The most annoying thing is that it worked perfectly earlier and all that has happened is that it has been removed and replaced.  
I have another sd card which ubuntu mounts with the correct permissions straight away (using the same card reader).

---

### Post by locke.dragon on 2007-04-27
INCONCEIVABLE!!!  the last thing i have to offer.  have you checked to see if the "lock" switch is turned on on the memory card (it's actually ON the memory card).  mine sometimes switches itself into lock mode when i hook it up to my computer or wii (something hits the switch as i push it in).  try putting a little piece of see-through scotch tape over the switch and see if that works.  it sounds dumb, but it's worth a try!  ;)

---

### Post by Campingman on 2007-04-27
The switch seems to be OK, I have tried it in both positions and I guess if it was screwed up windoze would not be able to write to it.  I am contemplating backing it up and reformatting to see if that does any good but do not really want to go that far as it has all my sat nav and pda programs on it.  I will have a play later when I have more time, thanks for all your suggestions.

---

### Post by kelvin spratt on 2007-04-27
i had the same problem with a usb pen drive that i unplugged the wrong way but if i left it connected and rebooted the read write permissions were ok so i reformatted the pen drive then it was ok had the same prob in xp after using sd card to flash upgrade my video camera had to use my wifes comp to unlock the card it most be some sort of protection in the comp/card to stop it being damaged

---

### Post by locke.dragon on 2007-04-27
not to be rude or anything kelvin, but it helps us ALOT if you at least use proper punctuation.  i'm not a stickler for capitalization as you can see, but PLEASE use commas, periods, exclamation points, question marks...  it'll help everyone. ;)

---

### Post by theredcross on 2007-04-27
```
sudo /sbin/fdisk -l
```
while its plugged in, it should read as an SDA i believe. then,
```
sudo gedit /etc/fstab
```
check for the entry matching the fdisk output, and if you don't understand whats going on in there just post that line, that may afford more clues.

---

### Post by Campingman on 2007-04-27
Well, I booted into windoze, backed the card up, formatted to FAT and then back into Ubuntu, no change "read only".  It is shown as sda1
 on list
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12756   102462538+   7  HPFS/NTFS
/dev/hdb2           15333       15459     1020127+  82  Linux swap / Solaris
/dev/hdb3           15460       19457    32113935   83  Linux
/dev/hdb4           12757       15332    20691720    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              21      167680     1005958+   b  W95 FAT32
dazza@dazza-desktop:~$ sudo gedit /etc/fstab
GTK Accessibility Module initialized

But I cannot see it on fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=1ca31312-1862-44b3-bce1-caca0505c123 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=901409A314098E02 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=B4C88A00C889C15A /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb4
UUID=45FD-9A4E  /media/hdb4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=0c25c699-84dd-4df9-893d-179289e9a4f8 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Should it be in fstab as it does not mount on booting up?

---

### Post by compmodder26 on 2007-04-27
In Ubuntu, with the drive plugged in, give us the output of "cat /etc/mtab"

---

### Post by Campingman on 2007-04-27
> **compmodder26 said:**
> In Ubuntu, with the drive plugged in, give us the output of "cat /etc/mtab"
Here goes

/dev/hdb3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/hdb1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb4 /media/hdb4 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk vfat ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

---

### Post by compmodder26 on 2007-04-27
Okay, try these two commands:

```
sudo umount /media/disk
sudo mount -t vfat -o rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 /dev/sda1 /media/disk
```

Note, if this works it isn't a permanent solution.  It would have to be done every time you plug the drive in.  I'll have to get back with a permanent solution as soon as I can find one.

---

### Post by Campingman on 2007-04-27
I get this output

mount: mount point /media/disk does not exist

---

### Post by compmodder26 on 2007-04-27
Oh yeah, I forgot that Ubuntu is asigning a virtual mount point for it.  Create a directory under /media for the drive.  Call it whatever you want.  Then change /media/disk in the command I gave you to /media/name_of_the_directory_you_created

---

### Post by zenkaon on 2007-04-27
Why don't you go into windoze and format the SD card as fat32. Then everything should be able to read/write/execute on it. Fat32 doesn't have any permissions, whoever mounts it owns it.

---

### Post by saadakhtar on 2007-04-27
simply goto "Home" and in "media" look for the appropriate name assigned to the memory card drive.
now in terminal do the following:

Here i am assuming that your drive is called "sda1"

type in

sudo -s
enter root password
chown /media/sda1

now

chmod 777 /media/sda1
chmod 777 /media/sda1/*

and hopefully you should see some progress.

please post results.

---

### Post by Campingman on 2007-04-27
> **zenkaon said:**
> Why don't you go into windoze and format the SD card as fat32. Then everything should be able to read/write/execute on it. Fat32 doesn't have any permissions, whoever mounts it owns it.

Did that, no good

---

### Post by compmodder26 on 2007-04-27
> **saadakhtar said:**
> simply goto "Home" and in "media" look for the appropriate name assigned to the memory card drive.
now in terminal do the following:

Here i am assuming that your drive is called "sda1"

type in

sudo -s
enter root password
chown /media/sda1

now

chmod 777 /media/sda1
chmod 777 /media/sda1/*

and hopefully you should see some progress.

please post results.

I don't think that would work.  The problem is that the drive is being mounted as read only.  It doesn't have anything to do with the permissions of the files and folders on it.

---

### Post by Campingman on 2007-04-27
I guess it just does not want to play today:

mount: block device /dev/sda1 is write-protected, mounting read-only


I guess I will just have to use windoze with this card

---

### Post by compmodder26 on 2007-04-27
Hmm... only other thing I can think of is to re-format in Ubuntu.  I can't remember the command line way to do this.  But you can install gparted and re-format the drive in there.

edit:  Are you sure that the write-protect switch isn't flipped?

---

### Post by locke.dragon on 2007-04-27
gparted is installed by default

---

### Post by compmodder26 on 2007-04-27
> **locke.dragon said:**
> gparted is installed by default

Odd, it isn't on my install.

---

### Post by Campingman on 2007-04-27
> **compmodder26 said:**
> Hmm... only other thing I can think of is to re-format in Ubuntu.  I can't remember the command line way to do this.  But you can install gparted and re-format the drive in there.

edit:  Are you sure that the write-protect switch isn't flipped?

My thoughts exactly,
I came back to post the resolution and you had already posted it!  I decided to try and reformat in Ubuntu (I had previously formatted to FAT32 in windoze with no luck).  Installed Gparted and expected it to return a similar error when trying to format.  It mounted sda1 ok formatted it and hey presto there it was full read/write permissions.
I need to change the thread title to one more reason to ditch Windoze.

Thanks all, I would have been stuck without you

---

### Post by locke.dragon on 2007-04-27
good job figuring it out!

---

### Post by compmodder26 on 2007-04-27
Glad you were able to get it sorted.

---

### Post by xpod on 2007-04-27
> gparted is installed by default

gparted is only on the live cd and once you`ve installed Ubuntu you need to  install gparted if you want to use it:)

---

### Post by Josey on 2007-04-27
heh read the whole thread as it seemed pretty strange so just wanted to add my congratulations on figuring it out.  :)

---

### Post by Campingman on 2007-04-27
Funny thing is I have completely forgotten why I wanted to write to it in the first place!!  The brain cells are going far too quick these days.
Could someone let me know how to mark a thread resolved, I cannot see how to do it.

---

### Post by Josey on 2007-04-27
edit your first post - click 'go advanced' - there you can edit title  

add (resolved) somewhere

---

### Post by Campingman on 2007-04-27
Cool, Thanks

---

