---
title: "[SOLVED] gutsy/ questions for successful boot from external drive"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by rosetown on 2007-11-04
I'm totally green and 61 years old:confused: - 1st computer was a Commodore Pet with 32K ram and a cassette drive. I'm old and my brain is fried so I am now guided by my nose. I'm not familiar with the terminal or any the CLI commands - will explored that after installation if at all possible. 

I have downloaded gutsy and committed the .iso to cd.
   did the appropriate checksums and verified the integrity of the cd.
      booted the live CD and explored. sound, wireless,screen display, and all the peripherals are working well. I'm impressed.

Many posters appear to have had immediate success installing to an external usb hard drive.

I have Windows XP on the internal drive and wish to install gusty on the external.  The external drive will be completely devoted to gusty, with grub installed as well.

My bios is Phoenix, and lists the external drive in the boot menu.
    I want the following boot priority:
      USB external hard drive for gusty
      Internal hard drive for XP

Question for those who have had a hassle free installation, or those who just know,  of a similar set-up.

   Did you unmount the external hot-linked drive as alluded to in other threads, many of which started        
   prior to the release of Gutsy, and may or may not apply only to previous releases,
      or,  did you proceed directly to installation and subsequent partioning?


Laptop Toshiba satellite M70 / 1.5 gig / 256M shared with ATI Express 200M / 80Gig / 250gig USB external hard drive

---

### Post by Pumalite on 2007-11-04
I've never done it, but I have a link that might be useful:

[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)

---

### Post by rosetown on 2007-11-04
> **Pumalite said:**
> I've never done it, but I have a link that might be useful:

[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)

Thank you Pumalite for the link and your help - I've previously read that that thread and perhaps I'm being paranoid, but my major concern is,  whether or not,  to unmount the external drive after the live cd has been loaded, as alluded to in other threads, some of which go back to 2006.  If I have to unmount the external USB drive and follow the instructions,  posted in old threads, that may be irrelevant  to 7.10,    then I'm relegated to the terminal and a great deal of effort.

The thrust of my posting is to try to differentiate between postings that dealt with installations prior to the release of gutsy and those that deal with gusty only.   Many recent posts dealing with this issue have been posted in threads that are almost as old as me:).   It is very confusing.

---

### Post by Pumalite on 2007-11-05
Here are some other links that might interest you:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by rosetown on 2007-11-05
> **Pumalite said:**
> Here are some other links that might interest you:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Thanks for the links Pumalite - I am still doing a lot of reading, planning and digesting and then repeating that process over and over.  At some point in time I'll take the plunge but judging from your byline I had better do it soon before it's too late.:)   Regards Rosetown

---

### Post by bijanafx on 2007-11-06
yes, you must unmount the file system before going through with the install.

when i forgot to unmount, the gutsy install would stall at 15%. canceled and unmounted and it worked perfectly...

---

### Post by rosetown on 2007-11-11
I am close to installing 7.10 Gusty

After viewing:
 [http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive)  
   post #2
   and
  [http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive)
   post #3
I think the following will work.

