---
title: "[SOLVED] GpartEd - Can anyone ID these partitions?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2007-10-20
Hey all,

I want to back up both my partitions (Windows XP & Ubuntu 7.10) in a 'copy/paste' fashion using this article:

[here]("http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php")

Then resize the partitions so they're not crazy looking like this:

[http://s65.photobucket.com/albums/h235/themangoduck/Ubuntu/?action=view&current=screenshot-1.jpg]("http://s65.photobucket.com/albums/h235/themangoduck/Ubuntu/?action=view&current=screenshot-1.jpg")

Can anyone give me information as to what's what here in this pic (specifically which partition is which OS) - any help is greatly appreciated you guys have been fantastic.  I only hope to help someone one day.

---

### Post by bruce89 on 2007-10-20
I can't see anything there.

---

### Post by AnLGP on 2007-10-20
Try the link that's there now

---

### Post by kellemes on 2007-10-20
I see you have one FAT32 partition with boot-flag enabled (4 Gb) and one NTFS partition (142 Gb)
I assume your Windows-install is on the FAT32-partition..?
Maybe you should start Windows and check through explorer the size of your C: drive.. if it's about 4Gb.. that's where Windows is installed.
Is the NTFS-drive maybe where you store mediafiles etc?

Also I see one ext3 partition (41Gb), that's where Ubuntu is!
The Swap-partition is also used by Ubuntu. Is pointless to backup.

---

### Post by FuturePilot on 2007-10-20
Starting at the left, the first one is a FAT32 partition which could possibly be a Windows backup partition or just a storage partition. The next one, the biggest one, is Windows as it's formatted as NTFS. The third one (41.24 GB) is a Linux partition. The 4th one, isn't a partition at all. It's empty space. And the very last one on the far right is a swap partition.

---

### Post by kellemes on 2007-10-20
> **FuturePilot said:**
> Starting at the left, the first one is a FAT32 partition which could possibly be a Windows backup partition or just a storage partition. The next one, the biggest one, is Windows as it's formatted as NTFS.

Sorry, I really feel this needs to be checked by OP.
The FAT32-partition has the bootflag. This may be seen as a hint. :popcorn:

---

### Post by AnLGP on 2007-10-20
Thanks Futurepilot & Everyone.

Is there any way to check what is on these partitions?  I have a bit of a problem dual booting my OSes to which you can read below:

[http://ubuntuforums.org/showthread.php?t=580996]("http://ubuntuforums.org/showthread.php?t=580996")

---

### Post by lyndaj70 on 2007-10-20
There is one hard disk installed... My sata drive is called sda as well so I'm going to guess you have a SATA drive as well,,,,

ON that drive, you have three Primary paritiions, and one extended partition which contains the Linux swap file.....

There is also roughly 42 GB of free space on this drive.. space you could claim and add to your filesystem when you want to grow.....

The Fat32, I'm thinking is a system restore partition.... if this system is an OEM (like Compaq, for instance) than that is definitely what it is... Compaq almost ALWAYS has a fat32 restore partition.... honestly can't remember seeing a CompaqPC that "didn't" have one unless it had been tinkered with or a HDD had crashed.....

NTFS is where Windows is installed, Could be Xp, Vista, 2K... I can't determine that of course (grin).

the ext3 is your root partition for linux.... roughly 42GB in size (these sizes in the pic are in gibibytes, which are binary and show smaller sizes than standard gigabytes.....

the extended, if you will notice, is the same size as the swap.  That is because they are one and the same, but the file system has to report it as being two partitions.....  So basically you can't mount or do anything with sda4 because it is filled with sda5 (hope that makes sense)..

Instead of resizing, why not claim that 42 GB of open space (unallocated) and mount that into your filesystem?  It would be easier and a whole lot safer than resizing....

Hope this helps,
~L

---

### Post by FuturePilot on 2007-10-20
> **kellemes said:**
> Sorry, I really feel this needs to be checked by OP.
The FAT32-partition has the bootflag. This may be seen as a hint. :popcorn:

Oh, sorry, didn't see that there. Anyways I was pretty much guessing on those two.

---

### Post by ddrichardson on 2007-10-20
> **lyndaj70 said:**
> Instead of resizing, why not claim that 42 GB of open space (unallocated) and mount that into your filesystem?  It would be easier and a whole lot safer than resizing....

Hope this helps,
~L

He can't do this because of the four partition limit. You could however expand the logical to include the unallocated space.

---

### Post by AnLGP on 2007-10-20
Any threads on how I would go about doing this?  Thanks everyone : )

---

### Post by ddrichardson on 2007-10-21
> **AnLGP said:**
> Any threads on how I would go about doing this?  Thanks everyone : )What exactly is it you want to do?

---

### Post by AnLGP on 2007-10-21
> why not claim that 42 GB of open space (unallocated) and mount that into your filesystem?

that

and also -

clean up the way it looks.  I only  have two OSes installed on this computer and there's four partitions.  I believe I messed something up when I installed linux.  There's another post to it which I've linked to earlier in this thread.

Thanks.

---

### Post by ddrichardson on 2007-10-21
Boot the Live CD, run gparted and resize the Linux partition to take up the unallocated space.

---

### Post by AnLGP on 2007-10-22
I 'solved' this prematurely.  I was in #ubuntuforms on xchat and someone said this:

<them> one of the problems with resizing partitions is that they have to be contiguous
<them> you can't join space at the beginning of the disk with a partition at the ened
<them> end*
<steve__> I just chose 'default' when I installed Ubuntu as I didn't know what I was doing
<them> but how did your dual boot get screwed up? did you install windows after ubuntu?
<them> oh...yeah, i don't care for "guided" partitioning.
<steve__> No, ubuntu after windows.  I had to reinstall windows because it wouldn't boot from the menu
<them> ok, so by reinstalling it you replaced GRUB with NTLDR on the MBR

--

I have no idea what that last sentance means but that's fine by me if someone can tell me how to go about fixing it?  

NOTE:  changed name to 'them' to protect the innocent.

I want to make the partitions as equal as I can and be able to boot from GRUB.  one person has said to allocate the unused space and I plan to do that but my boot menu is messed up.  see screenshot earlier in the post.  Sorry for marking it premature and thanks.

---

### Post by ddrichardson on 2007-10-22
Windows uses a small program called ntldr rather than grub which Ubuntu use. When you install Windows, it doesn't care whether you have another OS installed it overwrites an area of your hard disk known as the master boot record with its own - this prevents other installed os' booting.

There are a lot of threads already about restoring grub, such as [this]("http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub").

---

### Post by AnLGP on 2007-10-22
Windows is the OS not booting from GRUB.  It boots fine from [Super Grub Disc]("http://supergrub.forjamari.linex.org/") but I don't want to have to use that disc to choose between linux and windows all the time.  I'd rather it be able to work from the boot.  Is there a way I can take screenshots of my boot menu without running a virtual machine or taking camera pics?

---

### Post by ddrichardson on 2007-10-22
How about just posting the contents of /etc/grub/menu.lst?

---

### Post by AnLGP on 2007-10-22
How?

---

### Post by ddrichardson on 2007-10-22
Boot into Ubuntu and then paste the output of:```
cat /boot/grub/menu.lst
```

---

### Post by AnLGP on 2007-10-22
see below - double post.

---

### Post by AnLGP on 2007-10-22
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Ubuntu
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

---

### Post by ddrichardson on 2007-10-22
Can you also give the output of```
fdisk -l
```

---

### Post by AnLGP on 2007-10-22
I would if it would let me.  Here's what happens

```
steve@steve-desktop:~$ fdisk -l
steve@steve-desktop:~$
```

---

### Post by ddrichardson on 2007-10-22
Oops sorry - ```
sudo fdisk -l
```

---

### Post by AnLGP on 2007-10-22
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             573       19183   149492857+   7  HPFS/NTFS
/dev/sda2   *           1         572     4594558+   b  W95 FAT32
/dev/sda3           19184       24567    43246980   83  Linux
/dev/sda4           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Like I said I only have two OSes, windows XP and Ubuntu 7.10.  I had to re-install XP after installing ubuntu w/the default partition option on the disc.  XP won't boot from GRUB and I have to use SGD.  Thanks for your help thusfar.  We'll get this : )

