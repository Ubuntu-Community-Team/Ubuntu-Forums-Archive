---
title: "[SOLVED] Problems booting Ubuntu"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by animefan61 on 2007-10-08
I have 2 hard drives in my computer. I have a 13 gig hard drive that has Windows XP installed on it and a 40 gig hard drive with Ubuntu installed. I've been using the 40 gig hard drive with Ubuntu on it, and have to go into my bios every time I boot up. Today I decided to hook both hard drives up. I can get Windows to boot, but when I go to boot Ubuntu it says that there's a system boot failure and to insert the systems disk. I do and Ubuntu will boot from the cd, but won't boot from the hard drive when I restart. I want to be able to do a dual boot between both hard drives, but my bios doesn't recognize that I have a second drive. Can anybody help me? Thanks in advance.

---

### Post by Shazaam on 2007-10-08
Are they both hooked up to the same data cable? Have you checked the jumper settings on both drives? Do you have BOTH Ide channels turned on in your BIOS? Which one do you have set up in your drive boot order as MASTER?  Slave? And last but not least, did you make sure the cables (data and power) are fully seated?

---

### Post by overdrank on 2007-10-08
> **animefan61 said:**
> I have 2 hard drives in my computer. I have a 13 gig hard drive that has Windows XP installed on it and a 40 gig hard drive with Ubuntu installed. I've been using the 40 gig hard drive with Ubuntu on it, and have to go into my bios every time I boot up. Today I decided to hook both hard drives up. I can get Windows to boot, but when I go to boot Ubuntu it says that there's a system boot failure and to insert the systems disk. I do and Ubuntu will boot from the cd, but won't boot from the hard drive when I restart. I want to be able to do a dual boot between both hard drives, but my bios doesn't recognize that I have a second drive. Can anybody help me? Thanks in advance.

Hi when you moved the hard drive did you set the jumpers correctly? Also when change the location of the drive you will have to reinstall the grub and this link will help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by animefan61 on 2007-10-08
> **Shazaam said:**
> Are they both hooked up to the same data cable? Have you checked the jumper settings on both drives? Do you have BOTH Ide channels turned on in your BIOS? Which one do you have set up in your drive boot order as MASTER?  Slave? And last but not least, did you make sure the cables (data and power) are fully seated?

I am a total newbie, and am fully confused now.:confused:

---

### Post by overdrank on 2007-10-08
> **animefan61 said:**
> I am a total newbie, and am fully confused now.:confused:

Hi you stated you moved a drive, can you explain what you did?

---

### Post by animefan61 on 2007-10-08
I didn't move a drive, I hooked up both my hard drives. They are both on the same cable, but my bios only recognizes that I have 1 drive hooked up. I did what that article said, but it didn't help.

---

### Post by overdrank on 2007-10-08
> **animefan61 said:**
> I didn't move a drive, I hooked up both my hard drives. They are both on the same cable, but my bios only recognizes that I have 1 drive hooked up.

Ok there is jumpers on the hard drive to set it as master or slave. The jumpers are located between the power cable and ide ( or sata) cable.

---

### Post by Shazaam on 2007-10-08
This might help with jumper settings (it may be different with the brand of drives you have).
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=84&p_created=1005005461&p_sid=iiHNcINi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzQzLDM0MyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWp1bXBlciBzZXR0aW5ncw**&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=84&p_created=1005005461&p_sid=iiHNcINi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzQzLDM0MyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWp1bXBlciBzZXR0aW5ncw**&p_li=&p_topview=1)

Make ANY hardware changes with the pc OFF and UNPLUGGED, touch the pc frame before touching anything else in the pc AFTER you unplug it.
You should have the Windows drive set as MASTER and the other as SLAVE. Change the jumpers if you need to. Plug the pc back in, boot up and as the pc is booting press whatever button you need (delete is standard) to get into the bios. The page that opens should have your drive(s) listed. You should be able to AUTODETECT the drives from that page. If they are fine look in other bios pages for "Boot Order" or similar. Set the Windows drive to boot first. Save and exit the bios and then reboot. If grub still gives you an error on boot after this, load up the Ubuntu livecd, open a terminal and type in..
```
sudo grub-update
``` and you should be good to go.

---

### Post by animefan61 on 2007-10-08
I opened my computer, because I thought I knew what you were talking about, but I didn't. I unhooked both drives, but I only hooked my 40 gig drive back up. I think what I'm going to have to do is move my hard drives around, but I'm scared I'm going to mess something up. So I may just run this drive for a while, until I get the nerve to try to swap my drives around. Still I don't know if that will solve my problem.

---