Procedure:
   boot live cd
     when boot complete
	turn on external USB drive
	  right click on external drive icon on desktop and select unmount

   right click the install icon on desktop and select open
     follow the steps
	at the completion of step 4 I have the following (number of MB's more or less but close):
	   /dev/sda
	      /dev/sda1  ext3   /             10240 MB        unknown
	      /dev/sda2  swap                  1024 MB        unknown
	      /dev/sda3  ext3   /home   238792 MB      unknown
     follow the steps
	at step 7 select advanced
	   shows (hd0)
	      change to (/dev/sda)
		select finish

Is there something else that I need to do?
I there something in the plan that you find troubling?

---

### Post by bijanafx on 2007-11-11
that should work but keep in mind that you will not be able to boot -- even to xp -- unless your external is plugged into that computer.

---

### Post by rosetown on 2007-11-11
> **bijanafx said:**
> that should work but keep in mind that you will not be able to boot -- even to xp -- unless your external is plugged into that computer.

Thanks bijanafx for your input.

at boot in the bios and if
I select F2 and if it is set to boot from external first then the internal
or if
at boot in the bios
I select F12 and then select boot for the external
won't it boot into Ubuntu?
All the above assumes that the USB external drive is turned on.

With the external drive turned off
If I select F12  and select it to boot from the internal will it not boot XP and if not, then why not?

---

### Post by rosetown on 2007-11-13
After further reading of various threads regarding partitioning and particularly those posted by Bulldog,  I am now considering creating 4 partitions.
2 root partitions (10GB each), one swap 1GB, and one /home for the remaining free space.

The 1st / partition would be for Gutsy and the 2nd / partition for next release of Ubuntu. That way if for some reason another version of Ubuntu fails on my system, I would still have a stable installation to fall back on.

Is it even possible to have an unused root partition reserved for future use?

The above aside, I'm still not clear, in the live cd install, when at page 7, I choose advanced, whether to go with the default (hd0) or change it to (hd1) or as suggested in some other threads to (/dev/sda)


Thanks in advance

---

### Post by rosetown on 2007-11-13
no - one ?

---

### Post by rosetown on 2007-11-13
I am now running Gutsy from the live cd environment and am posting from there. In the install, I tried to create 2 / (root) partitions, a swap, and a /home. Gutsy didn't like it and told me that I couldn't have 2 / mount points or something to that effect.  So I quit the install and am back to the drawing board.

I think I'm talking to myself:)

---

### Post by BCRailrodder on 2007-11-14
Just a thought (you know what that is worth :) ) - nowhere does it say that you have to assign a mount point for a partition.  I have one machine that has an empty partition that will probably have the next Ubuntu incarnation installed in it.  Grub should then be able to see my XP, 6.10 and 8.xx partitions and allow me to choose which I want at boot up.

Good luck.

---

### Post by rosetown on 2007-11-14
> **BCRailrodder said:**
> Just a thought (you know what that is worth :) ) - nowhere does it say that you have to assign a mount point for a partition.  I have one machine that has an empty partition that will probably have the next Ubuntu incarnation installed in it.  Grub should then be able to see my XP, 6.10 and 8.xx partitions and allow me to choose which I want at boot up.

Good luck.

thanks BCRailrodder - I'll test your suggestion using the live cd - to see if it's more than "just a thought":)

The other question that remains unanswered, while doing a clean install to an external USB drive, when at page 7 in the live cd install, I choose advanced, whether to go with the default (hd0), or change it to (hd1), or, as suggested in some other threads change it to (/dev/sda)?  I definitely want the boot on the external.  Anyone?

---

### Post by BCRailrodder on 2007-11-14
> **rosetown said:**
> thanks BCRailrodder - I'll test your suggestion using the live cd - to see if it's more than "just a thought":)

The other question that remains unanswered, while doing a clean install to an external USB drive, when at page 7 in the live cd install, I choose advanced, whether to go with the default (hd0), or change it to (hd1), or, as suggested in some other threads change it to (/dev/sda)?  I definitely want the boot on the external.  Anyone?

Again just a thought..  once you install the system on the external drive, you would have to configure GRUB to install on the first drive in the system (probably the MS drive) so it will be able to redirect the bios to boot from the external (take it for what it's worth - I'm pretty new myself).  

As to which drive it is - could you boot the live CD (with the external drive plugged in) and in a terminal, run the fstab command others have listed here?  That should tell you what drive to list it as in the advanced section.  I "believe" that if you use hd0, you would end up overwriting your MS installation.

Hopefully, someone else will correct me if I am wrong.

Kent

---

### Post by rosetown on 2007-11-14
> **BCRailrodder said:**
> Again just a thought..  once you install the system on the external drive, you would have to configure GRUB to install on the first drive in the system (probably the MS drive) so it will be able to redirect the bios to boot from the external (take it for what it's worth - I'm pretty new myself).  
I don't want to write to the 1st drive at all!
 
