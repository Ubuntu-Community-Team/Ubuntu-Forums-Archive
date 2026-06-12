---
title: "XP duol boot help"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-05-05
Im going to add XP to my ubuntu system Im downloading an XP iso from frostwire as I write so how do I do this without messing anything up I only have an 80gig hard drive.

---

### Post by microsoft92sucks on 2007-05-05
and wats a good iso image burner for Ubuntu that i can get throw synaptic

---

### Post by kfrance on 2007-05-05
You can write an iso to disk just using nautilus.  Just right click on the iso and click on write to disk.  No need to install anything else.  

You'll first have to make a free partition to install windows on.  I would just use gparted to do that.  If it isn't already installed you can get it through synaptic.  After you have installed windows you will see that is has overwritten grub.  Windows doesn't play nice with other operating systems.  You'll need to reinstalling it.  Look at this to figure how to do that [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub).

---

### Post by junior28862 on 2007-05-06
I would actually recommend using K3B to burn the ISO to disk because you have the option to check the validity of the burn.  There is nothing worse than having a corupt disk and not knowing it until everything starts to break down the road or won't install.

---

### Post by microsoft92sucks on 2007-05-06
When do i parton the hard drive becouse I dont see gparted under any of my Applications and is will reinstaling grub go smoothly or do alot of people have a problem with it and how will i choose wat os I log into once i have it all finished???:confused:

---

### Post by microsoft92sucks on 2007-05-06
please help I want to install soon

---

### Post by rygar on 2007-05-06
if GParted is installed on your system, it doesn't show up under Applications
it shows up under System -> Administration

If I assume correctly, you have one partition on your computer, which is formatted to ext3 for Ubuntu...  correct?
You'll have to shrink your partition to make room for an NTFS (XP) partition.

The thing is, you can't do that when your partition is mounted.  Boot from your Ubuntu live cd.  Then go into Gparted and shrink your partition, leaving whatever size you want for your XP partition unallocated.

Pop in your XP CD and reboot your computer.  Your XP installation will ask you where you want to install XP; select the unallocated space, and tell it to format it to NTFS.

XP's boot manager probably will take over GRUB as the default boot manager.  Unfortunately, I had XP installed before Ubuntu so I can't help you with this, but I believe there are several threads on this forum with instructions on how to bring GRUB back...   try doing a search.

Hope this helps.

---

### Post by microsoft92sucks on 2007-05-07
thx I got XP installed but then I reinstalled grub so how do i get back to XP and It says that I have to verify XP over Inernet or Customer Service b4 I can get on it how do I do this without going to jail.

---

### Post by oilchangeguy on 2007-05-07
you can't. unless you have a legal product key. you've probably 30 days to activate it. after that it won't load.

---

### Post by microsoft92sucks on 2007-05-07
were can I get the pruduck key at for free. And my friend said for me to veldate it over the inernet and it will tell me it's an illegal copy but wont do no more then that. Is he right or will i go to jail

---

### Post by oilchangeguy on 2007-05-07
you can't get a free product key. what operating system did you have on your computer before ubuntu?

---

### Post by thefoolisme on 2007-05-07
> **microsoft92sucks said:**
> were can I get the pruduck key at for free. And my friend said for me to veldate it over the inernet and it will tell me it's an illegal copy but wont do no more then that. Is he right or will i go to jail

You can't get the product key for free.  Not sure what would make you think you could.  Without a product key, the Windows XP system will either stop running in 7 or 30 days, depending on what version you installed.  Once Windows determines it's an illegal copy, or it is not validated and activated within the time period, it will not allow you to even log into your Windows.  There are ways to get around activation, timebombs, etc, but you can't do any of that without a valid product key that hasn't been marked by MS as being pirated.  

Truthfully, this is the type of behavior that Microsoft has been fighting against, and causes them to keep putting more and more ridiculous anti-piracy and DRM crap in their systems.  

You had some sort of MS system on your PC before.  Which one was that?  Do you still have the systems disks for it?  and why did you delete it completely when installing Ubuntu?  And why do you need it back now?

---

### Post by microsoft92sucks on 2007-05-07
OK i found out how to get past all that and XP is installed but now how do I switch between the too 
Ive already put grub back on so when i turn my pc on it takes me to ubuntu. How do i get back to Xp 