---

### Post by ddrichardson on 2007-10-22
I *think* you have the wrong partition for Windows but am a little confused by your layout. Are you sure Windows boots from sda2 - the fat32 partition, because it seems a little small for a Windows XP partition and they are normally NTFS.

If that is the case and the NTFS partition is Windows then you  need to change the last section of menu.lst to:```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,[COLOR=Red]0[/COLOR])
savedefault
makeactive
chainloader     +1
```

---

### Post by AnLGP on 2007-10-22
Are you sure Windows boots from sda2 - the fat32 partition

-

I don't know what you mean by this - short answer:  no.  I am confused by my layout as well as I didn't intend to have that many partitions on there.  I only wanted one for XP and one for Ubuntu with (maybe) the option to have one to back up each system (but I didn't know this was a good idea until **after** I installed ubuntu & it looks to me (& correct me if I'm wrong) if there's 4 or 5 there?

---

### Post by ddrichardson on 2007-10-22
No there are four. One of the limitations to partitions was that you could only have four on a drive. Then logical partitions were invented which can contain four extended partitions inside them, in this case your swap partition is such an extended partition inside a logical.

Try altering menu.lst as I suggested to confirm which drive is the actual boot drive for Windows.

---

### Post by AnLGP on 2007-10-22
How?  : )

