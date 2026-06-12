---
title: "Problem configuring LILO"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-24
Hi everyone! Few days ago i decided to install LILO instead of GRUB only cause i had booting problems (error 16, 22, 23 and so on). I downloaded from terminal with aptitude, but this error message pops up when i enter liloconfig on my terminal:

Your /etc/fstab configuration file gives device                           &#9474;  
 &#9474; UUID=4eccbc2f-7619-4474-9e52-6014419f203d as the root filesystem device.  &#9474;  
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474;  
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474;  
 &#9474; as a RAID array) which this simple configuration program does not         &#9474;  
 &#9474; handle.                                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; You should either repair the situation or hand-roll your own              &#9474;  
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474;  
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474;  
 &#9474; found in /usr/share/doc/lilo/.                        

ive found some documentation about a guy named Herman who edited his fstab file in a different way and it worked. But it didnt for me. I even run a live CD, executed e2fsck -c0 -p -f -v /dev/hda1 and that was supposed to fix my filesystem or something but it didnt find any physical errors. Any answers to this problem?

Another thing that concerns me if that when i run my installed Ubuntu from the hard drive, the system monitor names the partition where ubuntu is installed /dev/sda1, but when i run the live cd it says /dev/hda1. Is this normal?

Thanks for yout replies

---

### Post by psusi on 2007-05-24
It has been years sine I used lilo because grub is so much better, so I probably can't help you with lilo, but I probably could help you get grub working if you could post specifics about what went wrong.

---

### Post by ferpadro on 2007-05-24
Well, are you ready, coz this is something strange xD:

I didnt buy this machine, my mother bought it for my grannies coz she wanted them to try something new on technology before they pass away. Finally they never understood how to use a machine, and my mother gave it to me coz im studing engenieering in computers. The fact is it came with Windows XP SP2, and sometimes, when booting, the screen threw a registry error: couldnt locate file /windows/system32/config/system. I didnt paid attention to it, coz i was planning to format and do a clean install, thinking the problem would be solved. But it didnt. The most strange thing was that the error was only shown when the computer booted after a long time being turned off. If i managed to enter and then wanted to do a reboot, it didnt show me any error. Thats when i started thinking that it was not a registry error, but more like a HD error or Motherboard error.
The same thing happened with ubuntu. I installed it without major problems but then when i first shut down the computer after installing it and rebooted , GRUB errors popped. I did a clean install of Ubuntu, deleting windows partition to see if it worked but it didnt. Thats my actual condition, im stuck here, i dont know want to do.

Thats a hell of an explanation, uh? XD

Thanks for your replies

---

### Post by psusi on 2007-05-24
I need you to be very specific about the grub error.  What exactly does it say?  When does it say it?  Etc.  

If you suspect there may be a hardware problem, then I suggest that you run memtest86 when you boot the cd.  Let it run for at least half an hour and see if your ram checks out.

---

### Post by ferpadro on 2007-05-24
The GRUB error that pops up is number 18. I run memtest86 and says there is no error. I'll post my fdisk -lu and menu.lst results (sorry if the output is in spanish) :

fdisk -lu:

fernando@Athena:~$ sudo fdisk -lu
Password:

Disco /dev/sda: 40.0 GB, 40060403712 bytes
255 cabezas, 63 sectores/pista, 4870 cilindros, 78242976 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    18410489     9205213+   7  HPFS/NTFS
/dev/sda2        18410490    75682214    28635862+  83  Linux
/dev/sda3        75682215    78236549     1277167+   5  Extendida
/dev/sda5        75682278    78236549     1277136   82  Linux swap / Solaris



/boot/grub/menu.lst:

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
# kopt=root=UUID=06f1f958-ad78-4b00-af17-6e1dd57d27c1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=06f1f958-ad78-4b00-af17-6e1dd57d27c1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=06f1f958-ad78-4b00-af17-6e1dd57d27c1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

hope anyone can find whats wrong here. Waiting for your replies

regards

---

### Post by psusi on 2007-05-24
Ok, so you only have the one disk right?  What exactly does grub say when you try to boot?

