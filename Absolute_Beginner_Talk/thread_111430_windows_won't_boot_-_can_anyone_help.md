---
title: "windows won't boot - can anyone help?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by jenphalian on 2006-01-02
I've set up a dual boot system on my desktop, or tried to, anyway.  Unfortunately, I can't get windows to boot now (honestly, I really don't want to boot windows, but my husband wants to use the ipod he just got for christmas, and I am thinking it will be easiest to let him load music from there.  I'm sticking all our .mp3s on the fat32 slave drive.)

Anyway, I think the problem is that windows is on hda2, not hda1.  Here is what my partitions look like:

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 125M     0  125M   0% /dev/shm
tmpfs                 125M   13M  113M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hda2              12G  6.8G  4.5G  61% /media/windows
/dev/hda5             4.6G  639M  3.8G  15% /home
/dev/hdb5             149G   19G  131G  13% /media/hdb5
/dev/hdc              4.9G  4.9G     0 100% /media/cdrom0

When I was installing ubuntu, the partitioning tool told me I had uncorrectable errors on the IDE1 master, and there was a tiny little partition at hda1 that was listed as free space, but I couldn't edit or do anything with that partition.  It was at the beginning of the space, and I think thats why the windows partition got called hda2.

When I try to boot windows, it tells me that the following file is missing or corrupted:  <windows root>\system32\hal.dll  and the system reboots and goes back to the GRUB screen.

Does anyone know how I can fix this and boot windows?

---

### Post by chimera on 2006-01-02
I don't really know what's wrong, but I just thought I'd let you know, if you can acces all your .mp3 files you can get them on your Ipod in ubuntu, it's recognised s an external storage device. Just don't forget to umount it before you plug it out;)

---

### Post by mckennas on 2006-01-02
I belive the HAL - Hardware Abstraction Layer - is built during the Windows install - If it is now gone or corrupted, you have a serious issue. My first thought would be a System Restore Point.

---

### Post by jenphalian on 2006-01-02
[QUOTE=mckennas]I belive the HAL - Hardware Abstraction Layer - is built during the Windows install - If it is now gone or corrupted, you have a serious issue. My first thought would be a System Restore Point.[/QUOTE]
But is it really gone, or is it just looking in the wrong place because the partitions are set up wrong?

---

### Post by d1337 on 2006-01-02
I agree with mckennas in regards to hal.dll likely causing this issue.  For grins, though, could you post your /boot/grub/menu.lst to compare against your partition info from above.

d1337

---

### Post by jenphalian on 2006-01-02
[QUOTE=d1337]I agree with mckennas in regards to hal.dll likely causing this issue.  For grins, though, could you post your /boot/grub/menu.lst to compare against your partition info from above.

d1337[/QUOTE]
I would love to!  Alas, I'm a n00b - How do I get that?

---

### Post by jenphalian on 2006-01-02
[QUOTE=d1337]I agree with mckennas in regards to hal.dll likely causing this issue.  For grins, though, could you post your /boot/grub/menu.lst to compare against your partition info from above.

d1337[/QUOTE]
Wait, nevermind, I figured out to use gedit.  Is this the relevant part of that file?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by kaamos on 2006-01-02
EDIT: neverming, you figured it out. And yes that is the correct part. Looks good to me though.

---

### Post by jenphalian on 2006-01-02
In the last week, visions of "sudo gedit" have replaced visions of sugarplums in my head.  :)

---

### Post by vasudevank on 2006-01-02
i think you have a corrupted windows, because it boots into it then gives you the error, the only thing that you could try whould be interactive grub (if that doesn't work, well you have a corrupted filesystem)

---

### Post by d1337 on 2006-01-02
Your error appears to be somewhat common.  A [google]("http://www.google.com/search?hl=en&q=%3Cwindows+root%3E%5Csystem32%5Chal.dll&btnG=Google+Searchp") search gave plenty of hits.  The one that I found to be a possible solution for you is on [nocrash.com]("http://www.nocrash.com/ncbbs/msgs/162.shtml")

On the upside, you do have a functioning machine on the Linux side that you may be able to use to recover important files.  The fix from the link above may restore without a format or losing any data.

Before you proceed, though, could you humor me by posting your entire /boot/grub/menu.lst

d1337

---

### Post by jenphalian on 2006-01-02
jenphalian@Bianca:~$ cat /boot/grub/menu.lst
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

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

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

jenphalian@Bianca:~$

---

### Post by d1337 on 2006-01-02
In the last section, change (using Gedit) root to:
```
root (hd0,0)
```
Save it, shut it down and try again to boot into MS.  While it has been about a year and a half, so I don't recall the exact error msg, I had a goof on a dual boot and the change above fixed it.  Recalling, it was having an issue grabbing something to fire MS.  Just a shot in the dark, but you never know.

d1337

---

### Post by jenphalian on 2006-01-03
Well, it was worth a shot, and I had been hoping changing that 1 to a 0 would fix things, but it still wouldn't boot.  Thanks, though!  Fortunately, I don't have any data over on windows that isn't backed up, and since the ubuntu system works so nicely, I can retrieve it anyway.

So long as my husband gets his ipod to work with gtkpod, I'll nuke windows and never feel bad about it.

---

### Post by proventech on 2006-01-03
you may try to boot windows in safe mode by hitting F8 then rebooting.  it may rebuild the file correctly.

---

### Post by steveneddy on 2006-01-03
Deleted....

---

### Post by Kurt Dodrill on 2006-01-03
[QUOTE=jenphalian]

So long as my husband gets his ipod to work with gtkpod, I'll nuke windows and never feel bad about it.[/QUOTE]

WELCOME!!

---

### Post by proventech on 2006-01-04
[QUOTE=steveneddy]We can ask Windohs questions here? cool.....my Win98 has a small problem. I can't get my linux cd to run when I start windows. I know it should run in a windows if I double click something, but what do I do? 

If I put linux in a folder on my desktop, will I be able to see linux?

Also, my Windows Media Player won't play my Quicktime files? Why is that?[/QUOTE]

steveneddy, you have to tell you computer to boot to your cd-rom.  reboot your computer, enter into the setup (F1, F2, esc, del - it should tell you), find the boot sequence option and tell it to boot to the CD first.  save then exit.  it should boot to the cd.

As for your second question...  Windows Media Player was designed by Microsoft (ie: Bill Gates) and Quicktime was designed by Apple (ie: Steve Jobs).  Any other questions?

---

