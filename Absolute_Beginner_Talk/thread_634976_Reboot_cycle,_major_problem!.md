---
title: "Reboot cycle, major problem!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-08
I had a great install of Ubuntu and I rebooted into WinXP to play a game.  When I was done, I rebooted to go back to Ubuntu.

However, when the boot process gets to the "Loading Grub..." phase it simply reboots again.  It's going on and on in this cycle.

Please tell me I haven't lost everything on both installs...

---

### Post by Mramius on 2007-12-08
I was able to insert the Ubuntu CD and boot to it...I'm at the Live desktop but it's obviously not my regular installation.

Is there something I can do here to fix the problem?

---

### Post by philinux on 2007-12-08
Sounds like grub is messed up - you may need to reinstall grub.

I'd google and get the "super grub" disk

---

### Post by Mramius on 2007-12-08
Is this a valid option:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by Mramius on 2007-12-08
Here is the output of fdisk -l


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30168   242324428+  42  SFS
/dev/sda2           30169       30401     1871572+  42  SFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33fe33fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+  42  SFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff18ff18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08640863

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4865    39078081    7  HPFS/NTFS

What information do I need and where do I need to put it?

---

### Post by philinux on 2007-12-08
what does /boot/grub/menu.lst look like.

---

### Post by Mramius on 2007-12-08
There is no /boot/grub/ directory.  There are just files in the /boot directory.

---

### Post by philinux on 2007-12-08
Are you looking on your / on your hard drive?

If you sudo gedit /boot/grub/menu.lst it should bring it up.

---

### Post by Mramius on 2007-12-08
I'm booted into the Live CD.

I open a terminal and type that and I get nothing.

---

### Post by Mramius on 2007-12-08
Ok, I found it.  Do I need to paste the whole thing here or can you tell me what it "should" look like, as opposed to what it "does" look like.  Because what it does look like is obviously not what it's supposed to. :)

---

### Post by Mramius on 2007-12-08
Anyone?  I'd really like to be able to use my computer again, and not just some Live CD! LOL

---

### Post by Mramius on 2007-12-08
K, here's what menu.lst looks like:

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
# kopt=root=UUID=2943b3d5-da14-4d97-8cd8-7fc8b1673020 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2943b3d5-da14-4d97-8cd8-7fc8b1673020 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2943b3d5-da14-4d97-8cd8-7fc8b1673020 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

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
chainloader	+1

---

### Post by philinux on 2007-12-08
if you can now browse the /boot/grub directory there should be a menu.lst~ this is the back up file, there may be others check the date stamp. You can use the backup to replace the bust one if it looks right.

mine looks like this.
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=vga=792 splash

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 ro vga=792 splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by Mramius on 2007-12-08
There is no backup file.

---

### Post by Mramius on 2007-12-08
But our drives are different.  What information do I need from fdisk -l to enter into this menu file?

---

### Post by philinux on 2007-12-08
I'd just reinstall grub from your live cd. Extract from 

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

```
Re-install GRUB with Live CD,
This method is also the best method to use from a hard disk installed operating system.
It can be done from a GRUB floppy disk too, or from GRUB's Command Line Interface or just about anywhere there is already a GRUB installation present with the necessary GRUB files.

You can use this to install GRUB to anywhere too, it doesn't have to be only to the MBR of a first hard disk. GRUB can be installed to any other hard disk, or to a usbdisk, or floppy disk this way.

The most common use for this operation is to fix your MBR after a Windows re-install has corrupted your MBR with the IPL for the Windows bootloader, so you can only boot Windows.

herman@red~:$ sudo grub

     GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
                  completions.  Anywhere else TAB lists the possible
                  completions of a device/filename. ]

grub>_
I typed 'sudo grub' and pressed 'Enter'.
In Ubuntu,  it is important  to use the 'sudo' preface to the 'grub' command. If not, you will get what appears to be a GRUB shell, but you won't be able to do very much with it. You will probably get some confusing error messages.

This is an example of one use of a GRUB shell.  I know this is a GRUB shell, because it has a GRUB prompt, like this, 'grub>_'    

grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Here, I typed 'find /boot/grub/stage1' because I want to find out which partitions in my computer have GRUB installed in them, (just to remind me).
This gives me a clue as to exactly where the necessary GRUB files may be located that I can install GRUB from.

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

The 'root (hd0,1) will tell GRUB which operating system partition contains the GRUB I want to install from.  
It has to be one of the ones listed by the 'find' command (above).

The GRUB menu from the operating system's /boot/grub/menu.lst that I installed grub from is the one that will appear on boot up.
In other words, if (hd0,1) contians Ubuntu, and I install GRUB from (hd0,1), I'll get Ubuntu's GRUB menu on boot up.
If (hd0,3) contians Kubuntu, and I install GRUB from (hd0,3), I'll get Kubuntu's GRUB menu on boot up.

GRUB should recognize the filesystem, and will reply with an output similar to the one shown above. If not, then check to make sure you didn't make a mistake.


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

The 'setup' command is the command that tells GRUB exactly where to install Grub to.

Installing GRUB to MBR:
'setup (hd0)' is the command to install Grub's stage1 to MBR.
Stage1_5 will also be installed to the 15 sectors following the MBR in the first track of the hard disk.
Installing GRUB to a partition:
It is also a good idea to install GRUB to the first sector of a Linux operating system's partition too, (I'm not sure about what you would do if you had a separate /boot partition, install to that instead I presume). To install GRUB to a partition, you would use a command like, 'setup (hd0,1), or 'setup (hd0,3)', where (hd0,1) and (hd0,3) are Linux partitions. If you do that, you should be able to 'chainload' your operating system in an emergency.
Installing GRUB to a non-first MBR:
If you have more than one hard disk in your computer, the BIOS normally looks for booting information only in the MBR of whichever disk the BIOS thinks is the first hard disk. However, you can also install GRUB to the MBR of your other hard disks as well, and this means the other hard disks can be chainloaded too. To install GRUB to a second hard disk, you would use 'setup (hd1)', and for a third hard disk 'setup (hd2)', and so on.
Installing GRUB to a floppy disk:
That's a seperate subject, covered further down this page.
How to make your own personalized GRUB Floppy Disk........................................ GO
Installing GRUB to a usbdisk:
That's another seperate subject, also covered further down this page.
How to add GRUB to your USB thumb drive...........................................................GO



grub> quit

This is just to take you back to the regular terminal prompt again.
```

