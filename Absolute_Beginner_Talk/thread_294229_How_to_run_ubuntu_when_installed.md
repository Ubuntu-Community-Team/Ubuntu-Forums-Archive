---
title: "How to run ubuntu when installed?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by sasamsa on 2006-11-06
Ok so now that I have installed it how do I run it?
When I turn my pc on it just boots win xp without asking me anything....
I have 2 hds and have created partitions on first (where winxp is) for ubuntu..

I tried something like this 
 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

but no matter what I put in root (hd0,x) it tells me that hd doesnt exist...
I gave up trying and need help...

---

### Post by mahy on 2006-11-06
How did you install Ubuntu? Desktop CD or Alternate CD. To the best of my knowledge, Desktop CD installs Grub to MBR of the first hard drive so it shouldn't be a problem... Try this:

Boot the Live CD. Assuming your Ubuntu partiton is /dev/hda2 and you use ext3:

sudo mkdir /mnt/whatever
sudo mount -t ext3 /dev/hda2 /mnt/whatever
sudo chroot /mnt/whatever
sudo /sbin/grub-install /dev/hda

---

### Post by Bachstelze on 2006-11-06
Here's another approach :

1. Boot the live CD and become root : *sudo -i*.

2. Create a mountpoint for your root partition : *mkdir /mnt/root*

3. Mount it : *mount -t ext3 /dev/whatever /mnt/root*

3b. If you have a separate /boot partition, mount it too : *mount -t ext3 /dev/whatever /mnt/root/boot*

4. Run grub-install : *grub-install --root-directory=/mnt/root /dev/whatever*

5. Reboot :)

---

### Post by ironfistchamp on 2006-11-06
EDIT: Much better ideas than my OP.

---

### Post by sasamsa on 2006-11-06
tried mahys method but gave me an error at the last command "not found or not a block device".. (mine is installed to dev/sda6 so I used  sudo mount -t ext3 /dev/sda6 /mnt/whatever) so at the last command I tried  
sudo /sbin/grub-install /dev/hda
sudo /sbin/grub-install /dev/sda6
sudo /sbin/grub-install /dev/sda
but it gave me the same error and still boots to xp...

---

### Post by bulldog on 2006-11-06
Can you give the outcome of```
sudo fdisk -l
```l as in like.

So we can see if Ubuntu is installed and where it is installed

{type yhe command in your terminal and copy paste the outcome on the forum}

---

### Post by Bachstelze on 2006-11-06
And also, please paste the exact commands you type and the exact error messages you get.

---

### Post by sasamsa on 2006-11-06
> **bulldog said:**
> Can you give the outcome of```
sudo fdisk -l
```l as in like.

So we can see if Ubuntu is installed and where it is installed

{type yhe command in your terminal and copy paste the outcome on the forum}

here it is>
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        5100    40957717+   7  HPFS/NTFS
/dev/sda2            5101       19929   119113942+   f  W95 Ext'd (LBA)
/dev/sda5            5101       19547   116045496    7  HPFS/NTFS
/dev/sda6   *       19548       19864     2546271   83  Linux
/dev/sda7           19865       19929      522081   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

---

### Post by sasamsa on 2006-11-06
maybe it installed grub to the wrong disk?

---

### Post by bulldog on 2006-11-06
> **sasamsa said:**
> maybe it installed grub to the wrong disk?

Well try it out and boot from your sda disk,you can set the bootorder in your BIOS I presume,or press a button while booting to get a menu to choose which bootdevice you want to use.

Or is your Sata disk your bootdisk and your IDE is a storage disk.

If that's the case and your Sata is your bootdisk I'm sure GRUB is on the wrong disk.

It installs on the first hdd by default and that is in your case the IDE drive.

---

### Post by sasamsa on 2006-11-06
> **bulldog said:**
> Well try it out and boot from your sda disk,you can set the bootorder in your BIOS I presume,or press a button while booting to get a menu to choose which bootdevice you want to use.

Or is your Sata disk your bootdisk and your IDE is a storage disk.

If that's the case and your Sata is your bootdisk I'm sure GRUB is on the wrong disk.

It installs on the first hdd by default and that is in your case the IDE drive.

wow it did install grub to the wrong disk...
and sata is the disk where winxp and ubuntu are installed and ide is where it installed grub..
I can boot ubuntu from second drive...
How to get it back to the primary drive where winxp and ubuntu are installed :) :-k

---

### Post by Bachstelze on 2006-11-06
Install it the way I told you but enter the correct drive in the grub-install command.

---

### Post by sasamsa on 2006-11-06
> **HymnToLife said:**
> Install it the way I told you but enter the correct drive in the grub-install command.
I entered this:

