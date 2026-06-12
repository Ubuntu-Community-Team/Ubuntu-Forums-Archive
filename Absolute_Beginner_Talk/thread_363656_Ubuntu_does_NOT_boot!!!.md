---
title: "Ubuntu does NOT boot!!!"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-17
Hello all!

After the new experience with [color=blue]Ubuntu v7.04 - Herd 3[/color], here:
[http://ubuntuforums.org/showthread.php?t=353467](http://ubuntuforums.org/showthread.php?t=353467)

I decided to go back to [color=blue]Ubuntu v6.10[/color].

So, I installed Ubuntu v6.10 on a Hard Drive.
At the same time all my Backup files are on a separate Hard Drive Partitioned as NTFS.
I access those files through "[color=blue]ntfs-3g[/color]".

I have the following problem:
When I boot my Ubuntu from the Ubuntu Hard Drive, everything is ok.
When I boot my Ubuntu from the Ubuntu Hard Drive, and at the same time the NTFS Hard Drive is connected (which has **NO** Windows OS installed), I get the following:

```
GRUB LOADING STAGE 1.5.
GRUB loading, please wait...
Press "ESC" to enter the menu...

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)
```

...and Ubuntu does NOT boot!!!

When I remove the Ubuntu Hard Drive & try to boot using _only_ the NTFS Hard Drive, which by the way contains NO Windows OS, I get the following:

```
GRUB LOADING STAGE 1.5.
GRUB loading, please wait...

Error 17
```

...bump :confused: 
It seems to me that Ubuntu again has tampered the Windows NTFS Hard Drive's MBR, even though the Windows NTFS Hard Drive contains **NO** Windows OS...
It is just an NTFS backup of my files...

That sucks!!!
How can I fix that?
Should I try to fix the MBR of a Windows NTFS Hard Drive that does NOT contain any Windows OS?

When I tried to use the [color=blue]Windows XP XP2 Install CD-Rom[/color] & selected "R" ([color=red]repair[/color]), I got to the following screen:

```
Microsoft Windows XP (TM) Recovery Console.
The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.

C:|> [color=blue]fixmbr[/color]

**CAUTION**
[color=red]This computer appears to have a non-standard or invalid master boot record.
FIXMBR may damage your partition tables if you proceed.
This could cause all the partitions on the current hard disk to be inaccessible.[/color]
If you are not having problems accessing your drive, do not continue.
Are you sure you want to write a new MBR?

```

The above does NOT look pretty!!!
What if I loose the ability to access my files?
I don't have a backup...
And I can access my files fine from WindowsXP.
Why does Ubuntu have to _always_ tamper Hard Drives containing Windows, while I explicitly said during the install that I want to install Ubuntu on a separate Hard Drive?
And things are even worse:

The Windows Hard Drive did NOT even contain a Windows OS!!!
It was just an NTFS Hard Drive containing just files...
Why did it tamper it in the first place?

What do I do now?

_Questions_:
1. Is it dangerous to apply "fixmbr" on a Windows NTFS Partition that does NOT contain any Windows OS?
2. Is there a chance that I loose files OR not being able to access them?

Thanks.

---

### Post by undertakingyou on 2007-02-17
Has the NTFS drive ever had Windows or any other OS installed on it?

---

### Post by Duck2006 on 2007-02-17
> Questions:
1. Is it dangerous to apply "fixmbr" on a Windows NTFS Partition that does NOT contain any Windows OS?
2. Is there a chance that I loose files OR not being able to access them?

Your partition will be ok, all your doing is fixing your MBR, so your files will be ok.

---

### Post by undertakingyou on 2007-02-17
I was also just thinking.  Was the drive in when you did your most recent install of Edgy?  When you have the drive in while you do an install it asks you where to mount the drive.  Can you go in and give the drive a mount point before you put the drive in and then install it?  I wonder if that might do something.

---

### Post by dvarsam on 2007-02-17
[QUOTE=undertakingyou]Has the NTFS drive ever had Windows or any other OS installed on it?[/QUOTE]

Yes it had, about a month ago...
But I have cleanly formatted the Hard Drive (all the way - not the "quick" format) & now use it _only_ to save my files...
Currently, there is NO Windows OS installed on it...

I think it is related on the "faulty" way Ubuntu gets installed...
I.e. IF Ubuntu install detects an NTFS Hard Drive, it does NOT check whether the Hard Drive truly contains a Windows OS...
... it just "stupidly" goes & tampers an MBR as long as an NTFS Filesystem is detected!!!

That sucks!

And it does NOT care IF the user "explicitly" orders Ubuntu to install on a separate Hard Drive...
... IF it detects an NTFS Hard Drive, it is going to tamper it...!!! :(

---

### Post by dvarsam on 2007-02-17
[QUOTE=undertakingyou]I was also just thinking.  Was the drive in when you did your most recent install of Edgy?  When you have the drive in while you do an install it asks you where to mount the drive.[/quote]

It probably was...
My mistake!
However, **I specifically told Ubuntu to install hte Ubuntu v6.10 OS, on a diff Hard Drive**...
I don't understand why it _must_ tamper any NTFS Hard Drive detected... :confused:
This is a true example of BAD PROGRAMMING CODE!!!

[QUOTE=understandingyou]Can you go in and give the drive a mount point before you put the drive in and then install it?
I wonder if that might do something.[/QUOTE]

What do you mean?
I don't understand...

Thanks.

---

### Post by rccharles on 2007-02-17
> **dvarsam said:**
> 

I have the following problem:
When I boot my Ubuntu from the Ubuntu Hard Drive, everything is ok.
When I boot my Ubuntu from the Ubuntu Hard Drive, and at the same time the NTFS Hard Drive is connected (which has **NO** Windows OS installed), I get the following:



When I tried to use the [color=blue]Windows XP XP2 Install CD-Rom[/color] & selected "R" ([color=red]repair[/color]), I got to the following screen:

```
Microsoft Windows XP (TM) Recovery Console.
The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.

C:|> [color=blue]fixmbr[/color]

**CAUTION**
[color=red]This computer appears to have a non-standard or invalid master boot record.
FIXMBR may damage your partition tables if you proceed.
This could cause all the partitions on the current hard disk to be inaccessible.[/color]
If you are not having problems accessing your drive, do not continue.
Are you sure you want to write a new MBR?

```

The above does NOT look pretty!!!


I would not mess with the MBR of the harddrive with NTFS on it.  You do not need it to boot your system.  You should be able to boot fine with the GRUB mbr on you Ubuntu disk.

You should check the jumpers on your harddrives.  Are you using cable select on the harddrives?  I do not know exactly how cable select works.  It could be switching around the order of your harddrives when you attach the ntfs drive.

You need to check out your bios to see what the boot order is.  Usually, you get into bios by pressing esc, del, f2, or someother function key just after poweron. I'd set up bios to only boot from your ubuntu disk.

How is grub configured?  You might want to copy /boot/grub/menu.lst here.

Do you select which OS you will be booting or do you let it boot automatically.

Does the grub menu come up?  

If you do not get a grub menu, I suggest you press esc just after bios completes running which runs when you poweron.  You have three seconds I think by default.  Select Ubuntu.

Robert

---

### Post by undertakingyou on 2007-02-17
To give it a mount point, you must edit the /ect/fstab file.  In there it should identify the drive, where it mounts, what it uses to mount, and any other instructions it may need.  Does it mount there.  Also, it is a good idea to look at the GRUB menu and see where that is pointing.  It does it by relative paths, not drive ID so if you move the drive to a different IDE location, it doesn't like it.

---

### Post by dvarsam on 2007-02-18
[QUOTE=rccharles]I would not mess with the MBR of the harddrive with NTFS on it.  You do not need it to boot your system.  You should be able to boot fine with the GRUB mbr on you Ubuntu disk.[/quote]

Even though I don't need this NTFS Hard Drive be plugged to boot Ubuntu (since Ubuntu can boot from its own Hard Drive), **IF I don't do it**... later I wont be able to access my files...
i.e. In Windows, Sata Hard Drives can be Hot-plugged (after boot) & they can be accessed just by refreshing Device Manager...
In Ubuntu IF I boot my PC & hot plug my Sata Hard Drive afterwords, no matter what I try - e.g. "mount -a" - the newly added Hard Drive does NOT get mounted!!!

So IF I don't plug-in the Hard Drive **before I boot** my System, how will I be able to access my files man?


[quote=rccharles]You should check the jumpers on your harddrives.  Are you using cable select on the harddrives?  I do not know exactly how cable select works.  It could be switching around the order of your harddrives when you attach the ntfs drive.[/quote]

Sata Hard Drives don't have jumpers...

[quote=rccharles]You need to check out your bios to see what the boot order is.  Usually, you get into bios by pressing esc, del, f2, or someother function key just after poweron. I'd set up bios to only boot from your ubuntu disk.[/quote]

I have already done this!
I tell it to boot from the Ubuntu OS Hard Drive.
NOT from the other NTFS (without OS) Hard Drive.

Still, for some reason it won't work!
Also, I plugged the Sata's Data Cable on a diff Sata plug on the Mobo...
Nothing changed!

[quote=rccharles]How is grub configured?
You might want to copy /boot/grub/menu.lst here.

Do you select which OS you will be booting or do you let it boot automatically.

Does the grub menu come up?[/quote]

Sorry man, but what are you talking about?
There is _only_ one OS -> the Ubuntu OS!!!
As I said before, the other Hard Drive is OS empty!!!
It is NTFS formatted & contains only my personal files!
So I do NOT understand why the contents of the file "[color=blue]/boot/grub/menu.lst[/color]" are needed...

[quote=rccharles]If you do not get a grub menu, I suggest you press esc just after bios completes running which runs when you poweron.  You have three seconds I think by default.  Select Ubuntu.
[/QUOTE]

I don't get a grub menu when booting...
Why should I (when there is only one OS installed on the Hard Drive)?
Thanks.

---

### Post by dvarsam on 2007-02-18
Anyway, here are the contents of the file "[color=blue]/boot/grub/menu.lst[/color]":

```
root@dimitris-desktop:/boot/grub# cat menu.lst
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
timeout         3

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
# kopt=root=UUID=fe579a42-11ea-452c-bcd0-efcd03f07cbe ro
# kopt_2_6=root=/dev/sda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Can you figure anything out?
Thanks.

---

### Post by bulldog on 2007-02-18
Tell me the outcome of```
sudo fdisk -l
``` and tell me on which hdd is grub installed.
I need to know from which disk you're booting [don't have the time to read all your postings]

If I have this info I probably can tell you what's wrong.

ps,you can learn a lot by reading and understanding,ubuntu isn't that hard.

---

### Post by dvarsam on 2007-02-18
I got tired of all of this...
I got impatient & decided to run "[color=blue]fixmbr[/color]" on the NTFS Hard Drive.
I had never done this before...
And was scared of that warning...
So I did it & restarted the PC... & got this again:

```
GRUB LOADING STAGE 1.5.
GRUB loading, please wait...
Press "ESC" to enter the menu...

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)
```

I was now sure that it was not due to MBR of the NTFS hard drive...
So I opened the box & changed the Hard Drive's Sata data wire to some other Sata data slot on the Mobo.
Everything is working fine now...
Thank you all for your help!

---

### Post by undertakingyou on 2007-02-18
Glad its working.

---

### Post by rccharles on 2007-02-19
Edit: Glad you got it working. 
> **dvarsam said:**
> Even though I don't need this NTFS Hard Drive be plugged to boot Ubuntu (since Ubuntu can boot from its own Hard Drive), **IF I don't do it**... later I wont be able to access my files...
i.e. In Windows, Sata Hard Drives can be Hot-plugged (after boot) & they can be accessed just by refreshing Device Manager...
In Ubuntu IF I boot my PC & hot plug my Sata Hard Drive afterwords, no matter what I try - e.g. "mount -a" - the newly added Hard Drive does NOT get mounted!!!

So IF I don't plug-in the Hard Drive **before I boot** my System, how will I be able to access my files man?

You might post this as a separate question to this forum.

> 

Sata Hard Drives don't have jumpers...



I have already done this!
I tell it to boot from the Ubuntu OS Hard Drive.
NOT from the other NTFS (without OS) Hard Drive.

Still, for some reason it won't work!
Also, I plugged the Sata's Data Cable on a diff Sata plug on the Mobo...
Nothing changed!


I didn't know you had sata.

> 

"[color=blue]/boot/grub/menu.lst[/color]" are needed...

'cause the file menu.lst tells Grub what partition and program to boot.

> 



I don't get a grub menu when booting...
Why should I (when there is only one OS installed on the Hard Drive)?
Thanks.

Whether or not you get a grub menu depends on how you configure grub.

.............
1:
I am no expert on sata drives.  

I assume you have two sata drives.  This is a total swag...  I'd consider swapping the sata connectors.  Perhaps the bios is booting the ntfs drive first.  When the ntfs drive isn't present, it boots the ubuntu drive. When the ntfs drive is present, it boots the ntfs drive.

2:  I'd change the /boot/grub/menu.lst

applications>accessories>terminal
sudo nano /boot/grub/menu.lst
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

control-o 
 to file
 
notice that I commented out hiddenmenu

This will let you know what grub you got too.

3: You could try superGrub.  This will let you pick what harddrive to boot.

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert
Edit/Delete Message

---