> **BCRailrodder said:**
> As to which drive it is - could you boot the live CD (with the external drive plugged in) and in a terminal, run the fstab command others have listed here?  That should tell you what drive to list it as in the advanced section.  I "believe" that if you use hd0, you would end up overwriting your MS installation.
and I don't want to do that. maybe will try (hd1). but first will attempt some commands in the terminal from the live cd.

Sounds like the blind leading the blind:)  Thanks for your concern.

---

### Post by meierfra on 2007-11-14
My suggestion:

1) Change your boot order so that the external drive is first.

2) Unplug the internal drive while installing Ubuntu. (that way  ubuntu will have no chance to mix up the drives and you won´t  have the use the advanced button.

3) Do NOT choose two ¨/ partitions¨. That will screw up your system. Just leave the spare partition unmounted. Or you can format it to ext3, mount it somewhere and use it for extra storage.


If you do it this way, you will automatically boot to Ubuntu if the external drive is plugged in, otherwise to windows.

(the only disadvantage:  You won´t be able to boot to windows when the external drives id plugged in. But that can be easily fixed.)

If you are uncomfortably with 2) let me know, and I give you (slightly more complicated) instructions which do not involve unplugging the internal drive.

---

### Post by rosetown on 2007-11-14
I am posting from the live CD and have not yet installed Gutsy to my 250GB USB external.

 sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96ba9a05

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9703    77939316    7  HPFS/NTFS
/dev/hda4            9704        9729      208845   88  Linux plaintext

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe768db1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

I don't know how to interpet the above.

---

### Post by meierfra on 2007-11-14
It says that you have two hard drives. Ubuntu calls  them hda and sda.

hda is a 80GB drive with two partitions: hda1 and hda4.  hda1 is  formated as NTFS (that is the file format  Windows uses) hd4 is a Linux partition.


sda  is a 250 GB drive with just one partition sda1 formated as NTFS

And from what you told us, hda is the internal drive and sda the external drive. That means that you should install Grub to /dev/sda (But with my method from my previous post  you won´t have to worry about that)

---

### Post by rosetown on 2007-11-14
> **meierfra said:**
> It says that you have two hard drives. Ubuntu calls  them hda and sda.

hda is a 80GB drive with two partitions: hda1 and hda4.  hda1 is  formated as NTFS (that is the file format  Windows uses) hd4 is a Linux partition.


sda  is a 250 GB drive with just one partition sda1 formated as NTFS

And from what you told us, hda is the internal drive and sda the external drive. That means that you should install Grub to /dev/sda (But with my method from my previous post  you won´t have to worry about that)

Thanks for you attention.  I hadn't seen your 1st post to this thread prior to my last post.

Yes, I am very uncomfortable unplugging the internal drive.  Odd that fdisk -l shows hda4 as a Linux partition. When testing partitioning in ubiquity it shows as a windows partition, and I have never installed any flavour of Linux intentionally or accidentally.

The above aside, I'm eager to hear from you regarding the second method.

Regards Duane - still posting from the live cd.

---

### Post by meierfra on 2007-11-15
Actually reading through your posts one more time, you do  seemed to have it nailed down by now.

But as a said in my previous  posts, don´t choose two ¨/ partition¨, at step 7 change (hd0) to /dev/sda and when you reboot  set the boot order so that you always boot from the external drive first. 

And in the event that something  goes wrong, just come back here and I´m sure it can be sorted out.

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> Actually reading through your posts one more time, you do  seemed to have it nailed down by now.

But as a said in my previous  posts, don´t choose two ¨/ partition¨, at step 7 change (hd0) to /dev/sda and when you reboot  set the boot order so that you always boot from the external drive first. 

And in the event that something  goes wrong, just come back here and I´m sure it can be sorted out.

