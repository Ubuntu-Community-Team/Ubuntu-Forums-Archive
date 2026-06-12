---
title: "Grub does not load"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by methosb on 2006-06-09
Hi I am absolutely new to linux. I was running XP and decided to dual boot Ubuntu Dapper. Both OSs are on the same drive but whenever my computer boots grub does not start up, it just boots straight into windows. I can get into Ubuntu if I boot from the cd and choose "Boot first hard disk" though, this starts grub up so it is definitely installed and from there I can choose the OS I want.

Here are the contents of my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hde1       /media/hde1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdf1       /media/hdf1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hde3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is what I get when I do 'df':
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hde2              6040320   2638332   3095148  47% /
varrun                  257508       124    257384   1% /var/run
varlock                 257508         4    257504   1% /var/lock
udev                    257508       188    257320   1% /dev
devshm                  257508         0    257508   0% /dev/shm
lrm                     257508     18324    239184   8% /lib/modules/2.6.15-23-k7/volatile
/dev/hda5             29302528  29164140    138388 100% /media/hda5
/dev/hde1             51448124  48094296   3353828  94% /media/hde1
/dev/hdf1            156288320 147768312   8520008  95% /media/hdf1
/dev/hdd                714594    714594         0 100% /media/cdrom0

```

hde1 would by the partition with Windows and hde2 would be Ubuntu.

Hope someone can help me with this, I hope these lists are of some help.

---

### Post by steve.horsley on 2006-06-09
Can I assume that windows is on the disk /dev/hda? If not, please post the output from:
**sudo fdisk -l**
And maybe explain how you come to have so many drives?

If my guess is right:
Take a backup of your windows partition with the command:
**sudo dd if=/dev/hda of=/boot/BOOTPART_A bs=512 count=1**
then try to install grub on /dev/hda:
**sudo grub-install /dev/hda**

If hda goes titsup you can replace the bootsector with 
**sudo dd if=/boot/BOOTPART_A of=/dev/hda**

I have to warn you I'm a little uncertain of this because of the huge number of disks and partitions you seem to have.

---

### Post by methosb on 2006-06-09
Ok just ignore /dev/hda5, /dev/hdf1, /dev/hdd  those are all seperate storage hard drives or cdrom

/dev/hde1 = windows
/dev/hde2 = linux
They are dual booted on the same hard drive that has 3 partitions (1 for windows, 1 for linux, 1 for linux swap). I think when you run that command the windows one is supposed to come up as /boot right?

I don't know what all the other stuff is just some linux stuff I am guessing.

Here are the results from the sudo fdisk -l:
```

Disk /dev/hde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        6405    51448131    7  HPFS/NTFS
/dev/hde2            6406        7169     6136830   83  Linux
/dev/hde3            7170        7297     1028160   82  Linux swap / Solaris

Disk /dev/hdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        3649    29302560    f  W95 Ext'd (LBA)
/dev/hda5               2        3649    29302528+   7  HPFS/NTFS

```

---

### Post by methosb on 2006-06-10
bump

---

### Post by steve.horsley on 2006-06-10
So "boot from first hard drive" on the installer CD boots from /dev/hde, or from /dev/hda? I wonder. 

I wonder if Linux is putting grub on hda but for some reason the BIOS is booting from hde. Maybe **sudo grub-install /dev/hde** would do the trick. Again, back up the bootsector first.

---

### Post by methosb on 2006-06-10
can't see any files on hda for it and there are grub files in hde I have no idea why it boots straight to windows

---

### Post by methosb on 2006-06-10
bump again

---

### Post by catlett on 2006-06-10
Did you run  ```
sudo grub-install /dev/hda
``` as previously suggested? What happens when you reboot?
You can do something quickly that won't touch any partition. ```
sudo update-grub
``` This just runs a grub update. Hopefully it will replace what's missing.
To put grub on the MBR when your not sure which drive it is, you can run the install with the grub specific labeling. ```
sudo grub-install (hd0,0)
```

Before you do anything you might want to check and make sure your grub menu entries match up with your partition setup.
Call up your grub menu with ```
sudo gedit /boot/grub/menu.lst
``` You already know how to get your partitions with fdisk -l.
Grub uses 0 as a value. So if ubuntu is an /dev/hda3 then grub lists it as (hd0,2). Drives are 0,1,2 in grub but a,b,c in linux. Partitions are 0,1,2  in grub but 1,2,3 in linux.


For an in depth guide an explanation of grub go here [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by drtvasudevan on 2006-06-10
[QUOTE=steve.horsley]So "boot from first hard drive" on the installer CD boots from /dev/hde, or from /dev/hda? I wonder. 

I wonder if Linux is putting grub on hda but for some reason the BIOS is booting from hde. Maybe **sudo grub-install /dev/hde** would do the trick. Again, back up the bootsector first.[/QUOTE]

right.
linux will put the grub in the mbr of hda. it can not be "seen"
if bios setting is to boot from hde it will do so.
look at the bios settings.

tv

---

### Post by methosb on 2006-06-12
Ok none of those commands made a difference. I didn't think it would because /dev/hda is merely a storage drive with nothing but mp3s on it. I have set up my bios so it boots the OS drive first then the cdrom and nothing else. Every time it boots to windows.

Though, when I did the grub install to /dev/hda and hd0,0 it listed the hard drives as:
(hd0) /dev/hda
(hd1) /dev/hde
(hd2) /dev/hdf

This makes the partition setup in menu.lst correct. I don't know what effect it would have on the boot menu.

Here is my menu.lst after all the commented out stuff at the top:
```

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

