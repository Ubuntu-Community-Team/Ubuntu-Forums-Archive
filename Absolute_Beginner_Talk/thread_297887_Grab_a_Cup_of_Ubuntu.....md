---
title: "Grab a Cup of Ubuntu...."
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by nuclearj on 2006-11-11
Cause we'll be here awhile.

Background:  I just got finished installing VMware with Windows 2000 Pro.  I am using Dapper as the host.  I have a copy of XP Pro on my Windows HD from another computer where the video card is shot.  I want XP Pro as my guest on Dapper.  So I think to myself, why don't i switch out HDs and burn a CD of XP Pro and then I can use that to have XP Pro within VMware?  Well that did not work because i got a stop error (blue screen of death) due to the fact the windows operating system is set up to the previous hardware so the new hardware will not recognize it.

In my youthful exuberance and curiosity, I was trying to find a way around this error (before I found out it was a hardware issue) and I had done a repair install of Win2000 thinking it would only affect the HD.  Seems it also works/writes to the BIOS, or CMOS or boot disk...  (I'm not sure what is really what but I'll be taking and A+ course soon:) )

Current Issue:  When I start the computer up (after I put the Ubuntu HD to its rightful place) I get this error saying (paraphrased) "Windows 2000 could not start because <windows 2000 root> \system\ntoskrnl.exe is corrupt or missing.  Please reinstall"  I found a workaround this using a program from The Ultimate Boot Disk that lets me choose what to boot.  Hence, I am able to type this and send it to you lovely folks.  I also found sites explaining this ntoskrnl.exe issue.  But they are all for people who want to get their windows working.  I belive I have a unique issue in that i want to get my Linux\Ubuntu running again.

I fiugre before I wipe the HD and reintall Ubuntu for the fifth time.  I'll ask the master brewers and the way too much Ubuntu folks for some guidance.  Everyone else is also welcomed to put in their two cents.:D 

My own Ideas for fixing:
-Wipe the BIOS or CMOS or the first sector of my HD (I'm not sure of what will happen if i do any of those, or even how to really do it)
-Wipe the HD and reinstall Dapper (would like to avoid this but I am willing)
-Keep dong what I am doing now to get here (do not like this Idea cause it's more of a band aid to the problem, plus there are some things that worked before that do not work now; i.e. VMware which is why I started this all in the first place!)

So please, show me the follys of my ways, and offer some guidance in these three paths I have chosen.  Maybe you could show me some paths that only a trained eye can see?:-k

---

### Post by lloyd_b on 2006-11-12
It sounds like you just messed up the Master Boot Record (MBR).

To fix:  When booted to Ubuntu, type 
```
**sudo grub-install {drive}**
```

Where {drive} is the "/dev" entry for the drive (i.e. "/dev/hda", "/dev/sda", etc.).

You can determine the {drive} by looking at your "/etc/fstab" file.  If the root partition is "/dev/hda2" for example, the drive you'll use will be "/dev/hda"...

Lloyd B.

---

### Post by nuclearj on 2006-11-12
Cool I'll try that.  Thanks!

---

### Post by nuclearj on 2006-11-12
Okay so this is what I ran.  I'll reboot to see if it worked.

nuclearj@Venice-610:~$ sudo grub-install /dev/hda
Password:
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
(hd1)   /dev/hdb
nuclearj@Venice-610:~$

Update: I ran the ablove and restarted my box.  Still the same error msg.

Lloyd_B - what does the above say?  (From the terminal)

---

### Post by lloyd_b on 2006-11-13
> Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem

:confused: I have never seen that particular message before. Either with Debian or Ubuntu.  Damifino....

> Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0) /dev/hda
(hd1) /dev/hdb

This is a normal-seeming output for GRUB.  Everything looks ok...

Could you post a copy of the file "/boot/grub/menu.lst"?  This is what GRUB uses to determine what to boot for a given menu option.

Also, could you post a listing of the partitions on both drives?  To get a list:
```
sudo parted /dev/hda
print
quit
```

Then repeat for /dev/hdb

I'm not sure what's wrong - I'm just fishing for the things I would look at first if it were my machine involved, and hoping that something will "jump out at me".

Lloyd B.

---

### Post by nuclearj on 2006-11-13
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

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

> nuclearj@Venice-610:~$ sudo parted /dev/hda
Password:
GNU Parted 1.6.25.1
Copyright (C) 1998 - 2005 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hda
(parted) print
Disk geometry for /dev/hda: 0kB - 82GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    79GB    79GB    primary   ext3         boot
2       79GB    82GB    3093MB  extended
5       79GB    82GB    3093MB  logical   linux-swap
(parted) quit
Information: Don't forget to update /etc/fstab, if necessary.

nuclearj@Venice-610:~$


> nuclearj@Venice-610:~$ sudo parted /dev/hdb
GNU Parted 1.6.25.1
Copyright (C) 1998 - 2005 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hdb
(parted) print
Disk geometry for /dev/hdb: 0kB - 15GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    15GB    15GB    primary   ntfs         boot
(parted) quit
Information: Don't forget to update /etc/fstab, if necessary.

nuclearj@Venice-610:~$



Here are those things you requested.  Thanks so much for your help.

---

### Post by lloyd_b on 2006-11-14
I'm not seeing any problems.:( 

What I *think* happened is that Win2K overwrote the default MBR with it's own, making it try to boot Win2K instead of running GRUB.

"grub-install" should have taken care of this.

It apparently didn't, and I don't understand why.

Unless your BIOS is actually trying to boot from the second hard drive.  I've never heard of a BIOS that would do this, though....

If you can open up the machine without too much trouble, try disconnecting the second hard drive, and see what happens when you reboot.  Just trying to eliminate that (remote) possibility.

Frankly, if it were my machine, I would *seriously* be considering a re-install of Ubuntu at this point. 

Hopefully, somebody else will wander by with some other alternatives...

Lloyd B

---

### Post by nuclearj on 2006-11-15
That remote possibillity blew this case wide open.  I disconnected it and it worked!  On further inspection I had the jumper on my main HD set incorrectly.  That's why it went to the other one and I got that error msg because the other drive is just for back up.  It does not have an OS installed on it.  It's always the mundane things that get me. :rolleyes:   Many thanks and many blessings to you Lloyd_B.

---