Great, at step 7 I select advanced and change (hd0) to /dev/sda . Do you know if it should it be surrounded by parentheses like this (/dev/sda) or not.

With regards to partitions, I still don't know how create a 4th partition (reserved for the Hardy Heron) release. I tried a coulple of things but managed to crash ubiquity (the installer).

Regards Duane

---

### Post by meierfra on 2007-11-15
It´s /dev/sda.   I don´t  know what the problem with your fourth partition is. One option is to download the ¨gparted live CD¨. It usually does a better job, than the Partitioner on the Ubuntu Live CD. The other option is do just forget about the fourth partition for now. I change my partitions frequently and never had any problems. (Although it is safer to do it now)

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> It´s /dev/sda.   I don´t  know what the problem with your fourth partition is. One option is to download the ¨gparted live CD¨. It usually does a better job, than the Partitioner on the Ubuntu Live CD. The other option is do just forget about the fourth partition for now. I change my partitions frequently and never had any problems. (Although it is safer to do it now)

Fair enough, I suppose, I could create it as an ext3 with a mount point named /backup or something and in the future change it to accommodate the Hardy release. That's 6 months from now and my experience with Ubuntu should be much improved.  Your thoughts?

---

### Post by meierfra on 2007-11-15
> Fair enough, I suppose, I could create it as an ext3 with a mount point named /backup or something and in the future change it to accommodate the Hardy release. That's 6 months from now and my experience with Ubuntu should be much improved. Your thoughts?

Sounds good.  I´m going to bed now, but l´ll  check in tomorrow to see whether you got Gutsy installed.

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> Sounds good.  I´m going to bed now, but l´ll  check in tomorrow to see whether got Gutsy installed.
On my 3rd glass of wine and I will leave the install for tomorrow, bedtime soon.  Once again thanks for the hand holding - much appreciated.

Assuming everything goes according to plan, my responsibility now,:) as my final post, I will recapture step by step for the benefit of others and mark the thread as solved.

Good night
Duane

---

### Post by rosetown on 2007-11-15
:( I installed gutsy to my external USB drive but I can't boot. It returns:

Error 17: Cannot mount selected partition
Press any key to continue.

I can boot into Windows - am now officially lost:)

---

### Post by meierfra on 2007-11-15
boot from the live cd  and post the output of

sudo fdisk -l

---

### Post by GeorgiaBoot on 2007-11-15
I just did this and it worked perfect.


1)Re-format whole drive

2)Change Bios Boot Priority to~

CD
USB
HardDrive

3)Shut down Computer and disconnect all internal hard drives

4)Connect USB Drive

5)Insert Live CD

6)Once in the desktop go to System>Preferences>Removable Drives and Media

7)Deselect
*Mount Removable Drives when hot plugged
*Mount Removable Media when inserted
*Browse Removable media when inserted

8)Close window

9)Select install Ubuntu on Desktop 

10) When it asks about HD select Use entire HD Disc

11)Run installation

12)Restart


This is very easy to do. When you want to go back to windows just shutdown normally with Ubuntu, turn off HD then Turn on Computer and you are back in windows. 

Hope this helps

---

### Post by meierfra on 2007-11-15
You can also  try this in  terminal: 

sudo grub

this will give you a "grub>" prompt.

Type 

find /boot/grub/menu.lst

This will return something of the form

