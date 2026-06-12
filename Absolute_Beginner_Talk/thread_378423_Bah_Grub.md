---
title: "Bah Grub"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by torgrot on 2007-03-07
Is there any way to boot Ubuntu 6.10 without the involvement of GRUB in any way.  :(   I have two 160GB drives,  hda is linux/Ubuntu  hdb is WinXP.  hda is partioned as /boot with 20GB and /home as 135GB and /swap as 5GB.  hdb is 140GB WinXP and 20GB swap drive.  This is on a Dell Dimension 4550.  I can install and boot Ubuntu or WinXP for several weeks and then blooey GRUB:(  or something in GRUB goes belly up and it can no longer find Ubuntu on the first drive but boots WinXP on the second drive just fine.  I used GAG and added Ubuntu but when I try to boot it it says there is nothing there to boot.  What gives?  Any assistance as this is getting real old real quick.  While I enjoy Ubuntu, I am ready to throw in the towel  and declare this operating system as not yet ready for prime time.  That is sad as I am a system administrator for a complex OpenVMS system and I can't imagine an ordinary person putting up with this much trouble before calling it quits.

torgrot

---

### Post by taurus on 2007-03-07
Do you have A LiveCD hanging around?  Boot with it and post the output of this command from a temrinal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by torgrot on 2007-03-07
It will have to wait until this evening as I am at work presently.

---

### Post by taurus on 2007-03-07
What is the error message if you can remember right now when you try to boot Ubuntu using GRUB?

---

### Post by torgrot on 2007-03-07
There is no error message the system just reboots when I use GRUB to boot Ubunut.  Mind you that this all worked for several weeks perfectly letting me switch back and forth between operating systems.  I have to keep WinXP in order to get in to work when they call.  They use a proprietary VPN and I have not been able to configure the one in Ubuntu to work with it yet.

GAG has saved me many times in the last couple of months with Ubuntu, allowing me to boot WinXP when Ubuntu has decided that it should no longer function.

torgrot

---

### Post by OBnascar on 2007-03-07
> **torgrot said:**
> While I enjoy Ubuntu, I am ready to throw in the towel  and declare this operating system as not yet ready for prime time.  That is sad as I am a system administrator for a complex OpenVMS system and I can't imagine an ordinary person putting up with this much trouble before calling it quits.torgrot

I felt that way one time myself. I tried Ubuntu for one week and could do practically nothing on it, I wiped it off my computer and went back to WinXP.

About a month later I installed Ubuntu again (I don't know why) after I looked at the manuals/documentation and visited the forums here more often and picked up on some crucial information. I have been using Ubuntu every since and that was two years ago.

Ubuntu is not WinXP, it takes some time to learn Linux. If you had started out on Linux, then learning WinXP would be difficult. My motto is "learning Linux is not difficult, but unlearning Window is.

When you get home after work, you could try this to reinstall grub on your Ubuntu partition.
[COLOR="Green"]To reinstall grub:
Boot from the Live CD. Open a konsole and type:
grub

Then type:
find /boot/grub/stage1

The output will be something like this: hd0,0
Yours may be different. then type:
root (hd0,0)

Use the parameters from the output you got from the find command. Next type:
setup (hd0)

Again using your parameters. When it's done with the setup type:
quit
exit

and reboot[/COLOR]

good luck, I hope you get Ubuntu booting again........cheers

---

### Post by dwblas on 2007-03-07
There are advantages to using GRUB.  However, i used LILO for 10 years.  IMHO it is more stable and easier to use as long as you have a fairly standard, straight forward system.  I'm not convinced that another boot manager would solve your problem however.  Whatever you use may magically disappear after a few weeks.
LILO's freshmeat page
[http://freshmeat.net/projects/lilo/](http://freshmeat.net/projects/lilo/)

---

### Post by torgrot on 2007-03-07
I will try reinstalling grub as suggested this evening.  Actually, I learned VMS and DCL long before I ever looked at Windows.  And probably no one here has ever heard of VMS.  I am able to do most of what I want in Ubuntu, with the caveat, when I can boot it.  I am not unfamiliar with the command line and x-term sessions.  VMS will boot if I type boot at the >> prompt, WinXP will boot if it is on the first hard drive.  Ubuntu depends on IMHO a shakey at best, boot loader called GRUB.  An excellent operating system is hampered by a poor implementation of its boot loader.

torgrot

---

### Post by OBnascar on 2007-03-07
> **torgrot said:**
> I will try reinstalling grub as suggested this evening.  Actually, I learned VMS and DCL long before I ever looked at Windows.  And probably no one here has ever heard of VMS.  I am able to do most of what I want in Ubuntu, with the caveat, when I can boot it.  I am not unfamiliar with the command line and x-term sessions.  VMS will boot if I type boot at the >> prompt, WinXP will boot if it is on the first hard drive.  Ubuntu depends on IMHO a shakey at best, boot loader called GRUB.  An excellent operating system is hampered by a poor implementation of its boot loader.torgrot

Good deal, sounds like you should not have a problem with Ubuntu once you get it to boot, your credentials are ***impressive***.

---

### Post by steve.horsley on 2007-03-07
What you may be able to do is to launch rescue mode on the "alternate" Ubuntu installer CD. This has an option to give you a command prompt in whatever partition you want - in this case I guess it would be something like /dev/hdb1. Once there, use the command
**grub-install /dev/hdb1**
(not just /dev/hdb) to install grub on the Ubuntu root partition rather than on the MBR. 
Now you can have GAG chainload that partition.

---

### Post by dannyboy79 on 2007-03-07
> **torgrot said:**
> I will try reinstalling grub as suggested this evening.  Actually, I learned VMS and DCL long before I ever looked at Windows.  And probably no one here has ever heard of VMS.  I am able to do most of what I want in Ubuntu, with the caveat, when I can boot it.  I am not unfamiliar with the command line and x-term sessions.  VMS will boot if I type boot at the >> prompt, WinXP will boot if it is on the first hard drive.  Ubuntu depends on IMHO a shakey at best, boot loader called GRUB.  An excellent operating system is hampered by a poor implementation of its boot loader.

torgrot

grub is a very versatile boot loader. I have read that many distro's have switched from lilo to grub! In fact, here is an article of grub being able to boot 100+ systems which are contained within 4 different hard drives which is then broken into 144 different partitions ([http://www.justlinux.com/forum/showthread.php?threadid=143973)](http://www.justlinux.com/forum/showthread.php?threadid=143973)). If you can show me any other boot loader that can do this than I'll stop promoting grub but for you to say that ubuntu is hampered by grub is not grub's fault. I would say it's because of your unfamilarity with grub. Your mbr must have been messed up by either winbloz, ubuntu or whatever other os you're running but it doesn't just happen for no reason.

---

### Post by torgrot on 2007-03-07
I will agree that it doesn't happen for no reason.  But lets' not get personal here.  I came with a problem, several people have offered options to restore grub, which as I said in my humble opinion is a major flaw in Ubuntu for the average person.  I haven't done anything that would cause Ubuntu to trash the MBR, and Windows can't even see it.  As I said in the beginning, I was using it successfully to switch between the two operating systems and then I go to boot Ubuntu via GRUB and it fails.  This has not been the only time this has occurred.  I replaced the hard drive after the first failure, since it would not pass Western Digitals own diagnostic.  I have run the Seagate diagnostics on both hard drives and both pass with nothing even close to marginal.  I ruled out the hardware.  Since I am a little frightened by losing access to Ubuntu regularly, the only things I have done recently were to set up e-mail and Firefox.  If setting up e-mail accounts and Firefox can corrupt Ubuntu then this is really not the operating system for the desktop.

torgrot

---

### Post by torgrot on 2007-03-07
> **taurus said:**
> Do you have A LiveCD hanging around?  Boot with it and post the output of this command from a temrinal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+  83  Linux
/dev/hda2            2551       18887   131226952+   5  Extended
/dev/hda3           18888       19457     4578525   82  Linux swap / Solaris
/dev/hda5            2551       18887   131226921   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/hdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/hdb5           16710       19457    22073278+   7  HPFS/NTFS

This is the output

---

### Post by torgrot on 2007-03-07
I was able to re-install grub to the MBR of the Ubuntu disk using the suggestions I was given.  I still feel that this is a less than ideal solution.  Can't Ubuntu/Linux be made to boot with out grub?

---

### Post by dwblas on 2007-03-07
> something in GRUB goes belly up and it can no longer find Ubuntu on the first driveThere was a new kernel maybe two weeks ago, at least for Feisty.  I'm wondering if it is that the update reconfigured GRUB for the new kernel but for some reason it can't find it.  See what's in /boot.  For now, is menu.lst booting the old kernel,  vmlinuz-2.6.17-10-generic, as that was the one that was working before.  If that is the problem, you can go back and try the newer kernel and see what happens.  A work around is good, but solving the problem would be better.  As far as GRUB verses other boot managers goes, Linux is about having a choice.

---

### Post by louieb on 2007-03-07
> And probably no one here has ever heard of VMS.
If I remember right VMS was some operating system put out by DEC or Unisys or some player like that. And DCL is the DEC equivalent of IBM's JCL (job control language).   I'm an old IBM mainframe guy started out on MVS, TSO, VM/CMS, IMS and a buch of other stuff that doesn't  mean much today. 

You have written a lot of stuff and about all you have said is:
 
> **torgrot said:**
> Ubuntu depends on IMHO a shakey at best, boot loader called GRUB.  An excellent operating system is hampered by a poor implementation of its boot loader.torgrot

Do you remember the stories about the Denver Airport and OS/2. Now that  what I call poor implementation. 

But back to GRUB getting messed up. Doesn't sound like the code in the MBR is getting messed up. Its just a pointer to the the GRUB program /boot/grub/stage2. and if it were hosed you would not get  to the GRUB menu. 
If you don't get the GRUB menu what was the last system used? Nothing in a normal Ubuntu install would touch the MBR. But there are windows viruses that do.  
You did not say what you were doing just prior to being unable to boot. 
Once install the GRUB program are static. The only thing that changes is the configuration file /boot/grub/menu.lst.  I've had my configuration file messed up when doing an automatic kernel update on a machine with two Linux installs. (Ubuntu and FC5) I've also lost the ability to boot XP at kernel update time because I had my XP entry in the wrong place.   

Are you running anything but 1 install of Ubuntu and an XP install? 
Kernel updates aside I've found GRUB to be stable and works. 
You have an odd problem and it would be interesting to find what changed.

When a user comes up to me and says "it use to work" (one of there favorite things to say) it means one of two things, either something changed and it wasn't tested thoroughly. OR it never did work the way he wanted it to and he is tying to get a software change in without going through approval channels.

---

### Post by mar225 on 2007-03-07
Something I found by accident a while back when Grub was driving me nuts.

On my machine I can hit F12 at boot and bring up a menu that lets me pick which drive I want to boot. It has nothing to do with the OS its part of the bios somehow. Just thought I would mention it. I use it every day.

---

### Post by torgrot on 2007-03-07
Yes VMS is still alive and kicking, latest is 8.3 on the Itanium platform and DCL stand for Digital Command Language, the equivalent of bash.  

And yes it does work very well when it works.  My complaint has been all along that every once in a while it doesn't work.  

I have lost the ability to boot WinXP on hdb at times until I found GAG.  

I have had to re-install and download 200MB of patches to Ubuntu at least twice, because like Microsoft the installation CD is out of date.

This time I could still boot WinXP from the GRUB menu, I just couldn't boot Ubuntu.  So I would guess that this means that Ubuntu was the culprit. 

Here is the menu.lst  and before some one points out the obvious that WinXP is in there twice, I know that.  The kernel that I am booting indicates in the menu that it is Ubuntu, kernel 2.6.17-11-generic

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

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
# kopt=root=UUID=01750166-717e-44d6-81d1-9e039b4d21fe ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by torgrot on 2007-03-07
This is really curious.  I booted into Ubuntu after repairing GRUB.  I then shut down the system and attempted to reboot.  I got the GRUB menu but neither operating system would boot.  I could select them but they would just reboot again.  

I attempted to use GAG to boot Ubuntu and it tells me there is no partion loader there.  
I then booted into WinXP via GAG and am posting this from WinXP.

So it would appear that GRUB has gone south again.

torgrot

---

### Post by louieb on 2007-03-07
Ok bah grub. :(
You don't happen to have [ fs-driver ]("http://www.fs-driver.org/") installed in XP do you. It for reading and writing to ext2/ext3 partitions from windows.
Ubuntu uses the Debian updater to modify /boot/grub/menu.lst when there is a kernel update. and it should have created a backup with the same name ending with a ~.   The last entry is for XP it should not have changed and I wonder if it did. 
As far as the Ubuntu entry only the kernel  and initrd file names should have changed and those files should be in /boot. In particular the two things that should not have changed are the [COLOR=Red]root line[/COLOR] and on the kernel line the [COLOR=Red]root=[/COLOR]   parms   if they did then the updater is the culprit. If not I'm cluless.

---

### Post by torgrot on 2007-03-08
No I don't have fs-driver installed.  And now with a new wrinkle, when I boot off the Live CD it doesn't install ipv4 on my ethernet either.  It only shows ipv6 on eth0.  So I have no way to get here from the live CD.  I have to boot back into WinXP to see the network.

I have the 6.10 iso image and I will try burning a new CD, but my hopes for that are dimming.  I ran the disk diagnostics on both hard drive just to rule out a hardware problem with the disk and they both pass with flying colors.

This is rapidly becoming a quagmire and I am not sure how much more time I want to invest in Ubuntu.  I will install it once more, but this is becoming a real waste of time.

torgrot

---

### Post by torgrot on 2007-03-08
> **mar225 said:**
> Something I found by accident a while back when Grub was driving me nuts.

On my machine I can hit F12 at boot and bring up a menu that lets me pick which drive I want to boot. It has nothing to do with the OS its part of the bios somehow. Just thought I would mention it. I use it every day.

The bios on my Dell 4550 doesn't allow booting from other than the primary master hard drive.

Thanks for the reply.

---

### Post by torgrot on 2007-03-08
I burned the CD and re-installed.  All went well.  I rebooted and selected Ubuntu from the GRUB menu.  The computer rebooted.  I selected Ubuntu again and it started.  I allowed it to update overnight.  I shut down and rebooted.  Again I selected Ubuntu and it rebooted.  I select Ubuntu again and it started.  I shut down and rebooted.  I select WinXP and it started.  I shut down and rebooted.  I select Ubuntu and it rebooted.  I selected Ubuntu and it started.  Again I say that GRUB is shakey at best.

Here is fsck -l
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2568    20627428+  83  Linux
/dev/hda2            2569       19187   133492117+  83  Linux
/dev/hda3           19188       19457     2168775   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/hdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/hdb5           16710       19457    22073278+   7  HPFS/NTFS

and here is the menu.lst 
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
# kopt=root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

So why do I have to reboot twice to start Ubuntu?

torgrot

---

### Post by dannyboy79 on 2007-03-08
> **torgrot said:**
>  I will agree that it doesn't happen for no reason.  But lets' not get personal here.  
Who's getting personal? I merely pointed out a link which lists several reasons why grub is one of the best if not the best boot loader for multi-boot installs.
> **torgrot said:**
>  Windows can't even see it.   
Any OS can screw up the MBR, just because you can't see it thru winbloz doesn't mean winbloz can't see it and mess it up!
> **torgrot said:**
> 
As I said in the beginning, I was using it successfully to switch between the two operating systems and then I go to boot Ubuntu via GRUB and it fails.  
ok well now I understand your problem a little better. If grub appears with a menu and your 2 OS options are there then your MBR is NOT messed up, since grub is installed into the mbr and it is doing it's job and it's loading. It sounds to me like your /boot/grub/menu.lst got messed up somehow. Also, if you ever upgrade your kernel (ie: 2.6.17-12 and then go to 2.6.17-13, your menu.lst can get hosed due to grub not auto-updating it correctly) I do think this is a downfall of grub, it doesn't auto-update my menu.lst correctly either. I have a /boot partition and so my #groot line (default grub root device) within menu.lst looks like this: #groot (hd2,1) because I have the /boot partition installed on the master of ide channel 1. what auto-update of grub does is simply make the #groot line the same as where the root partition is of your linux install based on what is in the device.map file, so my menu.lst file's #groot line was changed to hd2,2 so therefore i couldn't boot ubuntu for the life of me.
> **torgrot said:**
> 
 Since I am a little frightened by losing access to Ubuntu regularly, the only things I have done recently were to set up e-mail and Firefox.  If setting up e-mail accounts and Firefox can corrupt Ubuntu then this is really not the operating system for the desktop. 
Sounds to me like you need to become more knowledgable and understand your boot loader more before you can fault it for not being a good piece of software. Download yourself the super grub disk or make a grub floppy and you'll always be able to boot your ubuntu if your grub install becomes hosed.

Below I will paste an awesome walk thru of how to troubleshoot a hosed grub install. I give FULL credit to irrational_e as he wrote it (it was copied from here: [http://www.ubuntuforums.org/showthread.php?p=2255846&highlight=device.map#post2255846):](http://www.ubuntuforums.org/showthread.php?p=2255846&highlight=device.map#post2255846):)

I have been trying for a WEEK without any remote sniff of success to fix GRUB.
My setup:

Hda = WIndows XP. Master on IDE0 (Work drive)
Hdd = Windows XP. Slave on IDE1 (Occasional backup drive that I now wanted to remove)
Sda = Ubuntu Edgy on S-Ata (Hopefully new work drive)

The problem: 
Installed Edgy with all drives in the machine, removing the hdd cause GRUB error21 in Stage 1.5

I finally fixed the problem after thinking about it for a while and trying out some things.

There are 2 files in /boot/grub. device.map and menu.lst that make a difference. Basically they tell what shows up on the GRUB menu on bootup it seems.

steps:

1: Remove Hdd
2: Boot using Ubuntu Edgy install CD
3: Mount the Edgy drive as explained earlier like this:

In the install CD gui open a terminal or use ctrl+alt+f1 for a different term.
Changes as root user!
> sudo bash """switch to root user"""
> mkdir ubuntumnt """make a mount point"""
> mount -t ext3 /dev/sda1 ubuntumnt """Mount ubuntu drive. the '1' is a partition (s-ata drive, partition 1). In other words, mount the partition, not the drive"""

4: Now that you have a point edit the device.map and menu/lst files

> vi ubuntumnt/boot/grub/device.map
"""This shows the contents of the device.map file"""
hd0 /dev/hda
hd1 /dev/hdd
hd2 /dev/sda

"""
Edit above to remove the hdd. Since the IDE drive is read first by the system, by observation the s-ata drive will be hd(x) where x is the number after all ide drives (it seems to me), so 4 ides and an s-ata will result in hd4 being the sata drive.
Now we have:
"""

hd0 /dev/hda
hd1 /dev/sda

"""save the file and edit the menu.lst""
> vi ubuntumnt/boot/grub/menu.lst

"""At the bottom you will have entries like this"""

************************************************** *********************
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd2,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd2,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd2,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
chainloader +1

************************************************** *******************************

"""Edit the file to change the drive numbers to correspond to the device.map and remove the hdd so it now look slike this:
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

************************************************** *******************************
"""Save the file and enter the grub interface"""

> grub

Now we show where the root is. Since we mounted the edgy partition, we can see the grub folder. (Not mounting is the reason why "find /boot/grub/stage1" sometimes does not work as asked in above posts.
>find /boot/grub/stage1
hd (1,0) """This should be you edgy drive. In my case hd(1,0) after I removed hdd. 2nd Physical drive 2, partition 1. Meaning sda1 in my case"""

Now we follow previous steps in this HOW TO
root (hd1,0) """Define the root partition on the drive
setup (hd1) """Setup grub on the drive"""

"""At this point all previous posts said quit and restart, yet I still got the Error21. I eventually decided the MBR on the hda windows disk was messed up too.
Since I know the windows drive is hd0 I also did"""
setup (hd0)
quit

"""Now we restart the machine and voila! IT works again

--------------------------------------------------------------------------------

---

### Post by dannyboy79 on 2007-03-08
> **torgrot said:**
> I was able to re-install grub to the MBR of the Ubuntu disk using the suggestions I was given.  I still feel that this is a less than ideal solution.  Can't Ubuntu/Linux be made to boot with out grub?

sure it can, you can boot linux from NTDLR. here is the instructions if you choose to do it this but it's actually harder to setup.

[http://www.astahost.com/info.php/using-ntloader-boot-linux_t1510.html](http://www.astahost.com/info.php/using-ntloader-boot-linux_t1510.html)

---

### Post by Malac on 2007-03-08
I can't help thinking that this has something to do with you having two repeated entries for the WinXP system in the menu.lst file.
How did that happen there should be only one.
Any non-Ubuntu OS should really go after Ubuntu where the second entry is.
This should aid with updates or kernels etc.
And I have never been happy with the map swap to fool Windows (which seems a bit hacky to me) especially after you have just told GRUB which hd your OS is on. I wonder if these two things are conspiring to confuse GRUB as to which partition you want to "makeactive".
Could you not just swap the drives round?
Personally I have always run XP's bootloader on hd0 as per MS own recommendations. "Re-mapping of Windows XP drive assignments may cause erratic behaviour........."

---

### Post by torgrot on 2007-03-08
Ok,  this is a complete reinstall from a LiveCD for Ubuntu 6.10, with all of the updates installed.  There is only one WinXP entry in menu.lst.  menu.lst is as Ubuntu wants it after all of the updates were applied.

Here is the scenario.  No Windows involved here.
Start with computer shut down completely.
Power up select Ubunut from GRUB menu, computer reboots.
Again select Ubuntu from GRUB menu, Ubuntu starts.
Select Restart from Ubunutu desktop, Ubuntu shuts down and computer reboots.
Select Ubuntu form GRUB menu, computer reboots
Again Select Ubuntu from GRUB menu, Ubuntu starts.

Here is the scenario with Windows involved.
Start with computer shut down completely.
Power up and select WinXP from GRUB menu, WinXP starts.
Select Restart from WinXP, computer reboots
Select WinXP from GRUB menu, WinXP starts.
Select Restart from WinXP, computer reboots
Select Ubuntu form GRUB menu, computer reboots
Again select Ubuntu from GRUB menu, Ubuntu starts maybe or may reboot again and again until I select WinXP from GRUB menu and WinXP starts.
Usually at this point Ubuntu/GRUB can no longer start Ubuntu and I may or may not be able to boot WinXP without using GAG to boot WinXP.
Attempts to boot Ubuntu with GAG result in error message indicating there was not a bootloader in that partition.

torgrot

---

### Post by Malac on 2007-03-08
Sounds like you have ended up with two Grub menus one on the MBR of disk 1 pointing to another one possibly on the other disk MBR or the start of one of the partitions. This is possibly why you are having to do it twice and also why upgrades, etc. are going awry, which GRUB do they update? (rhetorical)

The only other thing I can suggest is that in Windows you have some sort of AV set to protect the boot record and it is doing some sort of automatic restore which again is mucking things up as it doesn't know about the Ubuntu System.

You may even have both.

I really would move the WinXP to Disk 1 do a fixmbr and start with a clean Windows System and put Ubuntu on Disk 2. As recommend by loads of threads on this (and microsoft's own) forum.

Sorry I'm out of ideas other than that.

---

### Post by louieb on 2007-03-08
The only part  thing I can explain is GAG not booting Ubuntu. GAG is looking for Ubuntu boot loader  in the MBR of the install partition. But its not there its in the MBR of the hard drive.

Your last menu.lst is odd, your 2 XP entries show XP to be on different partitions, different drives in fact. Leads me to think one of two things. GRUB isn't processing the information from BIOS correctly. or BIOS itself is messing up. Its just like going into BIOS and changing the boot drive, but I think you said earlier you PC's did not support  that. At this point I a clueless. How old is the PC, new battery time maybe? I doubt it though I've got a couple PC's over 10 years old and never change the battery and don't show any signs that there is a need.

---

### Post by torgrot on 2007-03-08
With all of the problems I have had with GRUB, I really can't afford to put it in the MBR of my WinXP disk and take the chance that I will have to dig out a dos floppy and run FDISK/MBR  on that drive to boot into WinXP.  I have never installed GRUB to the WinXP disk drive.  My first installation of Ubuntu 6.06 was with the WinXP drive removed from the system.  As I got more confident with Ubuntu, I reinstalled the WinXP drive as the slave on the primary controller.  I then followed the instructions in other posts here to allow me to boot the WinXP on hdb from GRUB.  Since that time, I have installed Ubuntu 6.10 to hda from the LiveCD several times and it has added the entry to boot WinXP.

This evening I will dig out that floppy.  Disconnect hda, move hdb to primary master and run fdisk/mbr on the WinXP disk.  If GRUB got installed there some how, that should remove it, am I correct?  

I will then reconnect Ubuntu disk as primary master and WinXP as primary slave.

We shall see.

torgrot

---

### Post by dannyboy79 on 2007-03-08
some questions first. are you using cable select or master and slave? if you're using cable select then stop this, I find this to be a problem more than not. nail it down for the bios, use master and slave. your bios has to have a location in it that states which item gets booted and in what order correct (ie: cdrom, floppy, hard disk)? also, is there another place in your bios that has a list of hard drives, if so, can you move them by using the arrow up or arrow down key? if you can, then this is the way you can put which hard drive gets booted by the bios. can you show me your sudo fdisk -l again? did you create a boot partition again?

---

### Post by dannyboy79 on 2007-03-08
> **torgrot said:**
> This evening I will dig out that floppy.  Disconnect hda, move hdb to primary master and run fdisk/mbr on the WinXP disk.  If GRUB got installed there some how, that should remove it, am I correct?  

I will then reconnect Ubuntu disk as primary master and WinXP as primary slave.

We shall see.

torgrot

that would be correct but you can also use the recovery console on your winxp cd. can you make sure you read my previous post, it has many questions that need to be answered so we can troubleshoot this.

---

### Post by torgrot on 2007-03-08
> **dannyboy79 said:**
> some questions first. are you using cable select or master and slave? if you're using cable select then stop this, I find this to be a problem more than not. nail it down for the bios, use master and slave. your bios has to have a location in it that states which item gets booted and in what order correct (ie: cdrom, floppy, hard disk)? also, is there another place in your bios that has a list of hard drives, if so, can you move them by using the arrow up or arrow down key? if you can, then this is the way you can put which hard drive gets booted by the bios. can you show me your sudo fdisk -l again? did you create a boot partition again?

I do use cable select.  I haven't seen an ATA 100 cable that wasn't cable select.  The bios shows ide primary master set to auto and 160gb, ide primary slave set to auto and 160gb  ide secondary are my cd and dvd drives.  They are also cable select.  boot order can consist of three items only.  Currently it is set to floppy, ide-cdrom, and first hard drive.  I can only enable or disable or re-arrange these.  I can not pick any other device.  So I can't select which hard drive is booted via anything here.  During boot, I can press F12 and then I have a selection of floppy disk, first hard drive, ide-cdrom, usb-device.  I have no idea where or even if this can be changed.  It would appear to be hardcoded in the boot roms someplace.

torgrot

---

### Post by dannyboy79 on 2007-03-08
> **torgrot said:**
>  I do use cable select.  I haven't seen an ATA 100 cable that wasn't cable select.    Cables have nothing to do with cable select. it's the jumper on the hard drive that makes the drive be a master, a slave, or make the drive work using the way it is hooked up to the cable, which that is the cable select option. You want to change this I would say. Master and slave is a much better choice as your not having the hard drive figure out where it is on the cable, it just knows it's either the master or the slave based on it's jumper.
> **torgrot said:**
> The bios shows ide primary master set to auto and 160gb, ide primary slave set to auto and 160gb.

newer bios's have enabled a way to rearrange hard drives that are shown in a list. it's not the first page of a bios that simply shows the different hard drives on the different channels. under this other tab, there is a list of hard drives, this is so that a person doesn't have to open there computer and move around hard drives between the ide0 channel and the ide1 channel. they can simply move the drive up or down and which ever 1 is first, that is the 1 that is booted BUT before it is booted, the bios first looks at the other list of the "order" in which stuff is booted, crdom, floppy, hdd etc etc.  

you could always try what I suggested, use the super grub disk to boot your ubuntu install or your windows install. or follow my link to use ntldr and stop using grub if you don't like it. OR
like the other guy said, switch your disks around and try grub on the winbloz mbr.

---

### Post by torgrot on 2007-03-08
How many times do I have to explain this is a Dell 4550.  Its a couple of years old.  I can't select which drive to boot from in the BIOS.  I don't want to put GRUB in the MBR on the Windows disk.  I think it is not very good software.  I can't afford in my job to lose my ability to connect to work.  I am a system administrator.  I can't connect through our VPN to my company.  I have to have windows available at home.  Deal with it DannyBoy79.  You can chose to not run windows, I can't.

torgrot

---

### Post by confused57 on 2007-03-09
> **torgrot said:**
> How many times do I have to explain this is a Dell 4550.  Its a couple of years old.  I can't select which drive to boot from in the BIOS.  I don't want to put GRUB in the MBR on the Windows disk.  I think it is not very good software.  I can't afford in my job to lose my ability to connect to work.  I am a system administrator.  I can't connect through our VPN to my company.  I have to have windows available at home.  Deal with it DannyBoy79.  You can chose to not run windows, I can't.

torgrot

I also have a Dell Dimension 4550 and I haven't found a way yet to boot first to the slave drive on the primary IDE controller...I have no earthly idea why you're having the problems you're having with Edgy.  I have Dapper installed on my master drive and Windows on my slave drive:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

The only suggestion I could offer would be to try Dapper, which has worked very well on my pc.

---

### Post by torgrot on 2007-03-09
Thank you.  I followed your suggestions to set it up this way in the beginning, for most of the same reasons as you.  I just can't not be able to boot windows when work calls.

---

### Post by Herman on 2007-03-09
Hello torgrot,
> Is there any way to boot Ubuntu 6.10 without the involvement of GRUB in any way.  :sad:
I can't really see what exactly your problem is so far, from reading and re-reading this thread.
I do have a question or two. 
What is in your /dev/hda1 1 2568 20627428+ 83 Linux partition that you are calling a /boot partition? Is that your root partition?
Also I noticed that your first hard disk doesn't have any boot flag in your fdisk output. There was one in your original fdisk output, but not in the one or after you re-installed. I wonder what the reason for that could be.

The reason why GAG Boot Manager doesn't boot Ubuntu is because it isn't a bootloader, it's a boot manager. It can boot an operating system by the bootsector, but it can't directly boot a kernel without a boot loader there to take over and do that part of the job.
It boots Windows fine, because by default, Windows has a bootable boot sector.
Ubuntu's bootsector is not bootable by default. It is simple to install a boot loader's stage1 code to it and make it bootable. If you do that, then you an boot Ubuntu with GAG Boot Manager.
You can install grub to your Ubuntu boot sector, or if you want to try something different, you can install Lilo there instead. You will need to install Lilo in Ubuntu first. It's quite alright to have both Grub and Lilo in Ubuntu at the same time. 
If you are interested in trying that, here's how to install Lilo in Ubuntu,         [Install Lilo with apt-get from terminal.]("http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_terminal")
After you install Lilo in Ubuntu, you can then install Lilo to your Ubuntu boot sector. You can do that by running  liloconfig.  [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig")

If you would find it easier to install grub to your Ubuntu boot sector, here's a link to some info on how to install grub from just about anywhere to just about anywhere you like.                                                           [Re-install Grub with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Also, feel free to visit my page on GAG Boot Manager, the link is in my signature, under this post. If you like GAG you might consider installing GAG to MBR, overwriting Grub's stage1 and stage1_5 in the first track of the hard disk.

That would be a good test to see if there is really something wrong with Grub, or if there's a gremlin in your BIOS or an intermittent hardware fault of some kind that needs to be tracked down. I would be interested to hear if that arrangement clears all your problems up or not.

---

### Post by Malac on 2007-03-09
Agree with Herman ^^ after having read the reports about mixed PATA/SATA systems. 
[https://launchpad.net/ubuntu/+source/grub/+bug/8497](https://launchpad.net/ubuntu/+source/grub/+bug/8497)

This might mean this is whats's happening when yours boots off one disk, then the other or does the map swap.

---

### Post by dannyboy79 on 2007-03-09
> **torgrot said:**
>  How many times do I have to explain this is a Dell 4550.  Its a couple of years old.  I can't select which drive to boot from in the BIOS. 
WOOOOOOO, settle down there big guy. You came here for help did you not? I am merely trying to hellp you. I was simply informing you about how newer bios's have a new feature in them to allow the rearranging of the disks, no where did I say that you should have this in your bios!!! 
> **torgrot said:**
>  I don't want to put GRUB in the MBR on the Windows disk.  I think it is not very good software.   
Then don't. Your welcome to your opinion.
> **torgrot said:**
>  I can't afford in my job to lose my ability to connect to work.  I am a system administrator.  I can't connect through our VPN to my company.  I have to have windows available at home.   
If you can't afford to lose access to winxp than I suggest either changing your boot loader or download the super grub disk, as this can boot any os anywhere in your computer, it searches all the drives for boot.ini, ntldr.com or whatever the files are and boots your windows install. also, it will boot a linux distro from it's menu as well. you simply boot the super grub disk (cd) and pick from the menu. or you could create a grub floppy like the other thread I linked to where the guy used it to boot over 100+ os's.
> **torgrot said:**
>  Deal with it DannyBoy79.  You can chose to not run windows, I can't. 
Deal with what? I still use windows xp pro for a few things so I am not sure why you would say this?

You keep complaining about grub but yet you stick with it, WHY????? Use NTLDR to boot your os's!!! I provided you a link but you probably didn't even attempt to do this. When you come to a forum and ask for help, don't get all huffy-puffy when people try to help, it'll just make them not want to help you anymore. Also, in order to ever fix something, it's a good idea to understand how it works, maybe you should read about how boot loaders work and you might just be able to nail down your problem.

---

### Post by torgrot on 2007-03-09
Herman, Primary master drive hda which has three primary partions they are mounted / /home /swap  all of ubuntu went into /  as I would expect it to.  Other than creating three partions this is a straight install of Ubuntu 6.10 from a LiveCD.  After the install I updated it using synaptic.  

Last night, I moved the Windows disk to the Primary master.  I ran fdisk /mbr to be sure that GRUB was not installed in the MBR of the Windows disk.   

I booted off the primary master several times directly into windows with no problems.  I am going to assume that this means there is no GRUB on the windows disk.

Next, I disconnected the windows drive and removed it completely.  I reconnected the Ubuntu drive as Primary master and booted.

GRUB menu comes up select Ubuntu press enter get message starting up system reboots
GRUB menu comes up do this again and it may or may not boot.  Sometimes if I press e to edit the commands and then b it will actually start Ubuntu and sometimes it will not.

When I get home I will follow the suggestions on your web page to re-install grub to both the MBR and the / partition.

I too saw that there was no asterisk anywhere on hda and wondered about that.  Should there be a makeactive command in the menu.lst for the Ubuntu entries?  Or could this be done with GPartEd?

I have read your pages about GRUB and that is where I originally saw GAG which has saved me by allowing me to boot windows off the second hard drive when GRUB/Ubuntu no longer works.

So is this a problem with GRUB or is it a problem with my Ubuntu Installation?  

torgrot

---

### Post by dannyboy79 on 2007-03-09
here is a bug report which suggests that this is a windows issue possibly. [https://launchpad.net/ubuntu/+source/grub/+bug/23666](https://launchpad.net/ubuntu/+source/grub/+bug/23666)


or even here (sounds way to close to the problem you're having it's scary):
[https://launchpad.net/ubuntu/+source/grub/+bug/26058](https://launchpad.net/ubuntu/+source/grub/+bug/26058)

I do hop eyou get this resolved. as I have suggested in the past, go with lilo or ntldr as your boot loader

---

### Post by torgrot on 2007-03-09
I did look at using ntldr, but my understanding of the article you posted was that it simply created a file which contains an image of the MBR that contains GRUB and then uses that to boot Ubuntu.  Since it appears to me that GRUB is suspect, I didn't think that was a practical solution.  It is kind of a catch 22, use ntldr to load GRUB to boot Ubuntu.  It still has the for me problematic GRUB in the mix.  

I used LILO many years ago with Red Hat and never liked it.  I will look again at it, but when I used it, it was always problematic to maintain.  One of the features that I like about Ubuntu is that it uses Synaptic and resolves the dependencies and configurations.  I would as I understand it give some of that up as it relates to the kernel.

I read all of the links you listed.  I agree that it is similar except when I removed the windows drive completely, re-installed grub and still get the same problem.  I never booted into windows.  This was with an all Ubuntu setup.  

The second link seems to have at its root dynamic disks.  I have a passing familiarity with that.  While I won't swear that the Windows disk is not a dynamic disk, since it is something to be done after installation, I believe I would remember converting to a dynamic disk.  Also unless Ubuntu also supports a dynamic disk arrangement in the Ubuntu only scenario I tried last night then there would be nothing to write the Dynamic datat to the MBR.  

torgrot

---

### Post by Herman on 2007-03-09
> Primary master drive hda which has three primary partions they are mounted / /home /swap all of ubuntu went into / as I would expect it to. Other than creating three partions this is a straight install of Ubuntu 6.10 from a LiveCD. After the install I updated it using synaptic. Okay, thank you for clearing that up. :)
> Last night, I moved the Windows disk to the Primary master. I ran fdisk /mbr to be sure that GRUB was not installed in the MBR of the Windows disk. 
I booted off the primary master several times directly into windows with no problems. I am going to assume that this means there is no GRUB on the windows disk.
Okay. I think your Windows disk was originally (hd1), or Primary slave. Grub is normally installed to (hd0), so unless you installed grub to MBR there yourself it should have your Windows boot loader code in it, but it does no harm to run FIXMBR . The MBR is made of the same material as the rest of the hard disk, it can be written and re-wirtten to as many times as we like, it won't wear out.
>  Next, I disconnected the windows drive and removed it completely.  I reconnected the Ubuntu drive as Primary master and booted.Can you confirm that you have the blue end of the cable plugged in to your motherboard and the black end plugged into the hard disk you want to be set as master, with the hard drive jumper in the cable select position?  Thanks.
>  When I get home I will follow the suggestions on your web page to re-install grub to both the MBR and the / partition.Okay, good. That will give you more ways to boot Ubuntu, you'll be able to boot with GAG Boot Manager then. I'm interested to find out how well that works. If GAG Boot Manager has problems too, then it could be a hardware related issue. 
Installing Grub to the Ubuntu boot sector is slightly better than Lilo in the long term, but I normally install Lilo there for something different, since I normally boot with Grub. When you use Lilo, you need to manually update it when you receive a new kernel, where Grub will do that automatically. But some people still prefer sticking with Lilo, they claim it's more reliable. 
> I too saw that there was no asterisk anywhere on hda and wondered about that. Should there be a makeactive command in the menu.lst for the Ubuntu entries? Or could this be done with GPartEd?
I don't know if that might be a symptom or a cause, but it might be a clue that could help solve your problem. That's the reason why I'm asking if you can confirm your cable arrangement and jumper settings. Grub should set that with its 'makeactive' command automatically. You can also use almost any hard disk partitioning software to set your boot flag. GParted is my favorite.
> I have read your pages about GRUB and that is where I originally saw GAG which has saved me by allowing me to boot windows off the second hard drive when GRUB/Ubuntu no longer works.That's good, that's why I made that web page. [GAG Boot Manager]("http://gag.sourceforge.net/") has helped a lot of people, especiaily when they rely on being able to boot Windows and they have a temporary problem with Grub. Some people like GAG so much they install it to MBR and keep on using it. It has it's advantages. One is that it installs to the normally unused first track of the hard disk. That means it is 'operating system independent'. (You can deleted an operating system along with its boot loader and GAG will still be there to boot your other installed systems. 
Nowadays [Super Grub Disk]("http://supergrub.forjamari.linex.org/") is more popular for emergency booting. It has more functions. GAG Boot Manager in MBR or floppy disks writes your setting to disk though, (saves your settings), so if you need to emergency boot Windows more than once only, GAG can be more convenient for that reason. I'm glad your found my web page useful, and thanks for reading it. :)
>  So is this a problem with GRUB or is it a problem with my Ubuntu Installation?   So far it could be almost anything. More testing and experiments will likely be needed. If we think of the right things to try, and we are a little bit lucky, we should be able to sort it out fairly quickly.  I can't prove it yet, if I was a betting man, I'd bet you have some kind of hardware problem.

Regards, Herman :)

---

### Post by torgrot on 2007-03-09
> **Herman said:**
> 
Can you confirm that you have the blue end of the cable plugged in to your motherboard and the black end plugged into the hard disk you want to be set as master, with the hard drive jumper in the cable select position?  
Yes the blue end is on the motherboard and the black is connected to the Ubuntu drive.
> **Herman said:**
> 
I don't know if that might be a symptom or a cause, but it might be a clue that could help solve your problem. That's the reason why I'm asking if you can confirm your cable arrangement and jumper settings. Grub should set that with its 'makeactive' command automatically. You can also use almost any hard disk partitioning software to set your boot flag. GParted is my favorite.

There is no make active in the menu.lst for any of the entries for Ubuntu only the Windows XP entry.
> **Herman said:**
> 
Nowadays [Super Grub Disk]("http://supergrub.forjamari.linex.org/") is more popular for emergency booting. It has more functions. GAG Boot Manager in MBR or floppy disks writes your setting to disk though, (saves your settings), so if you need to emergency boot Windows more than once only, GAG can be more convenient for that reason. I'm glad your found my web page useful, and thanks for reading it. :)

I am not fond of Super Grub Disk.  I had to restore from a backup the last time I used it on a Windows Partition.
> **Herman said:**
> 
 So far it could be almost anything. More testing and experiments will likely be needed. If we think of the right things to try, and we are a little bit lucky, we should be able to sort it out fairly quickly.  I can't prove it yet, if I was a betting man, I'd bet you have some kind of hardware problem.

Regards, Herman :)

I've run the Seagate diagnostics on both of the hardrives and the controller and it found nothing.  I have also run memtest overnight and it also found no problems.

I am about to re-install GRUB using your instructions.  To install it to the first partition on the first harddrive is setup (hd0,0).  Do the number partitions starting from zero also?

torgrot

---

### Post by dannyboy79 on 2007-03-09
yes, hd0,0 will insall grub into the boot sector of that drive. heres a guide for help if need be. [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

---

### Post by Herman on 2007-03-09
> I am about to re-install GRUB using your instructions. To install it to the first partition on the first harddrive is setup (hd0,0). Do the number partitions starting from zero also? That looks right. Use dannyboy79's guide or [A Quick Guide to Grub's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
> Yes the blue end is on the motherboard and the black is connected to the Ubuntu drive. Good then, can you also confirm that you have the hard drive jumper set in the cable select position please? :)
> There is no make active in the menu.lst for any of the entries for Ubuntu only the Windows XP entry.Okay, I forgot about that, that's normal. I think you still need at least one partition set active though if I remember correctly. In any case it is normal to have one boot flag on a hard disk's partition table, so we should try to add one just to make sure.

---

### Post by torgrot on 2007-03-09
First, yes the drive is jumpered for cable select.

grub> find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> makeactive

george@Ralph:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2568    20627428+  83  Linux
/dev/hda2            2569       19187   133492117+  83  Linux
/dev/hda3           19188       19457     2168775   82  Linux swap / Solaris

I rebooted several times and it worked fine.  I booted off the GAG disk and deleted the entry for the first partition with a ext3 file system and then added it back.  Which I thought I had just added GRUB to that partition.  Selected that entry and the computer rebooted.  I will try to use GAG to boot the first drive and not the partition.  I will then need to reconnect the Windows drive.

torgrot

---

### Post by torgrot on 2007-03-10
This is the results of my testing:
First with only the Ubuntu drive on the primary master Cable Select jumper.
I commented out the Windows entry from menu.lst
I can boot about 60% of the time from the GRUB menu.  The odds of successfully booting are decreased to near zero if I press enter before the time out.  If I press any key and wait or wait for the time out to expire the odds of booting Ubuntu increase probably to around 75%.  If I boot off the GAG floppy, and select the Ubuntu drive then it is probably a little higher than if I don't.  Again if I let it time out or press any key other than enter, the odds increase significantly that it will boot.

Now with the Windows drive connected as primary slave Cable Select jumper for both drives.  I left the Windows entry commented out.  The results were virtually identical as for those with only the Ubuntu drive in the system.
Next I uncommented the Windows entry in menu.lst
No change for Ubuntu with or without GAG.  Windows boots every time from the GRUB menu, I don't have to wait, I can hit enter and it boots.  I have set up GRUB to boot to the savedefault currently to speed the testing.

Here is the current menu.lst
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
default		saved

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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


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
# kopt=root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

Here is the device.map from /boot/grub
(hd0)	/dev/hda
(hd1)	/dev/hdb

Here is the output from fdisk -l
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2568    20627428+  83  Linux
/dev/hda2            2569       19187   133492117+  83  Linux
/dev/hda3           19188       19457     2168775   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/hdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/hdb5           16710       19457    22073278+   7  HPFS/NTFS

And finally here is fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=96c0669f-990c-4ad1-8a5b-65224e9efb74 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=A824A2E924A2BA28 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=1A80FA2580FA0753 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=a04a1b95-1d5b-4204-8487-5506dd0f36c8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

torgrot

---

### Post by Herman on 2007-03-10
So Windows boots okay for you with Grub or GAG now, but Ubuntu is still not booting very well with either Grub or GAG.
Hmmm :confused:

I don't see any problems with the menu.lst file.

How about trying a file system check from a LiveCD and see if that helps any?
```
sudo e2fsck -C0 -p -f -v /dev/hda1
```
Also it's interesting about your enter key making any difference to booting. I wonder if it would make any difference if you tried with a different keyboard or if there might be something in your BIOS to do with the away it handles all keyboards that Grub and GAG are having a problem with?

---

### Post by confused57 on 2007-03-10
Hi torgrot,
   I've been following your thread, especially since I also have a 4550.  It's my understanding that you have been successfully dualbooting Ubuntu & Windows on your pc for a period of time, and the booting problems just surfaced recently.  I'm no expert by any means when it comes to computer hardware(or software, for that matter), but I was wondering, if you have the means to do so, is trying a different IDE cable or a different keyboard, possibly.  You've probably thought of this, it's not rocket science; but I was just doing a little brainstorming(wasn't much of a storm) and thought I'd throw in a couple more cents of advice, for what it's worth.  You definitely have a couple of knowledgable & experienced people helping you, I'm not including myself here, and hope you can find a solution...good luck.

---

### Post by torgrot on 2007-03-10
I will try checking the disk from a LiveCD.  I probably have another keyboard and IDE cable here to try.  I am currently using both of the originals that came with the computer.  I don't think I have had the case open this much since I bought the computer.  I could understand problems if I had some bleeding edge piece of technology but this box is several years old.  This would make much more sense if GRUB and GAG didn't boot windows every time now.  GAG just boots using GRUB in the partition instead of the MBR, I am inclined to believe that there is something amiss in the later stages of GRUB or the handoff to Ubuntu.  But as I said I will try all three suggestions.

torgrot:confused:

---

### Post by torgrot on 2007-03-10
> **Herman said:**
> So Windows boots okay for you with Grub or GAG now, but Ubuntu is still not booting very well with either Grub or GAG.
Hmmm :confused:

I don't see any problems with the menu.lst file.

How about trying a file system check from a LiveCD and see if that helps any?
```
sudo e2fsck -C0 -p -f -v /dev/hda1
```
Also it's interesting about your enter key making any difference to booting. I wonder if it would make any difference if you tried with a different keyboard or if there might be something in your BIOS to do with the away it handles all keyboards that Grub and GAG are having a problem with?

Here is the results of e2fsck
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/hda1
/dev/hda1: Superblock last write time is in the future.  FIXED.
                                                                               
  118336 inodes used (4%)
     761 non-contiguous inodes (0.6%)
         # of inodes with ind/dind/tind blocks: 4475/49/0
  676835 blocks used (13%)
       0 bad blocks
       0 large files

   89198 regular files
   15692 directories
     132 character device files
      43 block device files
       2 fifos
     358 links
   13258 symbolic links (12359 fast symbolic links)
       2 sockets
--------
  118685 files

I don't really know how to interpret that, but from my untrained eye nothing looks amiss.

I don't know if I will have the time today to follow up on the keyboard and IDE cable.  

torgrot

---

### Post by Herman on 2007-03-10
> GAG just boots using GRUB in the partition instead of the MBR, I am inclined to believe that there is something amiss in the later stages of GRUB or the handoff to Ubuntu Yes, one of the reasons why a filesystem check can sometimes help. Your filesystem check output looks okay to me.

If you like, you could try installing Lilo to your Ubuntu bootsector as I explained and gave links for in an earlier post. If Lilo works well that would tend to confirm that you have found a grub problem or a fault in your particular grub installation.
If Lilo doesn't work either then it's back to looking for what is different about your hardware.
You don't have to keep Lilo, just try it out for testing purposes and if you don't like it, get rid of it later. It was your decision to install grub to your first sector, remember. GAG will boot grub or Lilo just as well.

I have seen instances where  a user has had faulty and misconfigured or corrupt grub files and deleting all the files in grub and then re-installing grub cleared up the issue. Other times a filesystem check was all that was needed.

Thank you for your on-going patience, you are very good to keep on co-operating so well like this. I'm sorry I can't tell you exactly what the problem is and how to fix it right away, but this is the first time I have heard of this particular problem.
It would be really nice to be able to find out what exactly it is and fix it.

Regards, Herman :)

---

### Post by torgrot on 2007-03-10
I followed your instructions to install LILO.  I then used the GAG boot floppy and configured it to boot using LILO.  The first reboot was fine.  Subsequent reboots were not.  Though the messages were flying fast and furious, I believe the last one before it rebooted was about acpi or something similar to that and then it rebooted.  Each time it got to the same point and then would reboot.  

As I recall there was something I could add to menu.lst to in effect turn off loading apci but I don't recall it now.  There was a problem with some computers with Dapper when they loaded it going to sleep and not being able to be brought out of hibernation.  I guess I need to start searching some older entries in the forum.

torgrot

---

### Post by Herman on 2007-03-11
Hello torgrot,
Well here's what I have in my Grub Page about setting kernel options in Grub, [kopt= (kernel options)]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")
If you only want to test kernel parameters for one boot-up when you are using Grub, you can just edit the kernel line by pressing 'e' from the Grub Menu, and then when you are ready, press 'b' to boot.
Take a look through the subsquent links at the bottom of that ...-oh, on second thought here they are, it's no effort for me to just paste them here as well,
[**10 boot time parameters** you should know about the Linux kernel **...**]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/03/10-boot-time-parameters-you-should.php")
                                 [**5.2**. **Boot Parameters**]("http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html")
                                 **[[B]The Linux BootPrompt-HowTo**]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html")
                                 [/B][**Cheat Codes** - **Knoppix Documentation Wiki**]("http://www.knoppix.net/wiki/Cheat_Codes")
                                 [**Kernel-parameters-2.6.11** - **Knoppix Documentation** Wiki]("http://www.knoppix.net/wiki/Kernel-parameters-2.6.11")

As far as Lilo goes, I think it probably takes the same parameters but I'm not very experienced with LiLo, so I'm not certain.

---

### Post by torgrot on 2007-03-11
Herman,

I had already found the linux kernel parameters page.  I tried various suggestions I found in the forums and they either didn't fix the problem or caused other problems.  The parameter that so far seems to work the most reliably is apci=ht  With that parameter added to the kernel line in menu.lst the system has booted from a complete shutdown and rebooted several times, all of them successful.

I really don't understand what what that parameter does.  I made a duplicate entry for Ubuntu and added the parameters to it one at a time and booting and rebooting until I found one that seemed to work the best.  I hope there aren't any unseen consequences from this.  Do you know anyone with knowledge of this particular parameter to the kernel?

Now I understand I can add that as a default parameter to the menu.lst and I will do so shortly.

Thanks for all your help tracking down this problem with me.  I really do appreciate the time you took.

torgrot

---

### Post by Herman on 2007-03-11
torgrot,
Hey, great! You solved it! :) Well done!
>  Now I understand I can add that as a default parameter to the menu.lst and I will do so shortly. Yes, you would want to add your new kernel parameters to your [regular booting entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries") in your menu.lst file to make it 'permanent'. 
And then to make it really permanent you would also want to edit further up in that file in [kopt=]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt") (kernel options) in order to make the change repeatable even when a new kernel is installed and the menu.lst gets automagically updated.
> I really don't understand what what that parameter does. I made a duplicate entry for Ubuntu and added the parameters to it one at a time and booting and rebooting until I found one that seemed to work the best. I hope there aren't any unseen consequences from this. Do you know anyone with knowledge of this particular parameter to the kernel?No, unfortunately I'm not experienced with kernel parameters as I have never needed to use them myself. All I can suggest is googling it, I'll do so too and see if I can turn up anything interesting about apci=ht and if I find anything I'll let you know.
>  Thanks for all your help tracking down this problem with me.  I really do appreciate the time you took.Allright, no problem, this has been a very interesting thread and I've learned a few things that might help me do better next time.
I'm really pleased that you have solved your problem too, that's the best part. 

Regards, Herman :)

---

### Post by confused57 on 2007-03-11
> **torgrot said:**
> Herman,

I had already found the linux kernel parameters page.  I tried various suggestions I found in the forums and they either didn't fix the problem or caused other problems.  The parameter that so far seems to work the most reliably is apci=ht  With that parameter added to the kernel line in menu.lst the system has booted from a complete shutdown and rebooted several times, all of them successful.

I really don't understand what what that parameter does.  I made a duplicate entry for Ubuntu and added the parameters to it one at a time and booting and rebooting until I found one that seemed to work the best.  I hope there aren't any unseen consequences from this.  Do you know anyone with knowledge of this particular parameter to the kernel?

Now I understand I can add that as a default parameter to the menu.lst and I will do so shortly.

Thanks for all your help tracking down this problem with me.  I really do appreciate the time you took.

torgrot
Excellent information & great job...I'm filing this for future reference, I might see the same problems on my Dell, if I upgraded to Edgy...I'll need to upgrade eventually when Dapper LTS is no longer supported & this may come in handy.  Adding a kernel boot parameter never occurred to me, I've never had to use one, except to boot the Sabayon live cd to correct a monitor out of range error.
  
You definitely had the right person helping you with Herman...he's helped me many times either in the forum or by my searching through his website for a solution.

---

### Post by dannyboy79 on 2007-03-12
> **torgrot said:**
> Ubuntu depends on IMHO a shakey at best, boot loader called GRUB. An excellent operating system is hampered by a poor implementation of its boot loadertorgrot

would like to change or retract your statements about grub now?

---

### Post by torgrot on 2007-03-12
Not particularly. all one has to do is look at the number of posts in this forum about GRUB and GRUB related problems.  It has to be close to the top in the number of problems here.  So if I were to suggest anything to the developers who want to bring Linux to the desktop, it would be spend a lot more time on the boot loader because if you can't boot it, all the eye candy in the world ain't gonna interest the masses.

torgrot

---

### Post by dannyboy79 on 2007-03-12
> **torgrot said:**
> Not particularly. all one has to do is look at the number of posts in this forum about GRUB and GRUB related problems.  It has to be close to the top in the number of problems here.  So if I were to suggest anything to the developers who want to bring Linux to the desktop, it would be spend a lot more time on the boot loader because if you can't boot it, all the eye candy in the world ain't gonna interest the masses.

torgrot

wow, it's just amazing after your ordeal that you still say such a thing. Everyone's problem is the fact that they don't LEARN about the software they're trying to use, they just try to use it based on a fellow inexperienced users who think they know how to use it when in fact there are multiple scenarios of dual-booting, tri-booting, etc etc that there is no way an inexperienced user can say to someone else, hey, this is how I got mine to work because it may not be the same setup despite them thinking so. BOTTOM LINE: before making irrational statements learn about the program COMPLETELY, EXPERIENCE IT KNOWLEDGABLY, then you can comment on it's ability to be a great boot loader.

Torgot, you think grub is a downfall for ubuntu and that way to many people have issues with it, I guess will just have to see with this Poll. [http://www.ubuntuforums.org/showthread.php?t=382560](http://www.ubuntuforums.org/showthread.php?t=382560)

---

