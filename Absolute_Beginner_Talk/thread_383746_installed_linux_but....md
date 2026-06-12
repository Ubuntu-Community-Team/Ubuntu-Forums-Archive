---
title: "installed linux but..."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-13
hey everyone i installed linux but for some reason windows xp wont start now. it gives me a reg error when i try to boot into windows but im not worried about that anymore. is there a way to get my files from windows without booting into windows cause i mustof did somthing wrong with the parition. 

also id like to know where to find that wine program that can run windows applications everyones been talking about. 

thanks.

---

### Post by Najand on 2007-03-13
Try to copy/paste the output of the following  command here:
```

sudo fdisk -l

```
Then we can see how we can help you.

---

### Post by Najand on 2007-03-13
To install wine, First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
Next, add the repository to your system's list of APT sources using the following command:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

```

---

### Post by noob_saioke45601 on 2007-03-13
thanks.

---

### Post by lorodft on 2007-03-13
hello. I have a simmilar problem. I can't make windows to boot. Because it doesn't even shows the list of my OS to chose from. It just goes ahead and boots ubuntu.

After writing "sudo fdisk -l" as Najand said, I get :

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1021     8201151   83  Linux
/dev/hda2            1022        4863    30860865    f  W95 Ext'd (LBA)
/dev/hda5            1022        4863    30860833+   b  W95 FAT32

what is wine?

Any help is greatly appreciated, as I have some important data on my winXP.

Thanks.

---

### Post by Najand on 2007-03-13
It seems during installation, it could not recognize your Windows partition on /dev/hda5. 
Check /boor/grub/menu.lst to  see if it has been installed or not? If you don't  know how, copy/paste it here for us to help you.

---

### Post by lorodft on 2007-03-14
Thank you for your reply.

Here is my menu.lst :

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```




I spent all night on these forums, but found nothing usseful. Please help me !!

---

### Post by IYY on 2007-03-14
Does GRUB (the text-based menu that lets you select which OS you wish to boot into) show up, or does it just go straight to Ubuntu? What's the error message Windows is throwing? 

I've seen a few cases where Windows behaved *very* strangely. It absolutely refused to boot when Ubuntu was installed, and only when I completely removed Ubuntu (just wiping the MBR didn't fix it!) did Windows start working again. Very odd.

---

### Post by lorodft on 2007-03-14
GRUB shows up at startup, with the entries from   menu.lst   I posted above.
Why doesn't the WindowsXP option appear in that list?
I want both Ubuntu + WinXP to work.

Any suggestions ?:confused:

---

### Post by nightwolf2k5 on 2007-03-14
did u install ubuntu on ur c drive or ur drive that u installed windows on?

---

### Post by lorodft on 2007-03-14
I installed ubuntu on C:/ and WinXP is on D:/

---

### Post by koshari on 2007-03-14
> Device Boot Start End Blocks Id System
/dev/hda1 * 1 1021 8201151 83 Linux
/dev/hda2 1022 4863 30860865 f W95 Ext'd (LBA)
/dev/hda5 1022 4863 30860833+ b W95 FAT32


you say you installed windows on D drive, i are guessing you had a windows partition called D. this is different to having a second hard drive, and Linux is seeing the partition as hda5 (hard drive A - partition 5)

> 
what is wine?
wine is a platform run in linux that tries to faithfully reproduce the runtime environment of windows from within linux. it runs various windows applications with varying degrees of success.

---

### Post by lorodft on 2007-03-14
> you say you installed windows on D drive, i are guessing you had a windows partition called D. this is different to having a second hard drive, and Linux is seeing the partition as hda5 (hard drive A - partition 5)