EDIT:

found out how but it won't let me edit.  it says I don't have permissions. 

Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.

Should I back up files before doing this?

---

### Post by ddrichardson on 2007-10-22
Yes backup,```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```You need to edit this file as sudo```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by AnLGP on 2007-10-22
I changed the menu from 1 to a 0 and it still did the same thing (XP didn't boot from GRUB) but still boots from SGD (I'm on windows now).  I wonder if there's a way to fix this - or should I just get rid of XP?  The only thing I do on XP that I don't do on linux is record - and I can't get rosegarden to work for linux.  If I were to choose to get rid of XP is there a way to do it without reinstalling ubuntu?

---

### Post by ddrichardson on 2007-10-22
Your setup is wierd. I have no idea why you have a fat32 partition set with a boot flag. If you need XP it might be better to start from scratch that way you can have the drive layout you are looking for and dual boot.

---

### Post by AnLGP on 2007-10-22
I have no real need for XP.  I have no idea why I have a fat32 partition set with a boot flag either.  I dont even know what that means.  Thanks for your help all the same :)

---

### Post by ddrichardson on 2007-10-22
Boot flags are used when the MBR searches for which partition to boot. It isn't normally set of a fat32 partition for XP

---

### Post by AnLGP on 2007-10-22
Do you have any kind of an idea as to what could be going on?  

Someone earlier mentioned a boot flag but I still don't understand why XP boots fine from SGD but won't boot from the GRUB menu.

---

### Post by meierfra on 2007-10-22
I don't understand why you can't boot into Windows. But I do know why the Fat 32 partition had a boot flag. Grub sets the boot flag whenever you use "makeactive". So 

title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

caused grub to set the boot flag for  your Fat 32 partition (hd0,1).

Actually now that you changed "root  (hd0,1) " to "root (hd0,0)"  grub should have moved the boot flag to the NFTS partition (hd0,0). 

To solve your boot problem:   Do you get any error messages when trying to boot into Windows? Could you post your current "menu.lst" so that we can look for misprints?

---

### Post by AnLGP on 2007-10-22
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Ubuntu
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

There's the menu list.  Going to go take a screenshot of what happens when I boot windows from GRUB.

---

### Post by meierfra on 2007-10-22
I'm confused. Your menu.lst  still says

title           Windows NT/2000/XP
root            (hd0,1)

did you try " root   (hd0,0)"  and then changed it back to "root (hd0,1")?

---

### Post by AnLGP on 2007-10-22
I did not change it back.  EDIT - > wow.  OK I don't know why but it did get changed back.  I believe I have it edited.  Code will follow below:

[here is my loading of windows off GRUB]("http://i65.photobucket.com/albums/h235/themangoduck/1022071746.jpg").  If you can't read it this is what it says:

Prepairing System Recovery Options.  

XP boots fine from Super Grub Disc.

Code here:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=793eede3-0844-4b9e-8b58-1f9b8c3f8908 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Ubuntu
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by meierfra on 2007-10-22
It seems you are trying to boot into the  Fat32 recovery partition. 

You need to change "root (hd0,1)" to "root (hd0,0)" via 

"sudo gedit /boot/grub/menu.lst"

---

### Post by AnLGP on 2007-10-22
I did that.  It worked!  Thanks everyone : ).  SOLVED.

---

### Post by meierfra on 2007-10-22
Sorry posted my last message before I saw your edit.

Is it working now that you  changed "(hd0,1)" to "(hd0,0)"

---

### Post by meierfra on 2007-10-22
Good news.


 I also recommend that you delete 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Ubuntu
root            (hd0,0)
savedefault
makeactive
chainloader     +1


from your menu.lst. Must be left over from a old ubuntu partition that no longer exists.

---

### Post by AnLGP on 2007-10-22
That was from when I was running wubi

---