(hdx,y)  (probably (hd1,0)

type 

root (hdx,y)

setup (hdx)

quit

Reboot and see what happens.
Just for trouble shooting: Before typing "quit" copy the the contents of the terminal and post it here.

---

### Post by GeorgiaBoot on 2007-11-15
A big problem I have read is people don't disconnect there internal Hard Drives and that somehow messes up the installation process. If you can just now format the external HD and start over I suggest you do that. If you are now having windows boot problems then you have gone into a little deeper water.

---

### Post by meierfra on 2007-11-15
No need to reinstall yet. Disconnecting the internal hard drive avoids the problems you are having. But it shouldn't be too difficult fix.

---

### Post by rosetown on 2007-11-15
sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96ba9a05

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9703    77939316    7  HPFS/NTFS
/dev/hda4            9704        9729      208845   88  Linux plaintext

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe768db1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        1369      996030   82  Linux swap / Solaris
/dev/sda3            1370        2614    10000462+  83  Linux
/dev/sda4            2615       30401   223199077+  83  Linux

---

### Post by meierfra on 2007-11-15
fdisk looks fine.


You can try reinstalling grub as I suggested in post #30. There is some chance that you also have to edit the file "menu.lst"  So I would like to see that file:
 

```

mkdir gutsy
sudo mount -t ext3 /dev/sda1  gutsy

```
This lets you access the ubuntu partition from the LiveCD

```
 gksudo gedit gutsy/boot/grub/menu.lst 
```

This opens a window with the file "menu.lst". Copy the whole file and post it here.

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> You can also  try this in  terminal: 

sudo grub

this will give you a "grub>" prompt.

Type 

find /boot/grub/menu.lst

This will return something of the form

(hdx,y)  (probably (hd1,0)

type 

root (hdx,y)

setup (hdx)

quit

Reboot and see what happens.
Just for trouble shooting: Before typing "quit" copy the the contents of the terminal and post it here.

grub> find /boot/grub/menu.lst
 (hd1,0)

grub> root (hdx,y)

Error 23: Error while parsing number

grub> root (hdx,y)

Error 23: Error while parsing number

grub> setup (hdx)

Error 23: Error while parsing number

---

### Post by meierfra on 2007-11-15
Sorry, I should have said so. You need to replace x and y by the actual values returned by find. So do this:


```
sudo grub
root (hd1,0)
setup (hd1)
quit

```

Don't reboot right away. Let me have a look at menu.lst first. (see my previous post)

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> fdisk looks fine.


You can try reinstalling grub as I suggested in post #30. There is some chance that you also have to edit the file "menu.lst"  So I would like to see that file:
 

```

mkdir gutsy
sudo mount -t ext3 /dev/sda1  gutsy

```
This lets you access the ubuntu partition from the LiveCD

```
 gksudo gedit gutsy/boot/grub/menu.lst 
```

This opens a window with the file "menu.lst". Copy the whole file and post it here.

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
# kopt=root=UUID=77d1607f-8473-41d7-aacd-c4082c88c365 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=77d1607f-8473-41d7-aacd-c4082c88c365 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=77d1607f-8473-41d7-aacd-c4082c88c365 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by GeorgiaBoot on 2007-11-15
I really suggest you don't have your internal Hard Drives connected when installing. I also think it would be far easier if you just started over, do a Clean install. Should only take about 30minutes.

---

### Post by meierfra on 2007-11-15
Ok. You need to edit menu.lst (but after that you should  be all set)

Open "menu.lst" as before. Edit the file as follows:

1) Change all (hd1,0)  to (hd0,0)

(There will be four: Once "#groot (hd1,0)" and three times "root (hd1,0)"

2) Change 

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
chainloader +1

to 

title Microsoft Windows XP Home Edition
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1


Save the file. If you didn't do it yet, reinstall grub according to my previous post. Cross your fingers and reboot.

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> Sorry, I should have said so. You need to replace x and y by the actual values returned by find. So do this:


```
sudo grub
root (hd1,0)
setup (hd1)
quit

```

Don't reboot right away. Let me have a look at menu.lst first. (see my previous post)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by rosetown on 2007-11-15
The menu.lst was posted prior to my changes in post 40

---

### Post by meierfra on 2007-11-15
Post #40 looks like it should. Also the  changes in post #40 did not effect menu.lst.  So just edit menu.lst according to my previous post.

---

### Post by rosetown on 2007-11-15
> **meierfra said:**
> 
Save the file. If you didn't do it yet, reinstall grub according to my previous post. Cross your fingers and reboot.

I've made all the changes to menu.lst and I reinstalled grub. To save menu.lst do I just select the save icon at the top of the screen? Man, am I sweating:)

---

### Post by meierfra on 2007-11-15
Yes.

---

### Post by rosetown on 2007-11-15
Hey meierfra Voila a miracle!!!

Well here I am in ubuntu booting from my external USB hardrive.  Windows works as well. Still have to test my peripherals. But I'm here and I can't thank you enough!!!  A few bumps - my Firefox bookmarks that I asked to be imported are not showing. There probably on the hard drive somewhere.  But the big hurdle is over and I couldn't be happier:KS

---

### Post by rosetown on 2007-11-15
Oh and I forgot to thank GeorgiaBoot as well for taking a major interest in my plight and who posted reasonable solutions.  Sorry that I didn't acknowledge your posts, I was in the thick of it and my plate was full.:KS

And to everyone else who posted when I felt like I was talking to myself - many thanks

---

### Post by meierfra on 2007-11-15
> I can't thank you enough!!! 

You are welcome. Glad to be of help.

---

### Post by rosetown on 2007-11-16
Before I mark this thread as solved, and for the benefit of others, I would like to review what I did:

1 In the bios I selected the CD rom to boot first and saved.
2) booted in windows with the external USB turned on
3) and to ensure that the USB drive was unmounted, I left clicked on the external icon on the bottom right side and selected safely turn off hardware or something to that effect, and then turned of the USB drive, and then inserted the live cd and then turned off the computer. 
4) Turned the computer on which booted the live CD
5) right clicked on the external Usb icon on the desktop and selected unmount
6) went through the install to page 7 and selected advance and change (hd0) to /dev/sda
6) selected finish or did it read install  (I don't remember)
7) the install completed and I selected reboot.
8) On reboot I selected F2 in the bios and moved the USB drive to the first place in the boot order
9) on the reboot I got error 17 and if you followed this thread you know the story

