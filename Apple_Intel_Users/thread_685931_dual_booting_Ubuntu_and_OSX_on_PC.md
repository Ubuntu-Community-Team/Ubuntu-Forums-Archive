---
title: "dual booting Ubuntu and OSX on PC"
date: 2008-02-02
forum: Apple Intel Users
---

### Post by raydar on 2008-02-02
I mainly run UbuntuStudio (CeleronD PC), but I'm trying to get dual booting working with an OSX86 installation on a separate hard drive.  I got the OSX installation working on its drive and then installed UbuntuStudio on its drive, but OSX wasn't listed in the grub menu.

I finally found how to edit my menu.lst file so that grub sees my OSX drive, but when I tried to boot OSX, I got the "HFS+ Partition Error" mentioned at 
[http://forum.insanelymac.com/index.php?showtopic=28780&hl=hfs\++partition+error](http://forum.insanelymac.com/index.php?showtopic=28780&hl=hfs\++partition+error) .
and so I tried the fdisk fix offered there.

Specifically, I booted from the OSX install DVD and executed the command
fdisk -u /dev/drive0
(using drive0 because my system sees my Ubuntu drive as /dev/sdb and my OSX drive as /dev/sda).  But that sent my system belly up when I restarted; no grub, just a blinking cursor forever. 

I think what I should have done is run fdisk from Linux, not OSX--although that same thread linked to above suggested that the fdisk operation can even be done from a DOS boot disk, so I didn't think I was doing anything wrong.  Turns out I was, and I'm very glad to say UbuntuStudio's installation DVD's repair-a-broken-installation tool saved the day, rewriting the boot sector and putting me back in grub when I boot.

I'm game to experiment more, but I'd rather ask the advice of someone who really knows fdisk, grub, and boot sectors before I bork my system again:  Is the command
fdisk -u /dev/sda
what I should be doing in order to make my OSX partition happy?  If not, what should I do?

Thanks for any help!

P.S.: Below is the important part of my menu.lst file as I currently have it:

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=ad4e59ec-3cc2-4cae-8545-48267a6da920 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=ad4e59ec-3cc2-4cae-8545-48267a6da920 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

## the below was added 2Feb08am per [http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate#Grub_in_short](http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate#Grub_in_short)

title OSX_X86
##rootnoverify (hd0,0)
root (hd0,0)
##makeactive
chainloader --force +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by cyberdork33 on 2008-02-03
Unfortunately you are probably not going to get much help with an OSX86 install here since there is the question of legality involved, but I can help you get Ubuntu working again, and that is going to require you reinstalling grub to the MBR (which your fdisk command likely wiped out.)

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