### Post by overdrank on 2007-10-08
> **animefan61 said:**
> I opened my computer, because I thought I knew what you were talking about, but I didn't. I unhooked both drives, but I only hooked my 40 gig drive back up. I think what I'm going to have to do is move my hard drives around, but I'm scared I'm going to mess something up. So I may just run this drive for a while, until I get the nerve to try to swap my drives around. Still I don't know if that will solve my problem.

HI maybe this link will help explain
[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=ATA_Jumper_Settings&vgnextoid=cbc974850ce0e010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=ATA_Jumper_Settings&vgnextoid=cbc974850ce0e010VgnVCM100000dd04090aRCRD)
I realize it might not be you hard drive but the principal is the same.

---

### Post by animefan61 on 2007-10-08
Thanks Overdrank, that helps. I noticed that both my drives had jumpers in them, just in different places.  The 40 gig may be set as the master. How would I go about changing the jumpers? Exactly how would I take them out?

---

### Post by animefan61 on 2007-10-09
> **Shazaam said:**
> This might help with jumper settings (it may be different with the brand of drives you have).
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=84&p_created=1005005461&p_sid=iiHNcINi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzQzLDM0MyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWp1bXBlciBzZXR0aW5ncw**&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=84&p_created=1005005461&p_sid=iiHNcINi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzQzLDM0MyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWp1bXBlciBzZXR0aW5ncw**&p_li=&p_topview=1)

Make ANY hardware changes with the pc OFF and UNPLUGGED, touch the pc frame before touching anything else in the pc AFTER you unplug it.
You should have the Windows drive set as MASTER and the other as SLAVE. Change the jumpers if you need to. Plug the pc back in, boot up and as the pc is booting press whatever button you need (delete is standard) to get into the bios. The page that opens should have your drive(s) listed. You should be able to AUTODETECT the drives from that page. If they are fine look in other bios pages for "Boot Order" or similar. Set the Windows drive to boot first. Save and exit the bios and then reboot. If grub still gives you an error on boot after this, load up the Ubuntu livecd, open a terminal and type in..
```
sudo grub-update
``` and you should be good to go.

I did what you said, and now I can load both hard drives through the bios. I need to know how to get both hard drives to come up on boot, so I can choose the hard drive I want to boot up.

---

### Post by Shazaam on 2007-10-09
Ok great job!. Now boot to Windows and see if both drives are in "Device Manager" and in "Disk Management" under "Administration Tools" They should both be there.

---

### Post by animefan61 on 2007-10-09
> **Shazaam said:**
> Ok great job!. Now boot to Windows and see if both drives are in "Device Manager" and in "Disk Management" under "Administration Tools" They should both be there.

I just checked, both drives are there.

---

### Post by Shazaam on 2007-10-09
Can you boot both Windows and Ubuntu now? (without going into the bios)

---

### Post by animefan61 on 2007-10-09
> **Shazaam said:**
> Can you boot both Windows and Ubuntu now? (without going into the bios)

No. I turned my computer off and  I can only boot up windows. I checked both drives in the device manger and it said both were working, so I don't understand why I can't boot up Ubuntu without going into the bios

---

### Post by logos34 on 2007-10-09
So you're saying that everytime you want to boot from the ubuntu disk (40GB) you have to go into the Bios and make it first, but that the next time you reboot it automatically goes into windows unless you reset the bios?

If that's the case you might consider reinstalling Grub on the MBR of the windows disk, so that on bootup you get the grub menu screen, where you can choose either XP or linux.

---

### Post by Shazaam on 2007-10-09
> **logos34 said:**
> So you're saying that everytime you want to boot from the ubuntu disk (40GB) you have to go into the Bios and make it first, but that the next time you reboot it automatically goes into windows unless you reset the bios?

If that's the case you might consider reinstalling Grub on the MBR of the windows disk, so that on bootup you get the grub menu screen, where you can choose either XP or linux.

Exactly. Thank you logos34. That was the next step. We had to fix his jumper/bios problem first.

---

### Post by animefan61 on 2007-10-09
> **logos34 said:**
> So you're saying that everytime you want to boot from the ubuntu disk (40GB) you have to go into the Bios and make it first, but that the next time you reboot it automatically goes into windows unless you reset the bios?

If that's the case you might consider reinstalling Grub on the MBR of the windows disk, so that on bootup you get the grub menu screen, where you can choose either XP or linux.

No, if I set my Ubuntu drive first it will boot up in Ubuntu until I go into the bios and set my Windows drive first, then it will boot up into Windows until I go into the bios and change it to Ubuntu. I just don't get a choice when I boot up.

---

### Post by logos34 on 2007-10-09
that's the way it's supposed to work..there's no bios selection screen that comes up allowing you to choose which drive to boot...you need to use a boot loader to give you a choice of which OS on which drive to boot.  You should set it to boot from the ubuntu hard disk and add a windows entry to the bottom of menu.lst.
[B]
gksudo gedit /boot/grub/menu.lst[/B]

