---
title: "Reinstalling GRUB?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-05-31
I've been having some problems with my Ubuntu system after I tried to install Windows XP on an unused partition on it. After removing this partition, I'm still unable to load Ubuntu. I'm using 6.06 and a 7.04 recovery cd to reinstall grub to get around this problem. (NOTE: This initially fixed my problem just fine, and then I was bullheaded enough to try installing windows again. Maybe I'm learning something here. Don't tell no-one!)

Right now, I have two mounted partitions: swap and /media/hda2. I can't get grub to mount in this setup as I get an error stating that I have not defined a root file system. Is there anything I can do to get my system recovered?

---

### Post by mikewhatever on 2007-05-31
I think that every time you reinstall Windows, the mbr is overwritten.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by seeknowsage on 2007-05-31
Thanks! That seemed to help. However, at boot, I get an option to select between Windows XP and Ubuntu still for some odd reason. If I select the Ubuntu partition, I get "Error 22: No such partition". If I select the Windows option, it goes to a black screen stating "Starting up ..." and nothing happens.

Any ideas?

---

### Post by confused57 on 2007-05-31
Boot the live cd  that you used to install Ubuntu, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Once you determine which is your root partition, mount it & post your menu.lst:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
substitute your root partition for hda1, then

```
gedit /media/ubuntu/boot/grub/menu.lst
```

See this link for more detailed instructions:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by seeknowsage on 2007-05-31
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *        4951        9639    37664392+  83  Linux
/dev/hda3            9640        9900     2096482+  82  Linux swap / Solaris
/dev/hda4            9901        9964      514080    b  W95 FAT32



ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2 /media/ubuntu
ubuntu@ubuntu:~$ gedit /media/ubuntu/boot/grub/menu.lst




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
# kopt=root=UUID=f50e1bfb-f7bc-4c08-9aec-1604900d23a9 ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by mikewhatever on 2007-05-31
The partition Ubuntu is on is hda2, which, in terms of GRUB is hda1. Edit the first boot option as follows
> title Ubuntu, kernel 2.6.17-11-generic
root (hd0,[COLOR="Red"]1[/COLOR])
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
The Windows entry shows because it is at the end of the file. Delete it if not needed.

---

### Post by seeknowsage on 2007-05-31
mikewhatever,
     Thank you for your help. Should I edit menu.lst through the LiveCD, save, then reboot for this to take effect?

---

### Post by confused57 on 2007-05-31
> **seeknowsage said:**
> mikewhatever,
     Thank you for your help. Should I edit menu.lst through the LiveCD, save, then reboot for this to take effect?
mike's right, but you also need to change the root in your kernel line(root=/dev/hda2

You can do this from the grub boot menu, highlight your Ubuntu entry, press "e", then change root to what mike suggested, then change the root in your kernel line, then press "b" to boot.
If this doesn't work, then try "root (hd0,0)" and make the same change in your kernel root.

---

### Post by seeknowsage on 2007-05-31
Thanks! This seems to be a move in the right direction. However, after making the change in the grub boot menu listed above, I'll get to the Ubuntu launch screen, but nothing happens and the bar doesn't fill up. Any ideas?


EDIT: Actually, after about 5 minutes of waiting, a black screen with the following text is produced:

"BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs) _"

---

### Post by confused57 on 2007-05-31
> **seeknowsage said:**
> Thanks! This seems to be a move in the right direction. However, after making the change in the grub boot menu listed above, I'll get to the Ubuntu launch screen, but nothing happens and the bar doesn't fill up. Any ideas?
You might want to check you /etc/fstab:
mount your root partition as before, using the live cd, then:
```
gedit /media/ubuntu/etc/fstab
```

to change your root partition(probably to /dev/hda2):
```
gksudo gedit /media/ubuntu/etc/fstab
```

Added:  Did you get the error message, trying both root (hd0,1) and (hd0,0)?

---

### Post by seeknowsage on 2007-05-31
I only got the error message with (hd0,1). The system wouldn't boot at all with (hd0,0). I believe I got an "error 17" with that.

Going to try the changes you suggested now. Will this help with the followup error message I received after waiting 5 minutes or so at the boot screen I mentioned when I edited my previous post?

Thank you very much for all of your help thus far!

---

### Post by confused57 on 2007-05-31
> **seeknowsage said:**
> I only got the error message with (hd0,1). The system wouldn't boot at all with (hd0,0). I believe I got an "error 17" with that.

