---
title: "How to install gparted"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by sheki1 on 2008-01-31
I installed Ubuntu 7.10 in a dual-boot mode with Vista.

I made some system changes in Vista and want to make sure that Ubuntu sees my many partititons properly.  Unfortunately I cannot find gParted on the system.  I recall that when I was in the process of installing Ubuntu i could find gParted off the Admin menu.

Now it appears to be gone.  I'm looking at the Ubuntu CD for the program but I cannot seem to find it.

Any help would be greatly appreciated!

---

### Post by emarkd on 2008-01-31
There may not be a menu item.  Can you run it from the command line?

```
sudo gparted
```

Remember, you won't be able to modify live, mounted filesystems...

---

### Post by benfindlay on 2008-01-31
It doesn't get installed as far as I am aware, but is present on the live-cd as you need it for partitioning.

Juat launch a terminal and type ```
sudo apt-get install gparted
```
Hope this helps!

---

### Post by Fixman on 2008-01-31
you can ```
 sudo aptitude install gparted 
```, but you can't modify your current partition, so I reccommend you to use live cd for using gParted.

---

### Post by wolfen69 on 2008-01-31
open terminal and type
```
gparted
```

also, go to system>preferences>main menu to add it to the menus.

---

### Post by Seisen on 2008-01-31
Gparted is not installed by default in Ubuntu but you can follow the what fixman said to install.

---

### Post by dstew on 2008-01-31
Linux filenames are case-sensitive. The correct name is gparted, not Gparted.

---

### Post by wolfen69 on 2008-01-31
> **dstew said:**
> Linux filenames are case-sensitive. The correct name is gparted, not Gparted.

relax. he was just starting a sentence with a capital. which last time i checked, is correct in the english language.

---

