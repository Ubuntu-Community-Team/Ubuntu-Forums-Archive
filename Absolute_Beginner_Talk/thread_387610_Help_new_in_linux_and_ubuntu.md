---
title: "Help new in linux and ubuntu"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by KeeperMustDie on 2007-03-18
Hi, I just installed Ubuntu to my pc. Before that I had 1 hard drive splited in c:(5GB) and d:(70GB) disks. I installed Ubuntu in c: and I had windows xp in d:. After rebooting I was shocked: Ubuntu starts ignoring windows... Now I cant access to windows xp and all files witch was stored in d:. But I don't want to remove ubuntu, I want to have 2 os. How I can to make Ubuntu let me access to windows or at least how I can access to d: disk?

---

### Post by mikewhatever on 2007-03-18
Open the terminal (Application>Accessories>Terminal) and post here the output of the following commands
> sudo fdisk -l
sudo gedit /boot/grub/menu.lst

---

### Post by KeeperMustDie on 2007-03-18
Yes, now I see menu list, what to do now?

---

### Post by mikewhatever on 2007-03-18
> **KeeperMustDie said:**
> Yes, now I see menu list, what to do now?

As I said, post the output of the two commands here.

---

### Post by KeeperMustDie on 2007-03-18
Yea I already inputed the commands and now I see menu.lst

---

### Post by tom56 on 2007-03-18
He wants you to copy what you get from the window and to post it here.

For example if I do it I get
```

tom@scaleo:~$ sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10334    83007823+   7  HPFS/NTFS
/dev/sda2           10335       30023   158151892+  83  Linux
/dev/sda3           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris
```