There is only 1 drive, with 2 partitons. c:\ and d:\
Ok, and what does that mean ? Is it good or bad ? Should I worry :D :( ?

---

### Post by Najand on 2007-03-14
Add this to the end of your "/boot/grub/menu.lst" file:
```
title		Microsoft Windows 95/98/NT/2000/XP/VISTA
root		(hd0,4)
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1
```

---

### Post by lorodft on 2007-03-14
I tried that, and it says :

```

root (hd0,4)
   Filesystem type is fat, partition tyoe 0xb
makeactive

Error 12: Invalid device requested

```


Now I decided to take it from zero. I want to reinstall everything.
Please tell me if these steps look right to you :

I have a 40 GB hard-disk.
I will make 3 partitions using the Ubuntu Install CD :
  1. C:\     -     Will be used for WindowsXp ( 20 GB - FAT32 )
  2. D:\     -     Will be used as SWAP for Linux ( 2 GB - ext3 ?? )
  3. E:\     -     Will be used for Ubuntu ( 18 GB - ext3 ?? )
Then I will continue with the Ubuntu installation and install to E:\
Then I will install WindowsXP to C:\

Hopefully I will get both OS in my boot list to chose from.
What do you think ?
Cheers.

---

### Post by mikesignguy on 2007-03-14
Don't reinstall anything... you are a few steps away...hang tight

---

### Post by lorodft on 2007-03-15
So, I reinstalled Windows, primary because I had to print more than 150 pages, and my Ubuntu wasn't getting along to good with my printer.

Now, I have to reinstall Ubuntu too.
I have two questions:

1). If I install Ubuntu on a FAT32 partition, would I experience problems ? 
I want Windows to read that partition.
2). Is the SWAP partition necessary or just recommended ?

Also, if you can give me other suggestions at 1) it would be great.

Thanks.

---

### Post by dstew on 2007-03-15
All you had to do was put the map statements before the root statement.

Anyway, since you reinstalled Windows:

1. No, you cannot install Ubuntu on a FAT32 partition. Ubuntu is a linux system, and uses ext2 or ext3 file systems. But you can access a FAT32 partition to read and write files from both linux and Windows. Suggestions: 20gb FAT32 for Windows as first partition, 18gb linux root partition, 2 gb linux swap partition.

2. The swap partition is not absolutely necessary, but it is important for good functioning.

---

### Post by lorodft on 2007-03-15
Thanks for the replies.

I would gladly use your suggestion, but I have the partitions set up different.
I have the partitions as follows:

b:   free space -                                    10 GB
c:   fat32 (needed by windows) -             8 Gb
g:   fat32 (where windows is installed). -   22 Gb

if I install Ubuntu in b:/ how do I setup it in the partition manager ?

b:     as / (root)
c:     as what ??
g:     as /windows

I think I'll spit b: and make another partition for swap.

How does it look ?

Thanks.

---

### Post by dstew on 2007-03-15
Yes, make two partitions out of the free space, a big one for linux /, and a small one for linux swap.

---

### Post by jhenager on 2007-03-15
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
 Follow the instructions on Bart's site to create a bootable CD. That will allow you to read your NTFS partition. Can't say enough about this utility. It saves my butt day after day here at work.

---

### Post by lorodft on 2007-03-17
Ok, I've installed windows again and ubuntu.

I get a "hal.dll not found" error.

I've tried to follow the instruction on this topic : [http://www.ubuntuforums.org/showthread.php?t=73254](http://www.ubuntuforums.org/showthread.php?t=73254) (the thomsuey advice)
and all went fine untill the step :

" sudo ntfscp /dev/hda2 /home/andrei25ni/boot.ini boot.ini "

I get : "Use the force option to work a mounted filesystem.
ERROR: couldn't mount volume: No such file or directory".

How do I mount ? How can I replace the boot.ini file from my ubuntu partition to the windows partition ? what is the force option for a mount ?

here are some additional data that may be usseful in helping me :

```

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         890     7148893+  83  Linux
/dev/hda2   *        1022        2041     8193150    7  HPFS/NTFS
/dev/hda3            2042        4862    22659682+   f  W95 Ext'd (LBA)
/dev/hda4             891        1021     1052257+  82  Linux swap / Solaris
/dev/hda5            2042        4862    22659651    b  W95 FAT32

```

Is there any way to dix this ?
Please help.
Thank you.

---

### Post by lorodft on 2007-03-17
i found out that -f is the force command but nothing happens.

Is there any way to replace that boot.ini file ??

---

### Post by lorodft on 2007-03-17
Ok. I fixed it. It works now.
I had to do 
```

del c:\boot.ini
bootcfg /rebuild
fixboot
exit

```

from within the windows boot cd, Recovery console (r)

And now it works! I can login to Ubuntu or Windows. Yay!!


Thank you all for the responses !\\:D/ =D> 
*goes and explores ubuntu*

---

