---
title: "No boot device detected:system halted"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by rick yent on 2008-04-12
This is the first time I haven't found an answer through simply doing a google search to my problem!

I have a single boot system using a new hard drive. The system was running fine, however, I tried to switch users; I have both gnome and kde running (I've found that neither, singly, meets my needs). They system just froze, I left it for quite a while, then hit the kill switch. When I tried to reboot, I get the error: No boot device detected: system halted. I almost forgot, I'm now running gutsy 7.10. When this happened I was running 7.04. I did the upgrade thinking that it might look at grub and re-make/image the mbr. It didn't.

First, I put in a live cd at the boot prompt I selected boot from hard drive. The system boots and all my information is there. I just can't start from a hard drive.

Following some of the threads I found I did the following (abbriviated)
Sorry, posts don't seem to be numbered so I can't site the post
From: [http://ubuntuforums.org/showthread.php?t=596239](http://ubuntuforums.org/showthread.php?t=596239)

[I]Mount the Ubuntu installation (sda2)
sudo mount /dev/sda2 /mnt


Chroot into it
sudo chroot /mnt

and run
sudo grub-install /dev/sda

Then reboot.[/I]

For me this didn't work my hard disk shows at sda1 so I used sda1 instead of sda2

Also on the is page I tried
# mkdir /oldsystem
# mount /dev/sda2 /oldsystem
# mount -o /dev /oldsystem/dev
# chroot /oldsystem

This doesn't work
There was a thread directing me to:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair)
These instructions do a sudo grub
look for stage1 and so on
This also doesn't work

I've tried everything I've found booting intiially from the live cd and then also using the live cd to boot but running from my installed system on my hard drive.

Also using Kate: Since I could get to the hard drive I simply said "sudo grub-install" This doesn't work

When I get a usable response it says that I already have the latest greatest version of grub installed. I don't think grub is the actual problem I think that the device map or whatever grub looks at is the problem. 

(sorry for the incomplete details I'm not on the problem machine)
Thanks for any help

---

### Post by Hospadar on 2008-04-12
in the livecd, I'd open up gparted (Alt-F2->"sudo gparted") and use it to "check" (I think is what they call it, it's the search for errors and repair them thing) the partitions on your hard drive.  Also, could you post your /boot/grub/menu.lst (the one installed on your hdd) file?

---

### Post by rick yent on 2008-04-12
Thanks for the quick post, sorry about the delay had to pick up someone from the airport. I'll check for the info you need and check on gparted.
rick

---

### Post by hyper_ch on 2008-04-12
can you make a screenshot when running gparted?

---

### Post by rick yent on 2008-04-12
I don't know if you needed it all, but here it is. Reading over it looks like the line (hda0,1) may be where my previous problem is. I was using sda1 for the solutions listed above. And this system isn't supposed to have any windows on it. When I did the install I said use the whole hard disk. It looks like grub didn't wipe the mbr out. Actually I don't think I ever had this as a boot HD I was just using it for storage. Interesting

I'm working on the gparted I'll have to reboot using the live cd. I thought ubuntu had a partitioning program in it?

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
# kopt=root=UUID=a35caee6-f391-4b91-81cb-44553e5bc979 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a35caee6-f391-4b91-81cb-44553e5bc979 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a35caee6-f391-4b91-81cb-44553e5bc979 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a35caee6-f391-4b91-81cb-44553e5bc979 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a35caee6-f391-4b91-81cb-44553e5bc979 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by rick yent on 2008-04-12
Ok, I've booted from the live cd and brought up gparted. Saved the screen shot to the desktop, and hopefully uploaded the image through the attachment manager

---

### Post by rick yent on 2008-04-12
Yup, the image showed up. Is my boot partition, partition 2, sda2?

---

### Post by hyper_ch on 2008-04-12
no, boot partition is sda1....

---

### Post by rick yent on 2008-04-12
I looked around in gparted, I didn't see anything that said "check" as the previous poster asked me to do. Do you have any advice about gparted? When messing with partiitions I don't like to just do anything. 
Thanks
Rick

---

### Post by torgrot on 2008-04-12
Use Gparted to make sda1 bootable i.e. set the boot flag.

torgrot

---

### Post by rick yent on 2008-04-12
If I did this correctly, it says that it is bootable (screen shot included)

---

### Post by rick yent on 2008-04-12
Here it is (I hope)

---

### Post by rick yent on 2008-04-12
**[COLOR="Red"]I don't know if you'all noticed, I've got screen shots on page 2[/COLOR]** thanks. I didn't find it for a minute.

---

### Post by otrojake on 2008-04-12
I'm just wondering, is this GRUB that's spitting out the error?  By this, I mean, do you see any stuff pertaining to GRUB pop up before it says it can't find a boot device?

Or is this a BIOS message saying that it can't find a bootable device?

---

### Post by rick yent on 2008-04-12
Hmm, good question. I hadn't thought of that and that idea would lend support to the fact that when I try to reinstall grub, it says that the latest version is there. I wonder why the bios wouldn't find a bootable device. I'm going to shut down and take a look at the bios to see if it sees the hard drive. But... if that's the case why, when I use an install cd to boot the system does it then see the hard drive and run just fine. As a matter of fact, I was having this problem when I upgraded from feisty to gutsy (thinking that might fix the problem. If you have any other ideas send them along. I'm monitoring on another system. I just may not be able to impliment right away.
Thanks otrojake
Rick

---

### Post by rick yent on 2008-04-12
Hey otrojake,
The bios sees the hard drive in the setup an st2008, or whatever it is. So I don't think thats the problem. I was messing around with external hard drives earlier, they weren't present when I did my upgrade and I don't have anything pluged in now. I have an hp system that will try to boot from cf and sd cards and will hang because it says there is not boot system (I've tried to change the bios on that one so it won't boot from usb but the change never sticks, now I boot an ubuntu external drive on it). So I don't think it's the bios. If I don't get any resolution from the forum maybe I'll stick an old hd in it and do a desktop install. 
thanks
rick

---

### Post by rick yent on 2008-04-12
I just tried another scenario. I have Kubuntu mounted on a 4gig pen drive. It read the pen drive and booted into my HD system with my server and all users! This get's more interesting as I plug things in!

---

### Post by otrojake on 2008-04-12
Good to know the BIOS is seeing it.

Does anything relating to GRUB pop at all?  Because if the hard disk is seeing the GRUB bootloader on there and GRUB's isn't screwed up, GRUB should be popping out a numbered error.  Something like an Error 17.  But if you're not getting a numbered error, then the board's not seeing the boot sector on the drive properly.  I haven't had much luck personally with the grub-install command (I think I probably was doing something wrong).

When you did the 'sudo grub' bit, once you found what partition the GRUB files were on, did you specify the root partition and then run the setup command on the disk?  More specifically, did you run inside 'sudo grub':

```
root (hd0,0)
setup (hd0)
```

---

### Post by otrojake on 2008-04-12
Right now, to me, it sounds like GRUB isn't installed correctly into your boot sector.  Because your system used the GRUB installation on your flash drive to read the files from the hard drive and then boot into the hard disk system.  I'd try doing 'sudo grub' again.

---

### Post by rick yent on 2008-04-12
In answer to the first question. I believe I was in grub and did everything in the other posts. The problem is that grub returned a map that said this is what I(grub) see in the map if it's wrong correct it and run the install again. The problem is, of course, that I don't know if it's right or wrong! If you know I can try running the commands from the earlier posts to the other person and bounce the info off you. With more knowledgeable feedback maybe all I need to do is run the other commands. But, I think there is a problem because grub didn't install itself again.

 The one thing I thought was to delete grub and then reinstall it. My thinking is that once it is gone when it tries to install new it will re-map the drives and install. However, since I'm a newbie this may totally kill my whole system, I don't know. So this was a last ditch plan. Then if it screws up I'd reinstall my whole server. But that's a pain.

---

### Post by otrojake on 2008-04-12
I've screwed up my boot sector too many times than I care to count and it took me a few times of screwing around with 'sudo grub' to get things working right.  I really think you should try running the 'sudo grub' command again and going through all the steps, most importantly the root(hd?,?) and setup(hd?) parts--both those depend on what find /boot/grub/stage1 returns--while you're at the GRUB command line.  Those two are the most important, because without typing those in, GRUB will not reinstall.

On a side note, your system's most likely intact.  If this is a GRUB issue (as it seems), nothing you do to GRUB will kill your system.

---

### Post by rick yent on 2008-04-12
It seems like I've lost my assistance for the time being. It's just as well, I have a dinner to go to so I'm leaving my system. I'll probably be back later this evening at the latest I'll be online tomorrow. Thanks to all
Rick

If anyone has any ideas about this issue please post them. I can be reached at gdylynx at gmail.com, please no spam

---

### Post by rick yent on 2008-04-13
This problem has been solved. For future knowledge: I put a second drive in the system so I could copy the files to it. The first time it didn't boot. I adjusted the jumper blocks on the HD's to master, slave. I then tried to let the system boot. It booted from the drive it earlier would not boot from. For the record I hadn't moved the jumpers when it stopped booting. Perhaps grub couldn't resolve the no indicator jumper setting after the freeze up. As I used to say, you can't argue with the computer gods, you just accept what they deal you!

---

### Post by otrojake on 2008-04-13
Glad that the problem's solved!  And you're definitely right about the computer gods.  They bring both rain and sunshine.  Best to accept the sunshine when they allow it :)

---