---

### Post by Mramius on 2007-12-08
Does anyone know how to fix this problem?

---

### Post by ronmarley1 on 2007-12-08
The easiest thing to do, in my opinion, would be to download the iso of the SuperGrubDisk from here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Burn the iso to a CD.
Boot the CD and follow the menu prompts to recover your GRUB.
It'll restore your GRUB and tell you to remove the CD and reboot and GRUB will be back.
It's fix GRUB for me quite a few times, since I had a issue where whenever I booted Windows, GRUB would be corrupted.  Eventually, I had to use the Windows bootloader.  This link: [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) describes how to do that.  Hopefully this is just a one-time problem for you.

---

### Post by Mramius on 2007-12-08
I tried the supergrub CD and all it did was bring me to a grub command prompt when I booted to it.

I followed the instructions at the supergrub site for command prompt help but it did nothing.

As you can see, hd2 is where Linux is installed, hd2 is where grub is and everything else.  It just won't load!

---

### Post by philinux on 2007-12-08
Thats exactly what i said in post three.

But I'd still try reinstalling from the live cd, nothing to loose.

---

### Post by Mramius on 2007-12-08
Try reinstalling the entire linux operating system?  That seems crazy to me.

If you mean just reinstalling grub, I did and it changed nothing.

---

### Post by philinux on 2007-12-08
Yes I meant just reinstalling GRUB.

---

### Post by Mramius on 2007-12-08
It did nothing.  I did it from the Synaptic Package Manager...was that the wrong way to do it?

---

### Post by philinux on 2007-12-08
You have to follow the instruction from my previous post from the live cd using the terminal.

Unless some grub guru expert pops up with advice. :) I've only used the method as described in post #16

---

### Post by torgrot on 2007-12-08
Reboot, when you get to the grub menu hit esc.  Press "e" to edit the command line in grub.  Scoll to the kernel line and press "e" again.  Use the arrow key to get to the end of the kernel line and add this without the quotes "acpi=ht pci=biosirq" Then press enter and "b" to boot.  I have to add this on my dell to prevent the constant reboot cycle.

torgrot

---

### Post by Mramius on 2007-12-08
lol, there is no grub menu.  Grub isn't loading.

Anyway, following your instructions here is where I end:

```
grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)

grub> 
```

So, after telling it which partition contains the grub I want to install from it does nothing, where it's supposed to report on it's file system.  The page says, if it doesn't reply with the file system type, I've made a mistake.

How can I possibly be making a mistake here??

---

### Post by philinux on 2007-12-08
Did you use 

sudo grub

---

### Post by Mramius on 2007-12-08
Yes.

I'm in the supergrub cd now...

I'm able to get the menu.lst to pop up by doing
```
grub>  configfile (hd2,0)/boot/grub/menu.lst
```

but, when I select the OS I want to load it says disk does not exist.

---

### Post by Mramius on 2007-12-08
I was able to boot by doing "chainloader +1" from the instructions on that page you gave me.

However, I'm absolutely petrified to turn off or reboot my computer.  Am I going to have to go through that process every time now?

What caused this?  Windows?  Linux?  Linux making it seem like Windows did it so that I'll hate Windows?

This was a maddening endeavor.

---

### Post by philinux on 2007-12-08
Not sure why this happened but as the wise one said, don't panic.

You're only messing with grub, all you stuff is intact windoze and linux.

---

### Post by Mramius on 2007-12-08
Will this happen again if I boot to Windows?

---