### Post by LaRoza on 2008-01-31
When installed (it isn't by default) it is under System->Administration->Partition Editor.

---

### Post by dstew on 2008-01-31
> relax. he was just starting a sentence with a capital.I was not referring to Seisen's post, but to the original post, where he had it gParted. I just did not check the misspelling before I posted.

---

### Post by sheki1 on 2008-01-31
tried all those commands, but still no luck...

sudo aptitude install gparted

came back with a bunch of info, but it ended by saying 

'no candidate version found...
no packages wikll be built...
0 packages upgraded, 0 newly installed,
blah blah blah...
ended with "You can install by typing: sudo apt-get install gparted"

tried that but no luck either... it says

This may mean that the package is missing, has been obsoleted or is only availa from another source...

I should mention that the notebook is not currently connected to a wired or wireless network. 
But I do have the Live CD handy...

---

### Post by Aurora@FleetBuzz on 2008-01-31
Suggest you try installing it via the Synaptic Package manager.  Make sure your repositories are enabled and do a search for the program.

---

### Post by sheki1 on 2008-02-01
Hi, I do not have any available connections (wire or wireless) with my new Ubuntu 7.10 install.
So I rely on my Vista dual-boot to get to the net and download at the moment.

I d/led gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and unzipped it, put in on a partition and rebooted into Ubuntu.

Now, how do I run it?

Here's a bit more info...   When I installed ubuntu, I created a root dir and swap dir w/o problem. However, the next time I rebooted I went into Vista and created another partition, before the swap partition.

Now, when I boot into Ubuntu, will it recognize that the swap partition is not in the same location (or same drive number/name), or will it try to use the original location.

Do I need to change anything to make sure the OS works as it should?

:confused:

---

### Post by emarkd on 2008-02-01
If you downloaded the source code, you'll have to compile it, but you don't have what you need to do that on a new installation.  You're better off going [here ]("http://packages.ubuntu.com/gutsy/")and downloading the gparted package.

---

### Post by jan quark on 2008-02-01
or you can use the gparted live cd

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Rocket2DMn on 2008-02-01
You can just ```
sudo apt-get install gparted
```
You can use it on any drive but your root drive since you can't modify a mounted partition.  That's when the LiveCD (either the Ubuntu one of GParted's) comes in handy.

---

### Post by sheki1 on 2008-02-01
> **emarkd said:**
> If you downloaded the source code, you'll have to compile it, but you don't have what you need to do that on a new installation.  You're better off going [here ]("http://packages.ubuntu.com/gutsy/")and downloading the gparted package.

So I clicked on that link and got to the Software Packages in "gutsy" page.  I clicked on the GNOME title and found:

gparted (0.3.3-2ubuntu6)
    GNOME partition editor

then I clicked on gparted and got to 

Package: gparted (0.3.3-2ubuntu6)
goGNOME partition editor

GParted uses libparted to detect and manipulate devices and partition tables while several (optional) filesystem tools provide support for filesystems not included in libparted. 

now what?

---

### Post by sheki1 on 2008-02-01
> **jan quark said:**
> or you can use the gparted live cd

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

> **Rocket2DMn said:**
> You can just ```
sudo apt-get install gparted
```
You can use it on any drive but your root drive since you can't modify a mounted partition.  That's when the LiveCD (either the Ubuntu one of GParted's) comes in handy.

I have the LiveCD and have tried that command with no luck... if I boot with the Live CD I can see the partitions fine, but do I need to change anything so that when i install w/o the cd it will look for the correct swap partition.

Or does Ubuntu find the swap partition just fine without me changing anything?

---

### Post by Rocket2DMn on 2008-02-01
I'm not sure I understand what you're saying. Right now you're in the LiveCD?  GParted is on the LiveCD and you can access it from System->Administration->Partition Editor.
You can go ahead and install Ubuntu and you will be asked about partitions during that time.  Once you have Ubuntu installed you can install gparted to the computer.

---

### Post by jan quark on 2008-02-01
perhaps you can throw in your live cd

boot into the live session

click on install and stop for a while during the partition step of the installation process
there you will see what partitions are present and recognized

---

### Post by JonUK76 on 2008-02-01
> **Rocket2DMn said:**
> I'm not sure I understand what you're saying. Right now you're in the LiveCD?  GParted is on the LiveCD and you can access it from System->Administration->Partition Editor.
You can go ahead and install Ubuntu and you will be asked about partitions during that time.  Once you have Ubuntu installed you can install gparted to the computer.

Exactly what I was thinking :)

---

### Post by sheki1 on 2008-02-01
> **jan quark said:**
> perhaps you can throw in your live cd

boot into the live session

click on install and stop for a while during the partition step of the installation process
there you will see what partitions are present and recognized

I've booted using the boot mgr, but can reboot using the LiveCD if I need to.

If I boot with LiveDC I can see all the partitions fine. Then what?

I know you'll trying to help, maybe I'm not asking the right questions...?!?!?!

---

### Post by Rocket2DMn on 2008-02-01
> **sheki1 said:**
> I've booted using the boot mgr, but can reboot using the LiveCD if I need to.

If I boot with LiveDC I can see all the partitions fine. Then what?

I know you'll trying to help, maybe I'm not asking the right questions...?!?!?!

I'm gonna have to go with that.  Why don't you explain to us exactly what it is you're trying to do, and what you've already done.

---

### Post by jan quark on 2008-02-01
perhaps this will help you

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by RudolfMDLT on 2008-02-01
> **Rocket2DMn said:**
> I'm gonna have to go with that.  Why don't you explain to us exactly what it is you're trying to do, and what you've already done.

+1

Tell us exactly what you've done and then where you want to end up and we'll help! :) Why don't you have internet in Ubuntu? If we fix the internet problem you won't have to install gparted from a downloaded file - it is in the Ubuntu Repo's.

---

### Post by sheki1 on 2008-02-01
> **Rocket2DMn said:**
> I'm gonna have to go with that.  Why don't you explain to us exactly what it is you're trying to do, and what you've already done.

sure...  my notebook came with Vista on one large partititon. I added 3 partitions with Acronis Disk Director 10, one for my date, one to install ubuntu, and another for the swap. I installed Ubuntu with the LiveCD.

I now have a dual-boot system.

Went back to Vista and from that one data partition, I made two data partitions, thereby changing the order of the swap partition from it's original state.

Now, when I boot into Ubuntu, does it recognize that the swap partition has changed from sda6 to sda7 automatically?

is this any better?

---

### Post by sheki1 on 2008-02-01
> **RudolfMDLT said:**
> +1

Tell us exactly what you've done and then where you want to end up and we'll help! :) Why don't you have internet in Ubuntu? If we fix the internet problem you won't have to install gparted from a downloaded file - it is in the Ubuntu Repo's.

I've got a HP notebook with an Atheros wireless card. I've read a post about installing the drivers, but since I cannot connect to the net with the ubuntu partititon, I can't install the drivers..

---