---

### Post by ferpadro on 2007-05-24
yes, i have only 1 disk. When loading it says:

GRUB stage 1.5 loading

please wait
error 18

and it hangs there. Whenever this happens, i enter the bios and change the User HDD type to fix it. But i dont think thats the error

BTW thanks for the quick replies...this forum rocks :D

---

### Post by psusi on 2007-05-24
Huh?  What do you mean you fix it by changing a bios setting?  What do you change, and what do you mean you fix it?  And what do you mean you don't think that's the error?

---

### Post by Skrynesaver on 2007-05-24
Error 18 is a BIOS configuration error, unless your machine is very old the problem should be solved by changing the disk mode to normal (Could currently be either LBA or AUTO).  
The error indicates that as currently configured the BIOS cannot read the entire boot partition/directory.  If your machine is very old you may have to create a separate boot partition.
Hope that helps

---

### Post by ferpadro on 2007-05-24
@psusi: I know it sounds confusing, i could try explaining it to you, but my english is kinda limitated and its not something easy to explain. The fact is that it does not matter what User HDD Type i choose, error 18 will always pop up if its the first time i turn on the machine after a long time of being shut down.

@Skrynesaver: My motherboard is an ASUS P4SPMX-SE ACPI BIOS revision 1005. The computer is not that old, i think it was built on February 2004. The change to HDD type to "Normal" wont do nothing, ive tried with all the different options in the bios and nothing. So u think the boot partition will be the best choice? how can i do that?

---

### Post by psusi on 2007-05-24
You want the bios disk type set to auto, not user, and the access mode set to LBA.

---

### Post by igloocentral on 2007-05-25
bad sector? use [spinrite](http://www.grc.com/sr/spinrite.htm)

---

### Post by Skrynesaver on 2007-05-25
If you haven't much/any data on your root partition"/" then reinstall choosing the advanced partitioning option and set up a partition of ~=120MB to be mounted on /boot this should be the first partition on the disk

---

### Post by ferpadro on 2007-05-25
@psusi: i entered the BIOS and tried to find something like disk type and access mode like you said but i couldnt find anything. The only option that lets me choose "LBA" is only user type HDD.

@SkryneSaver: how can i do that? I mean, if i place a partition of the size you are suggesting, will the bios know that it has to boot from this partition? Sorry if the question is plain obvious.

regards

---

### Post by ferpadro on 2007-05-25
I forgot to say, today when i woke up and turned on my machine a lot of errors popped up:

first try: GRUB error 17. rebooted
second try: "Disk read error, press ctrl+alt+delete to try again" (i had chosen windows in grub)
third try: "The file /windows/system32/config/system is corrupted or it doesnt exist"

i gave up and finally chose ubuntu, but i wanted to enter windows to download some music with Ares. 

I think my computer needs serious exorcizing XD

---

### Post by psusi on 2007-05-25
Huh?  User and LBA should be two different selections.  One should be a choice between LBA, LARGE, and NORMAL.  The other should be a choice between NONE, AUTO, and USER.

---

### Post by igloocentral on 2007-05-25
Many bios's have an option to "load optimized defaults". have you tried this? You could also run the windows xp setup and format the disk but DO NOT USE the "Quick Format" option. You "might" find spinrite on "ares-like" networks...

---

### Post by ferpadro on 2007-05-25
@psusi: Thats the way it is. You can choose Auto, User type HDD or none. If you choose auto, you cant select LBA, normal or any other option. They are only available if you choose User type. I selected "user type" and "Normal" but the same grub error pops up

@igloocentral: My bios does not have that opcion. Instead if you press F5 lets you restore default configuration. I did it once to check if all this errors popped out coz i changed something in the bios accidently, but nothing changed. Whenever i format my computer using WXP cd i always use complete format, not just erasing. The fact is that i turn off the computer, and when i turn it on again the /windows/system32/config/system error cames up again.

I formatted my computer again with ubuntu cd and created a boot partition of 128 MB and mounted it in /boot. I'll turn off the computer for now for a few minutes to see what happens and then ill let you know

Regards

---