Going to try the changes you suggested now. Will this help with the followup error message I received after waiting 5 minutes or so at the boot screen I mentioned when I edited my previous post?

Thank you very much for all of your help thus far!

I hope it helps...your /etc/fstab probably has /dev/hda1 for your / partition, changing it to /dev/hda2 would concur with your "fdisk -l" output.

---

### Post by seeknowsage on 2007-06-01
These are the current contents of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=[REMOVED] /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=[REMOVED]  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=[REMOVED] none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0



Note that there were some numbers I replaced with [REMOVED] above. Should I uncomment out the /dev/hda4 below "UUID=[REMOVED] /               ext3    defaults,errors=remount-ro 0       1" in addition to changing it to hda2, saving it, then rebooting?

---

### Post by confused57 on 2007-06-01
Sorry for the delay, but I wanted to boot into my Dapper install & post my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

So yours should look something like this:
```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0 
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda4 /media/hda4 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda3  none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
```

You might want to adjust the spacing a little, using my Dapper fstab as an example.

---

### Post by seeknowsage on 2007-06-01
I tried making the suggested change, but I still get to the same error before (initramfs prompt). Furthermore, the grub boot loader isn't saving the change I make to the boot location (hd0,1). Additionally, are the changes I make to the fstab file saved when I edit it through the LiveCD? Thanks again!

Edit: The above is in reference to a previous post, not your most recent reply. I'm going to give that a shot now (=

---

### Post by confused57 on 2007-06-01
> **seeknowsage said:**
> I tried making the suggested change, but I still get to the same error before (initramfs prompt). Furthermore, the grub boot loader isn't saving the change I make to the boot location (hd0,1). Additionally, are the changes I make to the fstab file saved when I edit it through the LiveCD? Thanks again!

Edit: The above is in reference to a previous post, not your most recent reply. I'm going to give that a shot now (=
The changes you make using "e" in the grub boot menu are temporary, you make it permanent in your /boot/grub/menu.lst.   Hope the fstab changes work...good luck.

---

### Post by seeknowsage on 2007-06-01
I just made the fstab changes, but unfortunately it still stalls out at the ubuntu boot screen (the bar remains at zero for 5 minutes or so  before loading a separate error page).

---

### Post by confused57 on 2007-06-01
> **seeknowsage said:**
> I just made the fstab changes, but unfortunately it still stalls out at the ubuntu boot screen (the bar remains at zero for 5 minutes or so  before loading a separate error page).

Do you remember what the error message is?  You could try taking out the "quiet" & "splash" options in your kernel line to see where the boot process  is stalling.

Another thing you might want to try is a filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

The easiest way is with the gparted live cd, as described in the link...you may have to scroll down a little for the instructions on how to do this.

---

### Post by seeknowsage on 2007-06-01
The error was:
"BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs) _"

Going to give the file system check a shot now!

---

### Post by seeknowsage on 2007-06-01
It's working!

I went back and read all the suggestions made by mike and you and made sure the suggested changes were made. I completely overlooked your recommendation of editing the root location in menus.lst to /dev/hda2. And just as I was about to throw in gparted! 

mikewhatever and confused57, thank you both VERY much for your help! You both really went above and beyond in helping a stupid newb like me, and I am really grateful!

(Edit: The reason I tried and failed to install windows on this machine is because I wanted to test out the new monitor I have it running on. I upgraded from a 15" Dell lcd to a 22" Acer value LCD. For some reason, the text is noticably blurry in Firefox and other applications [including login]. I don't know if this is the monitor itself, my old 9700 pro video card having problems with the bigger resolution, or just a general quirk with Ubuntu.)

---

### Post by confused57 on 2007-06-01
> **seeknowsage said:**
> It's working!

I went back and read all the suggestions made by mike and you and made sure the suggested changes were made. I completely overlooked your recommendation of editing the root location in menus.lst to /dev/hda2. And just as I was about to throw in gparted! 

mikewhatever and confused57, thank you both VERY much for your help! You both really went above and beyond in helping a stupid newb like me, and I am really grateful!

Glad it worked...I was running out of ideas, if you were following the suggestions from mike & me.
I was more than clueless when I started using Ubuntu, hence my username.  You probably learned a little tonight.

Be sure to make the changes permanent in your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
quit & save

Added:  One last thing you need to do...change your #groot line to (hd0,1):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