> title        Windows
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by Shazaam on 2007-10-09
animefan61 this page explains grub pretty well....

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can read it carefully and try some of the suggestions if you want to especially the part about re-installing grub.

---

### Post by logos34 on 2007-10-09
actually animefan61 doesn't even have to reinstall grub, just add a windows entry to menu.lst and boot from the ubuntu disk. that would be the easiest way

I was referring to this section
**[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)**

---

### Post by animefan61 on 2007-10-09
Shazaam, Logos, I tried both your suggestions, neither one worked. I kept getting error messages.

---

### Post by logos34 on 2007-10-09
post your fdisk

sudo fdisk -l

also

cat /boot/grub/device.map

---

### Post by animefan61 on 2007-10-09
Here's my terminal:

linda@linda-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1747    14032746    7  HPFS/NTFS
/dev/hda2            1748        1826      634567+   5  Extended
/dev/hda5            1748        1826      634536   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4737    38049921   83  Linux
/dev/hdb2            4738        4865     1028160    5  Extended
/dev/hdb5            4738        4865     1028128+  82  Linux swap / Solaris
linda@linda-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hdb
linda@linda-desktop:~$

---

### Post by logos34 on 2007-10-09
hda1 is windows, so (hd1,0) should work

add windows drive to device.map:

(hd1) /dev/hda

any luck?

---

### Post by animefan61 on 2007-10-09
> **logos34 said:**
> hda1 is windows, so (hd1,0) should work

add windows drive to device.map:

(hd1) /dev/hda

any luck?

Didn't work. How exactly would I add windows to the device.map?

---

### Post by logos34 on 2007-10-09
gksudo gedit /boot/grub/device.map

add windows drive:

> (hd0) /dev/hdb
**(hd1) /dev/hda**

Now the 'map' commands in your windows menu.lst entry can swap the drives.

---

### Post by animefan61 on 2007-10-10
> **logos34 said:**
> gksudo gedit /boot/grub/device.map

add windows drive:



Now the 'map' commands in your windows menu.lst entry can swap the drives.

Okay, I did it and both drives are in the menu list, but when I boot up, the Window's drive isn't in the list with Ubuntu. Is it suppose to be? If it's not then how do I switch between drives?

---

### Post by logos34 on 2007-10-10
Did you add the entry as I suggested in post #20?

Post your menu.lst

---

### Post by animefan61 on 2007-10-10
> **logos34 said:**
> Did you add the entry as I suggested in post #20?

Post your menu.lst

I just did what your post #20 said and it didn't make any difference. Here's my menu.lst



title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
(hd0)	/dev/hdb
(hd1)  /dev/hda

---

### Post by logos34 on 2007-10-10
no, don't put the device.map lines in menu.lst entry:

> 
title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

device.map:

> (hd0) /dev/hdb
(hd1) /dev/hda

---

### Post by animefan61 on 2007-10-10
> **logos34 said:**
> no, don't put the device.map lines in menu.lst entry:



device.map:

This is what's in my menu.lst

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
# kopt=root=UUID=a8f3055a-7459-43e6-94b9-6374f9a9fdc9 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a8f3055a-7459-43e6-94b9-6374f9a9fdc9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a8f3055a-7459-43e6-94b9-6374f9a9fdc9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a8f3055a-7459-43e6-94b9-6374f9a9fdc9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a8f3055a-7459-43e6-94b9-6374f9a9fdc9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by animefan61 on 2007-10-10
logos, I did what you said in post #20 and it worked. I can choose the Windows from the start up screen, but now I have a new problem. My mouse went crazy and I had to shut down the computer, because I couldn't control the mouse. What do I do?

---

### Post by animefan61 on 2007-10-11
I don't know what happened last night, but my computer's working fine this morning. Thank you so much Overdrank,  Shazaam and Logos for all your help, I really appreciate it.

---

### Post by animefan61 on 2007-10-11
> **Shazaam said:**
> Exactly. Thank you logos34. That was the next step. We had to fix his jumper/bios problem first.

I'm actually a her.

---

### Post by Shazaam on 2007-10-11
> **animefan61 said:**
> I'm actually a her.


Please accept my humblest apologies, my favorite word got me again and yes, it made me one (ASSume).
Good to hear you got it sorted out.

---

### Post by animefan61 on 2007-10-11
> **Shazaam said:**
> Please accept my humblest apologies, my favorite word got me again and yes, it made me one (ASSume).
Good to hear you got it sorted out.


That's quite alright, I guess it would be easy to assume I'm a guy. Anyway, yes my computer's working great, and I love being able to choose which drive to load up without having to go into the bios. My husband knows nothing about computers, but I love them, and I love learning how to work on them. Thanks again for all your help.:)

---

