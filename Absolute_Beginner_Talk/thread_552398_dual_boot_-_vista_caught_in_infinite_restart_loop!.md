---
title: "dual boot - vista caught in infinite restart loop!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-09-16
Hey everyone I have read many articles and forums regarding this but have yet to come to a solid conclusion on what the cause of the problem is and the exact solution.

I have Ubuntu dual booting with Vista.  I need to keep windoze because my printer doesn't work with ubuntu, and secondly i write my programs in ubuntu but i need to make sure they compile fine with Pelles C a windows compiler as that's the compiler the professor will be using to test our programs.

So here is my problem!  from grub i select vista and it restarts the computer, if i select it from the grub menu again it restarts again!  

i am quite puzzled and would appreciate any suggestions or feedback on any possible fixes or just thoughts on how to get ir all back to normal.

if you need any output of any sort let me know and i would be more than happy to post it.

Thanks, Alain

---

### Post by S15_88 on 2007-09-16
thought i'd throw my menu.lst in, perhaps it's of help.  

since i have nothing of importance in vista would a fresh install be a logical step?

what sort of risks do i run if i try to reinstall vista with ubuntu already on my machine?

Thanks again, Alain

menu.lst:
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
# kopt=root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Micro$oft Windozzze Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by jordanmthomas on 2007-09-16
Don't know if this is your problem per se, but usually when I dual-boot windows on the line where I define the root, I use rootnoverify because just using root doesn't usually want to work.
```

title           Micro$oft Windozzze Vista/Longhorn (loader)
root[COLOR="Red"]noverify[/COLOR]            (hd0,1)
savedefault
makeactive
chainloader     +1
```

Also, could you post the output of 
```
sudo fdisk -l
```
to make sure Vista is where Grub says it is?

---

### Post by S15_88 on 2007-09-16
alright i'll add that in there and see what happens, and here's the output for:  fdisk -l
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *        1312        5844    36411322+   7  HPFS/NTFS
/dev/sda3            5845       19457   109346422+   5  Extended
/dev/sda5            5845       17998    97626973+  83  Linux
/dev/sda6           17999       19261    10145016   83  Linux
/dev/sda7           19262       19457     1574338+  82  Linux swap / Solaris

Thanks for the help, Alain

---

### Post by jordanmthomas on 2007-09-16
Well, everything other than the rootnoverify (which, by the way, root works for some people, just not me) seems to be in order.

---

### Post by S15_88 on 2007-09-16
i threw the noverify in there, didn't make a difference.  just another quick question, i'm thinking of just reinstalling vista, but i remember reading something somewhere that if you install windows on an ubuntu machine windows will wipe the whole hard drive, off the top of your head do you know if that's correct?  

i'm going to google around about reinstalling vista.  this restart loop crap has me stumped!

Thanks again for the help, Alain

---

### Post by jordanmthomas on 2007-09-16
It should only wipe out the partition you install it to.  It will, however get rid of Grub so you'd need to reinstall grub, which is not too difficult.

You might want to look up whether or not Vista wipes everything though, because I'm not sure as I have never used or installed Vista.

Good luck anyway.  I would like to think a reinstall isn't necessary, but it *is* Windows after all.

---

### Post by dijipo on 2007-09-24
i've got the problem too but i can't find a solution, i tried the ubuntu live cd and that works but windows doesn't...

---

### Post by Soranor on 2007-11-10
Hey guys- 

Did you ever find a solution to your problem? I'm having a very similar one on a month old tablet PC. It's dual boot with vista (booo!) and Fiesty (to which I am a newbie- converted by vista).

After trying to restart from a windows hibernation, I'm now stuck in an infinite reboot loop. The system posts (memtest, drive check) then reboots without ever taking me to the grub menu, so I can't get into either OS. Disc based start-up is fine, and I can access the drive when I hook it up to my home PC. Any thoughts? I ran a memory checker and a disc checker - both seem fine.

I'm thinking maybe something happened to the grub boot menu file? Could anyone point me towards instructions on removing or reinstalling that file? I have no idea where it is or what it's called. If I remove it, will I default boot into Vista for now?

Thanks... hoping to avoid another windows reinstall - it took so long to get vista tolerable the first time (sigh).

---

### Post by riftt on 2007-11-12
Same problem here :(

---

### Post by Soranor on 2007-11-12
So I kept browsing help forums and whatnot, and found a solution that worked. I created a super GRUB boot disc:

[HTML]http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html[/HTML]

I was able to boot from the disc and get into windows. I then used it to repair the master boot record (i.e. replace the original GRUB file that opens up the dual boot menu). Seems to be working fine again.

---

### Post by kirkquitar on 2008-01-27
I have the same problem mentioned in the first post, I just moved my Vista partition (to get rid of blank unpartitioned space) and now when I tell grub to boot vista, the computer reboots instantly. I'm going to try reinstalling grub, but other than that, any ideas?

Update: So I tried re-installing Grub, and no luck. It seems as if it's not Grub's fault, it boots Linux fine, but it seems like Vista refuses to boot, and the computer just reboots. Does anyone know what the reason could be? The only thing that has really changed is the Vista partitions location.

Update: I fixed it, in case anyone comes across this thread, I managed to get a Vista Installation DVD, and repaired it with that. It didn't overwrite GRUB, simply fixed Vista so it would boot.

---