sudo -i.
mkdir /mnt/root
mount -t ext3 /dev/sda6 /mnt/root
grub-install --root-directory=/mnt/root /dev/sda

and it installs grub but when I click Ubuntu, kernel 2.617.....it says error no such partition

---

### Post by bulldog on 2006-11-06
Just set your IDE drive as bootdevice and boot from this disk.

It shouldn't be a problem.

If you want GRUB on the Sata disk boot the live cd and do the following commands.
```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


[code]sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
[/code]

---

### Post by sasamsa on 2006-11-06
> **bulldog said:**
> Just set your IDE drive as bootdevice and boot from this disk.

It shouldn't be a problem.

If you want GRUB on the Sata disk boot the live cd and do the following commands.
```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


[code]sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
[/code]

I want to buy a new drive and give that to a friend but I cant if I cant boot without it... :)

So I did the find /boot/grub/stage1 and it just said (hd1,5)
(I guess that the ide drive is hd0 and sata from where I want to boot is hd1)

and then I did 

root (hd1,5)
setup (hd1)

...and grub is still installed to the sata but it wont boot neither ubuntu or winxp, but grub from ide drive works ???](*,)

---

### Post by bulldog on 2006-11-06
Give me the output of```
gedit /boot/grub/menu.lst
```

It was the intention to set GRUB on the Sata disk?
Well there should be some altering to be done to let it work.

To remove GRUB from the IDE you just install windows and GRUB will be gone.

---

### Post by sasamsa on 2006-11-06
> **bulldog said:**
> Give me the output of```
gedit /boot/grub/menu.lst
```

It was the intention to set GRUB on the Sata disk?
Well there should be some altering to be done to let it work.

Yes I want grub to work on sata and I dont care about the ide (where it works now)... ;)
from ubuntu live gedit /boot/grub/menu.lst is empty...
hmm more trouble?:-k

---

### Post by bulldog on 2006-11-06
I,m sorry it was the plan you boot your Ubuntu first before you gave the command.

But it can be done from the live cd as well.```
sudo mkdir /mnt/rescue
```
Than,```
sudo mount /dev/sda6 /mnt/rescue
```
Now your Ubuntu install is mounted at /mnt/rescue.
To open menu.lst```
gedit /mnt/rescue/boot/grub/menu.lst
```
This opens your menu.lst in read only mode.
Copy this to the forum please.

---

### Post by sasamsa on 2006-11-06
ubuntu@ubuntu:~$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/rescue
gemount: /dev/sda6: can't read superblock
ubuntu@ubuntu:~$ gedit /mnt/rescue/boot/grub/menu.lst

damn...im gonna boot from disk and than list the file...

---

### Post by sasamsa on 2006-11-06
Here it is

sasa@sasa-desktop:~$ gedit /boot/grub/menu.lst

```
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
# kopt=root=UUID=e65f047e-6375-43d3-95a8-e686cde73a0d ro
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,5)
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
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by bulldog on 2006-11-06
```
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
# kopt=root=UUID=e65f047e-6375-43d3-95a8-e686cde73a0d ro
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1) {This is good if you boot from IDE
#map		(hd1) (hd0) not needed when you use the Sata.} 
chainloader	+1

```

I have altered some things (hd1,5) should be (hd0,5) if you boot from Sata.
And your windows shouldn't be mapped and is located on (hd0,0).

This works only if you use the Sata disk to boot but if you use the IDE you should keep the one you posted.

Resuming,we're going to make a copy of your menu.lst so if you want to use the IDE for some reason to boot you have only to copy the menu.lst back and it works.[I presume you are **not** on the live cd]
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-ide
```
With the next command you open your menu.lst and alter the menu.lst as I discribed [or copy paste it]
```
gksudo gedit /boot/grub/menu.lst
```

Alter it and save the file.

Now you should be able to boot from your Sata disk into windows or Ubuntu.
Ubuntu is the default but if you prefer windows as a default boot,set this zero to three```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

---

### Post by sasamsa on 2006-11-06
thank you very very much bulldog..:) Now everything works

---

### Post by bulldog on 2006-11-06
Glad to hear,welcome to Ubuntu :D

---

### Post by beefcurry on 2006-11-08
Is the problem due to GRUB itself or the Ubuntu installation of grub? I had this EXACT problem, took me ages for it to boot from GRUB and not straight to windows. And once i got GRUB loaded all its load directories are wrong, had to manually change the boot locations, just like above it mapped the windows drive and got it completely wrong.

Just that ive got a IDE and a SATA drive installed with booting on SATA, exact same config, exact same installation problem..this calls for consern :)

---