and
```

tom@scaleo:~$ sudo cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bcaad465-0190-4fb2-bdd0-835c90f9be6b ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by mikewhatever on 2007-03-18
> **KeeperMustDie said:**
> Yea I already inputed the commands and now I see menu.lst

It's ok that you see it, but to help you, I need to see the output of the two commands. Can you please copy the output and paste it in your next post.
Thanks Tom56 :)

---

### Post by KeeperMustDie on 2007-03-18
Oh omg sorry! I didn't noticed... after first command I get this:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          66      530113+  82  Linux swap / Solaris
/dev/hda2             641        9732    73031490    f  W95 Ext'd (LBA)
/dev/hda3              67         640     4610655   83  Linux
/dev/hda5             641        9732    73031458+  82  Linux swap / Solaris

Partition table entries are not in disk order

other command opens menu.lst

---

### Post by tom56 on 2007-03-18
Ok. And what does your menu.lst look like? Please can you post the contents of it here.

Thanks


EDIT: spelling

---

### Post by KeeperMustDie on 2007-03-18
[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff6f91b9-efb9-48f6-bfe9-344d2b8c29f3 ro
# kopt_2_6=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot


### END DEBIAN AUTOMAGIC KERNELS LIST[/PHP]

---

### Post by tom56 on 2007-03-18
Ok try running the following:

```
sudo dpkg-reconfigure grub
```

Then reboot. If that doesn't work then don't panic there is another solution but it's a little harder. Come back here and I'll help though.

---

### Post by KeeperMustDie on 2007-03-18
No result

---

### Post by mikewhatever on 2007-03-18
Add the following to the end of your GRUB menu.lst
> # This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows
root        (hd0,1)
savedefault
makeactive
chainloader    +1
Save and exit.

---

### Post by tom56 on 2007-03-18
And make sure the line that just says "hiddenmenu" is commented out, i.e. add a # before it

---

### Post by mikewhatever on 2007-03-18
Tom56 is right.
To actually see the menu at boot, edit the following part
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

to look like this
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


---

### Post by KeeperMustDie on 2007-03-18
Again - no result. I chosen Microsoft Windows title and then get error:
 error 12: invalid device request

---

### Post by tom56 on 2007-03-18
Hmm. I'm just eating my dinner so I'll be back in 30 mins to help. I'll leave you in mikewhatever's clearly capable hands :)

---

### Post by mikewhatever on 2007-03-18
> **KeeperMustDie said:**
> Again - no result. I chosen Microsoft Windows title and then get error:
 error 12: invalid device request

Can you tell us more about your system setup? Was there another Windows installation on the PC? Why do you have two swap partitions? Anything you can think of.
I found information on the error 12 here [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

Does it apply to your setup? Try to make something out of it, although it does not look too promising.
> 12 : Invalid device requested
    This error is returned if a device string is recognizable but does not fall under the other device errors. 

It looks like this,
Error 12: Invalid device requested

Press any key to continue..._


I received this error while trying to boot Windows XP in a logical partition. Normally, Windows is only bootable in a primary partition, because only a primary partition can be set  as 'active'. However, the Windows  default method of dual booting more than one Windows system installs the boot-up files in the previously existing Windows installation, and the subsequent Windows installation boots via the original installation. In this case, Windows users call their original installation their 'boot partition'.
Unfortunately for a some unlucky Windows users, once the installation has been completed that way, it means if they delete thier original installation, it becomes impossible to boot their new installation, which may be in a logical partition.

That is why Windows users are better off dual or multi booting with Grub. That is why Super Grub Disk provides Windows users with special tools such as the ability to hide and unhide partitions to allow a subsequent Windows to be installed independantly of an existing installation.
'English Super Grub Disk'-->'Advanced'-->'Windows (Advanced)'--> Unhide 1 Partition and Hide other Partitions... and Boot...

For Windows users to use Grub without Linux, they would need to install WinGrub, GRUB4DOS and WINGRUB Project Homepage  WinGrub is very good, I have tested it in a FAT32 filesystem Windows XP Home Edtition and it is currently working very well for me.
Otherwise, they would need at least one Linux installation in thier computer, to have Grub installed in, I suggest Ubuntu, and even 'Damn Small Linux' would do if they want to save disk space.

Grub is a much better bootloader and boot manager than Windows' own bootloader when it comes to dual or multi booting.

Once Windows is already installed wrong, and the 'boot partition' has been deleted, Super Grub Disk can't really help that.
There is still a chance that this kind of problem can be worked around, but depending on circumstances this might be difficult or impractical. I would suggest making a lot of room on the disk somehow and making a new primary partition with GParted -- LiveCD and copying and pasting the whole Windows partition there, so it will be a primary partition now.
Then make a Windows Xp boot floppy, Click Here for a how-to. Then try to boot it.
If it will boot up at all, to avoid always needing to use the floppy disk, try copying the files from the floppy disk to the root of the Windows partition. I don't know if that will work or not, I have never tried it, but it seems to be worth a try.



---

### Post by KeeperMustDie on 2007-03-18
I had 2 windows xp one in disc D: (logical) other in disc C: (primary) I instilled linux in disk C: and formated it creating 2 partitions because it was requested to create at least 2 GB partition to root and 0.25GB to swap partition after installation i can't use windows xp because automatically starts linux. Thats all i can't imagine that it is so difficult to make that I could use windows again. I think it is some misunderstandings makes all difficult. I tried to explain all clearly so I hope you can help me.

---

### Post by tom56 on 2007-03-18
Do you mean to say you are using two hard drives when you say C: and D: ? Because the output of fdisk says you only have one hard drive. If you do have two then run fdisk -l again making sure you copy absolutely everything to post here.  Please can you post your menu.lst again? I know it's a drag but it might have changed so I just want to check everything is right there so that we can be sure that that's not the problem.

---

### Post by KeeperMustDie on 2007-03-18
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff6f91b9-efb9-48f6-bfe9-344d2b8c29f3 ro
# kopt_2_6=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST






Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          66      530113+  82  Linux swap / Solaris
/dev/hda2             641        9732    73031490    f  W95 Ext'd (LBA)
/dev/hda3              67         640     4610655   83  Linux
/dev/hda5             641        9732    73031458+  82  Linux swap / Solaris

Partition table entries are not in disk order







And i was talking about one hard splited  into 2 discs C and D.

---

### Post by tom56 on 2007-03-18
EDIT: sorry, misunderstood the grub manual - ignore this post

---

### Post by KeeperMustDie on 2007-03-18
Remove linux partition? You suggest format C: disk (linux) or there is some other way? And also how to make that linux would be *after* windows?

---

### Post by tom56 on 2007-03-18
Nevermind, it was a mistake. Essentially the problem you have is outlined in mikwhatever's last post. You've installed Windows on both primary and logical partitions then deleted the primary partition. I don't really want to suggest any more solutions because it's too easy to get it wrong now we're into problems of partitions and so on - but I'll do a little searching for 5 minutes or so. However using mikewhatever's post you should be able to fix this. Best of luck!

---

### Post by tom56 on 2007-03-18
OK, this is the last thing I will suggest

replace

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

with

# Windows
title Microsoft Windows
hide(hd0,0)
root (hd0,1)
savedefault
makeactive
chainloader +1

---