If this meters I have a old hp i think its like a 2000 im not sure I got it from a flea market yes a flea market
  
and to answer you "thefoolisme"
it came with a boot legged copy of XP 
It got a viruses and wouldn't even start and so i finaly swiched to Ubuntu like i had been wanting to for awhile and Im really really happy with Ubuntu
but I want to learn the M$ command proment because most people sadly use M$:(   and to get some games. 

Please how do I switch between the 2

---

### Post by microsoft92sucks on 2007-05-07
please need help

---

### Post by hesaidit on 2007-05-07
Not that i should say this but if u get a key that is already in use then just ring up MS and say that u had to r installing it on a new computer (u will have to say u r not using ur old one) and they should reactive it for u...

i know people that do this all the time..

---

### Post by microsoft92sucks on 2007-05-07
I got passed all that I found the key and put it in and it was working but i dont know how to get back onto XP when i turn on my pc it just loads up grub and doesent ask me wat os i want

---

### Post by drowner on 2007-05-07
It just loads grub?

And doesnt ask you what you want?

What does GRUB do then?

---

### Post by microsoft92sucks on 2007-05-07
grub just loads like normal not saying anything else 
whats should I do is that not what it should be doing normal 
windows is installed i was on it then i put in the Ubuntu installation cd and fixed grub now i cant get to xp

I have windows on a differnet portion of the hard drive

if u need more info just ask
Please Help im still kinda a noob to Ubuntu

---

### Post by thefoolisme on 2007-05-08
Post the results from these two commands in terminal.  It will let everyone know what your grbu menu looks like, and the layout of your hard disk.  

cat /boot/grub/menu.lst
sudo fdisk -l

Just copy and paste the commands into the terminal and copy and paste the output back here.

Also, did you install Windows on the first partition or the second?  From what I've been reading, Windows doesn't like being on anything but the first partition.  See:  [http://ubuntuforums.org/showthread.php?t=426919](http://ubuntuforums.org/showthread.php?t=426919)

But let's get your Grub and disk info, and maybe someone can guide you from there.

---

### Post by microsoft92sucks on 2007-05-08
justin@EggHead:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=38142ed8-caca-43fb-a5e2-c6275f73e630 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7725    62051031   83  Linux
/dev/sda2   *        7726        9637    15358140    7  HPFS/NTFS
/dev/sda3            9638        9729      738990    5  Extended
/dev/sda5            9638        9729      738958+  82  Linux swap / Solaris


System HPFS/NTFS is were windows is at and I think windows is on the 2nd portion

All Help Is Greatly Thanked

---

### Post by microsoft92sucks on 2007-05-08
I got on the Ubuntu live cd and looked at the portions and windows is portion 2 so if thats the problem how do i switch it to portion 1 and once i do will i be able to get on Ubuntu

---

### Post by microsoft92sucks on 2007-05-08
I got on my PC settings by pressing f2 b4 a os loads and I went under boot and then Hard Drive and fund 2 OSes 1 was WDS so and so and the other was Ubuntu but anyway I fond the same the same thing under a Hard Disk that pops up when i go to Gpartion on Hard Disk Ubuntu and Its windows but when I tell the PC to load it first It still loads Ubuntu?:confused: 
Wats up with that and i still dont know how to make windows portion 1

---

### Post by armagon on 2007-05-08
can someone tell me how 2 use linux ubuntu n microsoft xp in one drive?
can my computer use the os's without any problem?

---

### Post by Duck2006 on 2007-05-08
Try adding these lines to your menu.lst

itle		Windows NT/2000/XP
root		(hd0,0)
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
savedefault
chainloader	+1

> can someone tell me how 2 use linux ubuntu n microsoft xp in one drive?
can my computer use the os's without any problem?

[http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot](http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot)

---

### Post by microsoft92sucks on 2007-05-08
how do I add them to my menu.lst and wat menu list and i though I had To make windows portion 1

---

### Post by microsoft92sucks on 2007-05-08
Ive been trying to do this for days now there is no way to to make windows portion one without reinstalling Ubuntu and im not doing that so can som1 please help me:(

---

### Post by microsoft92sucks on 2007-05-09
I fingured it out Thank u to any 1 who helped me

---