### Post by Rocket2DMn on 2008-02-01
That is much better.  Fi you can boot into Ubuntu, can you please post the outputs of:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sheki1 on 2008-02-01
> **Rocket2DMn said:**
> That is much better.  Fi you can boot into Ubuntu, can you please post the outputs of:
```
sudo fdisk -l
cat /etc/fstab
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122cd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        5222    10490445   83  Linux
/dev/sda3            5223       28832   189647245    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           28832       30401    12603052+   7  HPFS/NTFS
/dev/sda5            5223       18276   104856222    7  HPFS/NTFS
/dev/sda6           18277       27034    70348603+   7  HPFS/NTFS
/dev/sda7           27035       27557     4200966   82  Linux swap / Solaris
/dev/sda8           27558       28832    10238976    7  HPFS/NTFS

Disk /dev/sdb: 1026 MB, 1026555904 bytes
16 heads, 32 sectors/track, 3916 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x3b5dc2bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916     1002480+   b  W95 FAT32


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FEE0E247E0E2062D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=2C88743C8874071C /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=58FCA16AFCA142DC /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=2C3009263008F91A /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=14469cb6-3aa8-429e-a473-a3841f37604f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


when I installed ubuntu, the swap partition was /dev/sda6.  Now it's /dev/sda7.

---

### Post by Rocket2DMn on 2008-02-01
Change your fstab file to this, I changed the second and 3rd to last lines
```
gksudo gedit /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FEE0E247E0E2062D /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda4
UUID=2C88743C8874071C /media/sda4 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=58FCA16AFCA142DC /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda7
UUID=2C3009263008F91A /media/sda7 ntfs defaults,umask=007,gid=46 0 1
# swap (old /dev/sda6)
/dev/sda7 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Then run
```
sudo mount -a
```
Do you have problems getting other partitions to mount after the change?

---

### Post by tad1073 on 2008-02-01
> /dev/sda7 27035 27557 4200966 82 Linux swap / Solaris
# /dev/sda7 UUID=2C3009263008F91A /media/sda7 ntfs defaults,umask=007,gid=46 0 1

from what I can see it looks like ubuntu recognized sdc7 as swap

---

### Post by sheki1 on 2008-02-01
> **Rocket2DMn said:**
> Change your fstab file to this, I changed the second and 3rd to last lines
```
gksudo gedit /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FEE0E247E0E2062D /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda4
UUID=2C88743C8874071C /media/sda4 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=58FCA16AFCA142DC /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda7
UUID=2C3009263008F91A /media/sda7 ntfs defaults,umask=007,gid=46 0 1
# swap (old /dev/sda6)
/dev/sda7 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Then run
```
sudo mount -a
```
Do you have problems getting other partitions to mount after the change?

will try it later this eve... what does fstab do?

---

### Post by Rocket2DMn on 2008-02-01
fstab is where your system looks for information about where to mount different partitions.  It is primarily used for static filesystems like internal hard drives and where to look for the swap, the processor, the root filesystem, and a /home partition if you have a separate one, and any cd/dvd or floppy drives you might have.
External drives like usb disks and flash drives are not in here since they mount automatically when you plug them in.

---

### Post by kaiju on 2008-02-02
yup, turns out it was the wrong question :P

Rocket2DMn is very right, except that you are only mounting 4 of your 5 ntfs partitions in his example. but if you take a good look at your sudo fdisk -l output, you can easily add that one too ;)

---

### Post by erfahren on 2008-02-02
actually the fstab that Rocket2DMn posted in post #18 is NOT correct

/dev/sda7 is listed twice
```

# /dev/sda7
UUID=2C3009263008F91A /media/sda7 ntfs defaults,umask=007,gid=46 0 1
# swap (old /dev/sda6)
/dev/sda7 none swap sw 0 0

```
note: "blkid" gives a little clearer output - including the [UUID](http://linux.byexamples.com/archives/321/fstab-with-uuid/)
```

blkid

```

--- good info here: [hermanzone's Filesystems and Mounting page](http://users.bigpond.net.au/hermanzone/p10.htm)

EDIT: more info links
[How to fstab](http://ubuntuforums.org/showthread.php?p=1653968)
[Setting permissions for FAT (and NTFS) filesystems - Fedora Forum](http://forums.fedoraforum.org/archive/index.php/t-32096.html)
[How to edit and understand /etc/fstab - tuxfiles.org](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Fechter on 2008-02-02
Hey, why not look here 
[http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml](http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml)
To create root partition, just type to it /  and format it as ext3
To create swap /1,5 times more than your RAM/ just click swap:)

Manual partition, remember. Automatic will delete your whole data. There are many properties, you will see. If you need help, write here.

---

### Post by kaiju on 2008-02-02
alright, i was too quick with that reply (thanks, erfahren :) ).

i will be assuming  that you do not want to reinstall or format anything.

from what i can see, you still have the same root partition (/dev/sda2 > / ext3) but a differnt swap (/dev/sda7 > none swap). you also have five ntfs partitions.
if you want to make it clear and simple, you can do a 'sudo umount /media/sda7' and remove the mount point sda7 (because that partition is your swap now), then make two new mount points: 'sudo mkdir /media/sda6' (for the last ntfs you created) and 'sudo mkdir /media/sda8' (for the one that used to be sda7 before the change).

then edit your fstab to make every /dev/sda entry have the corresponding mount point.
and, as erfahren already pointed it out, you can use blkid's output to replace the /dev/sda entries with uuids.

---

