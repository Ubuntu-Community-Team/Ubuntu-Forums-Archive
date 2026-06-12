---
title: "Grub help For Windows, Ubuntu, and Suse"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-07-18
I'm trying to do a triple boot with Windows, Ubuntu, and Suse.  Windows is fine.  I had ubuntu on as a dual-boot, and it was all good.  Then I messed up Ubuntu.  I left it for the time being to go back to, and installed Suse to try it out.  When I did that, the Suse screen took ubuntu off the list all together.  Then I went back an reinstalled Ubuntu on it's partitions (remember, I'd messed it up previously).   Now the Grub menu has Ubuntu, Windows, and Suse listed, but the Suse won't load properly.  I think it can't find the drive it needs to.  My guess is because the partitions were renamed when I reinstalled Ubuntu, and there's something in the Suse file that's wrong, because it starts with the commands screen running through, and then fails somewhere while looking for the Suse boot(?).   Can someone please help me fix this?  I've been going through grub info and suse info, and ubuntu info, but there's nothing that covers this faupax.  

Please Understand that I am a newbie!  I may be over my head, but I figure it's the only way I'll learn.  So speak plainly, and don't assume I understand anything.  Thanks. 

Here's the fdisk and Ubuntu Grub menu.lst, with my notations:

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS - Windows XP
/dev/hda2            4463       19929   124238677+   f  W95 Ext'd (LBA)
/dev/hda5            4463       11551    56942361    b  W95 FAT32  - Shared Documents
/dev/hda9           11552       13435    15133198+  83  Linux  - Ubuntu /
/dev/hda10          13436       15388    15687441   83  Linux  - Ubuntu /home
/dev/hda7           15389       16401     8136891   83  Linux  -Suse /
/dev/hda8           16402       17432     8281476   83  Linux - Suse /home
/dev/hda6           19687       19929     1951866   82  Linux swap / Solaris

Disk /dev/hdb: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2534    20354323+   b  W95 FAT32


# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


timeout		10






## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e80037ea-85ed-442d-a1f1-2b48b95539d0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0 )
# groot=(hd0,8 )

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
root		(hd0,8 )
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e80037ea-85ed-442d-a1f1-2b48b95539d0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,8 )
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e80037ea-85ed-442d-a1f1-2b48b95539d0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic


title		Ubuntu, memtest86+
root		(hd0,8 )
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0 )
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		openSUSE 10.2 (i586) (on /dev/hda7)
root		(hd0,6 )
kernel		/boot/vmlinuz-2.6.18.8-0.5-default root=/dev/hda7 
initrd		/boot/initrd-2.6.18.8-0.5-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		openSUSE 10.2 (i586) (on /dev/hda7)
root		(hd0,6 )
kernel		/boot/vmlinux-2.6.18.8-0.5-default.gz root=/dev/hda7 
savedefault
boot

---

### Post by confused57 on 2007-07-18
Try a configfile entry to boot Suse, as I mentioned in your other thread:
[http://ubuntuforums.org/showthread.php?t=501860](http://ubuntuforums.org/showthread.php?t=501860)

It may not work, but worth trying:
```
title        OpenSuse on /dev/sda7
configfile   (hd0,6)/boot/grub/menu.lst
```

---

### Post by thefoolisme on 2007-07-19
I'll try that when I get home tonight.  I think I understand now what that does now that I've played a bit more.  It's looking for Suse's loader list.  Gotcha.  I was looking at that stuff you posted last night, and didn't think it would work for the situation.  Maybe I shouldn't mess with that stuff when I'm tired.  :-)

---

### Post by confused57 on 2007-07-19
> **thefoolisme said:**
> I'll try that when I get home tonight.  I think I understand now what that does now that I've played a bit more.  It's looking for Suse's loader list.  Gotcha.  I was looking at that stuff you posted last night, and didn't think it would work for the situation.  Maybe I shouldn't mess with that stuff when I'm tired.  :-)
Yes, the configfile method should work...you might want to check that Suse doesn't use /boot/grub/grub.conf.

Maybe you can help me out a little...I just downloaded the OpenSuse DVD and was wondering if you were able to specify where to install grub(mbr or root partition).  From install screenshots that I've seen, it looks like there is an option for custom partitioning to specify where to install the root partition and I noticed a separate boot partition was recommended(which I don't know why?).  Thanks for any advice you can give on installing Suse.

---

### Post by thefoolisme on 2007-07-19
> **confused57 said:**
> 

Maybe you can help me out a little...I just downloaded the OpenSuse DVD and was wondering if you were able to specify where to install grub(mbr or root partition).  From install screenshots that I've seen, it looks like there is an option for custom partitioning to specify where to install the root partition and I noticed a separate boot partition was recommended(which I don't know why?).  Thanks for any advice you can give on installing Suse.

The boot partition wasn't necessary for the install, and I didn't use one (maybe that's my problem :-)).  I've come across postings on the forum and in literature that talk about the boot partition and in my first ubuntu install, I set one up.  I've since gotten rid of it.  I think I'm too much of a newb to tell you why they recommend it.  

I used the custom partitioning when I installed it because I wanted to specify where it should be installed.  I didn't want it to overwrite the Ubuntu by mistake.  Honestly, I didn't pay attention about  the grub installation and let it do what it wanted.  That might be why that Ubuntu wasn't on the boot list (just suse and Win) after my Suse install.  If I knew more about it, I probably wouldn't be having the issues I'm having now.  

I do need to learn about them though, because I'd like to put a few more distros on to try, just for fun, and the learning experience, of course.  

If you get it successfully installed, I would love to know the steps you took.  It might help me if I attempt to install another distro or 3.  After all, I have a 250GB HD sitting here just waiting for the world of open source.  

Sorry, I'm not much help.

---

### Post by confused57 on 2007-07-19
Actually, you've helped quite a lot...it's really no problem if OpenSuse's grub is installed to the mbr, I've had this happen with installing other distros that didn't give an option.  It's quite easy, using the live cd,  to reinstall the main distro's grub to the mbr, then install the other distro's grub to the root partition, then use chainloading to boot the new distro.
It's fun for me to try out different distros, I have a 160 Gb IDE drive with 6 distros and a 160 Gb SATA drive with 3 distros & one large data partition.

I don't think you'll have any problem experimenting with multiple distros and it'll be an educational experience, as well...sounds like you already know how to specify installing to a designated partition.  Here's an excellent guide for partitioning basics:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

I've already provided this link, but it explains how to boot multiple distros in grub:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Mainly, I use chainloading, but I have used configfile and symlinking to boot other distros from the main distro's grub.

---

### Post by thefoolisme on 2007-07-19
Just wanted you to know I now have a successfully triple-booted system.  thanks for the input.

---

### Post by confused57 on 2007-07-19
> **thefoolisme said:**
> Just wanted you to know I now have a successfully triple-booted system.  thanks for the input.

No problem...glad it worked out, have fun trying out new distros...you'll definitely learn how to troubleshoot.

---