The 2nd and 3rd last lines are odd right? I don't want to fiddle with it until someone tells me what that is and if I can remove it or whatever.

---

### Post by catlett on 2006-06-12
Did you switch your hard drives around after install? This grub menu is for Ubuntu being the master and Windows being the slave. If you put wundows as the master and ubuntu the slave then you would have the situation you are having.
This appears to be the problem. Windows' hard drive is booting first. It doesn't have grub on it so it cant' load grub. When you choose Ubuntu's hard drive it loads grub because it is on that drive.
For some reason windows is acting like the master. Either you switched them back after install or your bios has the windows drive first and ubuntu second in it's booting order.

---

### Post by drtvasudevan on 2006-06-12
there is nothing wrong with the grub.

mbr is the first 63 sectors of the hard disk and this can not be seen by us though programs can write into that.

what you are seeing is the copy of the grub list in the mbr.
but it is in the hda mbr.
you have set the bios to boot from hde.
so naturally it boots to windows.
install grub in hde and it will boot from grub

tv

---

### Post by methosb on 2006-06-12
k, I installed in grub into hde and yes it booted to grub, so it must have been installed onto hda.

Then when I tried to boot Linux it said that the partition did not exist, this was with the menu.lst posted on the previous page so the linux partition was root (hd1,1) which is correct. This is also what is listed when I boot from cd (which it would seem calls up grub from the mbr of hda) and this works.

So I figured out that I believe that grub assumes that which ever hard drive it is being called from is infact hard drive 0. So I set the menu.lst with linux as root (hd0,1) and Windows is not (hd0,0). Viola! Linux boots.

BUT!!

Now Windows will still not boot like this. Now when Windows is set to (hd0,0) it comes up saying:
```

root  (hd0,0)
  Filesystem type unknown partition type 0x7
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

NTLDR is missing

```

I tried changing Windows to root (hd1,0), this did not help. I tried setting it to rootnoverify (hd0,0), this did not help. I saw other threads about this Windows issue that said to set the hard drive to type "LBA", but they already are. Others said to try setting the type to "Large" but the bios I have is American Megatrends Dual Bios, and the OS drive is on the ATA133 sockets and hence is not in the first bios, and in the second bios there are no settings for drive type.

EDIT: Yay I can boot windows now! I removed the two lines
```

map		(hd0) (hd1)
map		(hd1) (hd0)

```
and now it works for some reason. Thanks for your help guys. Now if I could only get dvd menus in mplayer and plugins in opera...the battle rages on!

---

### Post by catlett on 2006-06-12
Great,Great,Great.:D 
Now to your other issues. I follow this guide after I install and I get everything I need [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)  But when it comes to mplayer and some other multimedia I go back to Ubuntu's roots. Meaning I use Debian Sid's multimedia repo.
As I'm sure you know Ubuntu is Debian  based so the sid multimedia repo works nicely with Ubuntu. The only thing is sometimes the new aplications are way ahead and it causes an issue with synaptic and apt-get. Every now and again I'l have a dependency issue. All I do is run aptitude and it fixes everything. Every time  the problem was resovled by Aptitude holding a package at it's current version. (so if there is an issue a sudo aptitude upgrade has resolved it)
Here is the repository I use for mplayer   > deb [http://www.debian-multimedia.org ](http://www.debian-multimedia.org ) sid main   Here is the web site in case your curious [http://hpisi.nerim.net/](http://hpisi.nerim.net/)

---

### Post by methosb on 2006-06-13
hrmm I have just read on here that mplayer cannot do dvd menus, is that correct? 

I would use VLC but I can't get wmv/real vids to work in it even though they work in everything else, and subtitles look absolutely disgusting in VLC and can be hard to read because of their chunkyness. On the subtitles note, I also can't get mplayer to load .sub/.idx subtitles, only .srt

I really don't like having to use multiple video players.

---

