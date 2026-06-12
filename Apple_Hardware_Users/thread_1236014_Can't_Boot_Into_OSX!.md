---
title: "Can't Boot Into OSX!"
date: 2009-08-09
forum: Apple Hardware Users
---

### Post by mspainhour on 2009-08-09
I chose to install Ubuntu on an external hard drive on my Mac mini. I dictated to the installer to install to a 50 GB partition of a 500 GB Hard drive. The installation was successful and I restarted upon completion, as the installer requested.

After restarting I got a Folder with a "?" in it.

It cannot find/boot into the Ubuntu installation, nor can it locate my OSX installation. I booted into the LiveCD and checked by HD contents, and both the Ubuntu Installation and the OSX installation seem to be unscathed, but my computer cant find them.

I've done some research on the subject and it seems to be a bootloader problem? Not sure.

Ubuntu masters, I call upon you for help. :confused:

Without you, I'm left only to the Apple store, and I'm out of warranty. I don't like imagining the wallet gouging to come if I cannot figure this out.

---

### Post by j.bell730 on 2009-08-09
Post output of:
```
cat /boot/grub/menu.lst
```

---

### Post by mspainhour on 2009-08-09
Oh damn. No such file or directory:

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by j.bell730 on 2009-08-09
Ah, that explains it...
```
sudo apt-get install grub
```
Then post output of above command.

---

### Post by mspainhour on 2009-08-09
Still getting the same error:

ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
grub is already the newest version.
grub set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 184 not upgraded.
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

<EDIT> Keep in mind that I'm on Ubuntu LiveCD because of this problem.

---

### Post by j.bell730 on 2009-08-09
Argh, this will get ugly, post the output of:
```
sudo fdisk -l
```

---

### Post by mspainhour on 2009-08-09
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007d39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78150740   ee  GPT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c714

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6528    52428800   83  Linux
/dev/sdb2            6528       60802   435957732   af  Unknown

---

### Post by j.bell730 on 2009-08-09
Oh, yes, I forgot you're on the Live CD...
In that case, try this:
```
sudo mount /dev/sdb1
```
Then, try the above command:
```
cat /boot/grub/menu.lst
```

---

### Post by mspainhour on 2009-08-09
ubuntu@ubuntu:~$ sudo mount /dev/sdb1
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by j.bell730 on 2009-08-09
Ok, mounted on /media/disk, see if you can get to it via:
```
cat /media/disk/boot/grub/menu.lst
```

---

### Post by mspainhour on 2009-08-09
Ugh, if you cant get terminal to do something, you have to do it yourself:

I just manually opened up the partition to wich I installed Ubuntu. (Attempted, more likely... lol)

Here's the menu.lst in that installation:


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=3b39f962-378a-471b-9d9d-eb75fe4414b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b39f962-378a-471b-9d9d-eb75fe4414b3

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3b39f962-378a-471b-9d9d-eb75fe4414b3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3b39f962-378a-471b-9d9d-eb75fe4414b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3b39f962-378a-471b-9d9d-eb75fe4414b3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3b39f962-378a-471b-9d9d-eb75fe4414b3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3b39f962-378a-471b-9d9d-eb75fe4414b3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mspainhour on 2009-08-09
Oh, and just so we're on the same page:

Mac mini - 80 GB Hard drive with OSX installed

500 GB External USB Hard Drive, partitioned:
--->50 GB Partition with Ubuntu "installed"
--->~450 GB hfs+, journaled* for storage in OS X


I could be mistaken about the "hfs+, journaled" part.

---

### Post by j.bell730 on 2009-08-09
After this:
```
title Ubuntu 9.04, memtest86+
uuid 3b39f962-378a-471b-9d9d-eb75fe4414b3
kernel /boot/memtest86+.bin
quiet
```
(The last grub entry)

Add this:
```
title          Mac OS X86
root         (hd1,1)
makeactive
chainloader +1
```
That should add the Mac entry to grub, so you can choose it when booting.

Then, when it reboots, if you don't see the grub bootloader, press the button it tells you to (for me it's Esc, but I have no idea if Macs are different).

---

### Post by mspainhour on 2009-08-09
This may work, I'm not sure, but to clarify, even when I do a fresh boot I get no option to boot into anything. OSX and Ubuntu. I cannot boot into anything.

I just want to make sure you know that because I'm on LiveCD and my stuff will be lost when I restart.

<Edit> Damnit. I don't have permissions to make that ammendment to menu.lst...

---

### Post by j.bell730 on 2009-08-09
Ok, just to be clear, what do you get, specifically, when you boot up? Black screen? Pure command prompt environment? Anything?
And, to change that file, type
```
sudo gedit <path to file>
```

---

### Post by mspainhour on 2009-08-09
When I boot, I get a completely grey screen and then a flashing version of this image:

[http://adamturtle.com/wp-content/uploads/2008/11/mac-os-folder-question-mark.gif](http://adamturtle.com/wp-content/uploads/2008/11/mac-os-folder-question-mark.gif)


<Edit> I added that portion of text to that file sucessfully.

---

### Post by j.bell730 on 2009-08-09
Oh, ok, but before you do anything else, can your problem be compared to [this one]("http://ubuntuforums.org/showthread.php?t=1091282")?

---

### Post by mspainhour on 2009-08-09
Not that I can tell. That thread seems to revolve around an installation using a botched Ubuntu install disk that crapped it's pants, messing up the computer. But the question mark folder he describes is the one plaguing mine.

From what I can see, that folder icon depicts a wide range of problems on macs:

Hard drive failure
missing installation
damaged installation
missing boot directory
etc...

Dunno what to do. The fine people on this forum may be my only hope. That or being sexed in the butt by the apple store.

---

### Post by j.bell730 on 2009-08-09
Well, since you were able to post items from your boot folder, you are not missing it. Damaged installation...potentially. But, like you said, the installation is not missing because you checked it yourself from the live CD.

---

### Post by mspainhour on 2009-08-09
So I'm assuming you're stumped?

Let me try a restart and boot and get back to you.

brb

---

### Post by mspainhour on 2009-08-09
Damn... no dice.

Still not working.

It seems I cant even choose where I would like to boot to...

1) Turn on computer
2) Grey boot screen
3) Flashing Folder Icon

It seems I'm limited to LiveCD at this point.

Ah well... I made an Apple Store appointment for tommorow, I'll see what they have to say, have it fixed, and then pay them an exorbitant amount of money.

Ubuntu + Mac OS = Fail, apparently.

---