what I did not do as suggested in various threads: (possibly critical)

Once in the live CD environment

I did not select System>Preferences>Removable Drives and Media Preferences and de-select  the following:
1) Mount removable drives when hot plugged
2) Mount removable media when inserted
3) Browse removable media inserted

I suspect the above omission was  a key to a successful conclusion - but I don't know for sure because I am a noob.

Nonetheless, with the help of meierfra I was able to rectify the ensuing problems.

How is my system behaving:

1) A cold boot with the external turned on boots to windows
2) A cold boot with the external turned off boots to windows
3) A cold boot with the external turned on and by selecting F12 in the Bios boots to Ubuntu
4) F2 which sets the boot priority is not persistent. Even though the external drive is set to the first priority and saved, and then I boot to windows with the external turned off, the external, not being recognized by the bios as on, gets dropped to the bottom in the bios boot priorty list. (I hope I am clear)

Otherwise, my peripherals, printer, camera, usb drive are all working well.
My sound quality is the same as in Windows.
My wireless works like a charm
Cannot seem to tweak my touchpad - acceleration problem

Before I mark this as being solved if some experts would like to make some observations about what I did right and what I did wrong please do so now.  Tomorrow evening I will mark this as solved

---

### Post by meierfra on 2007-11-18
> 
and what I did wrong

Nothing.  The cause of your problem was this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497")

and the only way to avoid it, is to unplug the internal drive. But even if you unplug the internal hard drive, you still would have to edit "menu.lst"  afterwards to add "windows" to the grub menu. (And I  bet if you would have tried to unplug the hard drive you would have been  sweating just as much as you were when editing "menu.lst")

---

### Post by rosetown on 2007-11-18
> **meierfra said:**
>  (And I  bet if you would have tried to unplug the hard drive you would have been  sweating just as much as you were when editing "menu.lst")

Your are so right:)

Regards Duane

---

