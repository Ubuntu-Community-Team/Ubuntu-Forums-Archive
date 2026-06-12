---
title: "Tryed to dual boot linux and XP but XP wont load back up!"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Tooplex on 2007-11-11
Please help me i tryed to install linux ubuntu and it worked perfectly (using it right now) Ubuntu runs perfectly but XP wont load up at all it hasent been formated i know that i can see it and it appears in GRUB but when i select XP it doesnt want boot it just shows a black screen how can i have it boot xp again please (No formatting please)

And if worse comes to worse is there a way to get rid of linux and grub and only boot up xp again please Thanks.

---

### Post by jordanmthomas on 2007-11-11
In Ubuntu, open up a terminal (applications --> accessories --> terminal) and type this in it
```
sudo fdisk -l
```
you'll have to put in your password, and then hit enter.

Copy / paste that into the forum here.

Also, post the output of this command
```
cat /boot/grub/menu.lst
```
and we'll see what we can do.


For the case that "worse comes to worse" you can boot off your Windows install CD, go to the recovery console and type ```
FIXMBR
``` to remove grub.

**edit** Make that FIXMBR

---

### Post by Pumalite on 2007-11-11
Have to edit menu.lst after backing up the file and adding an entry for Windows:
title   Windows
rootnoverify  (hd0,0) (or such)
savedefault
chainloader +1

Find out where is Windows with:
sudo fdisk -lu

---

### Post by Er1ck on 2007-11-11
How did you partition your hard drive? Did you use any software such as Norton Partition Magic?

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> In Ubuntu, open up a terminal (applications --> accessories --> terminal) and type this in it
```
sudo fdisk -l
```
you'll have to put in your password, and then hit enter.

Copy / paste that into the forum here.

Also, post the output of this command
```
cat /boot/grub/menu.lst
```
and we'll see what we can do.


For the case that "worse comes to worse" you can boot off your Windows install CD, go to the recovery console and type ```
FIXBOOT
``` to remove grub.

tooplex@Doofus:~$ sudo fdisk -l
[sudo] password for tooplex:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81258125

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5222    41937682+   f  W95 Ext'd (LBA)
/dev/sda2   *        5223       28437   186474487+   7  HPFS/NTFS
/dev/sda3           28438       30401    15775830   83  Linux
/dev/sda5               2        5222    41937651    7  HPFS/NTFS
tooplex@Doofus:~$ 


Thats for the sudo command

And this is for the grub command:

[B]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8bf03e3a-5b1b-45b0-825b-321b7992a696 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8bf03e3a-5b1b-45b0-825b-321b7992a696 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8bf03e3a-5b1b-45b0-825b-321b7992a696 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

tooplex@Doofus:~$ 

Hope it helps.

---

### Post by Tooplex on 2007-11-11
> **Pumalite said:**
> Have to edit menu.lst after backing up the file and adding an entry for Windows:
title   Windows
rootnoverify  (hd0,0) (or such)
savedefault
chainloader +1

Find out where is Windows with:
sudo fdisk -lu

I have no idea what you just said :(

---

### Post by Tooplex on 2007-11-11
> **Erick87 said:**
> How did you partition your hard drive? Did you use any software such as Norton Partition Magic?

I used GParted to make the 15gb partiton for unbuntu.

---

### Post by jordanmthomas on 2007-11-11
It looks like you have two NTFS partitions.  Perhaps Windows is installed on /dev/sda5 instead of /dev/sda2 (like Grub thinks it is)

So, try editing /boot/grub/menu.lst to use /dev/sda5 instead of /dev/sda2
```
gksudo gedit /boot/grub/menu.lst
```

Scroll to the bottom where you'll find this:
```

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```
and change it to look like this:
```
title Microsoft Windows XP Professional
rootnoverify (hd0,[COLOR="Red"]4[/COLOR])
savedefault
makeactive
chainloader +1

```

Then, see if that helps any.

---

### Post by Pumalite on 2007-11-11
> **Tooplex said:**
> I have no idea what you just said :(

Sorry, tried to help, but obviously couldn't.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> It looks like you have two NTFS partitions.  Perhaps Windows is installed on /dev/sda5 instead of /dev/sda2 (like Grub thinks it is)

So, try editing /boot/grub/menu.lst to use /dev/sda5 instead of /dev/sda2
```
gksudo gedit /boot/grub/menu.lst
```

Scroll to the bottom where you'll find this:
```

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```
and change it to look like this:
```
title Microsoft Windows XP Professional
rootnoverify (hd0,[COLOR="Red"]4[/COLOR])
savedefault
makeactive
chainloader +1

```

Then, see if that helps any.

Ok i did that and now im going to see if it has worked

---

### Post by Tooplex on 2007-11-11
> **Tooplex said:**
> Ok i did that and now im going to see if it has worked

I did that and it came up with 

Error 12 : Invalid Device Requested

Yes sda5 is used for Windows and i have sda2 as my games partition 

Any other thoughts :(

---

### Post by jordanmthomas on 2007-11-11
I don't have time to investigate it further at the moment (taking too many hours in school :) ) but it may have something to do with the extended partition you have (note you have no /dev/sda4) so maybe you can look up to see if there's anything special you need to do as far as that is concerned.

Hopefully someone else can pop in and see what's up.

---

### Post by Tooplex on 2007-11-11
Ok then forget it how can i delete Linux and make it run XP on its own please with no Grub loader please

---

### Post by jordanmthomas on 2007-11-11
While I don't think you should give up quite so easily, see my first reply in this thread.
(note that I did have FIXBOOT there, but you really need FIXMBR)

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> While I don't think you should give up quite so easily, see my first reply in this thread.
(note that I did have FIXBOOT there, but you really need FIXMBR)

Lol No the reason why i want to is to put ubuntu on my laptop (which i have already) and i want just XP on this and by the way i don't have my XP installation disk any more I kind of got it for free :/ Anyway i can delete ubuntu perfectly on this and make sure XP will load up 100%?

---

### Post by jordanmthomas on 2007-11-11
If you don't have an XP installation disk, you'll have to get a Windows 98 boot disk and use fdisk /mbr from there.  (Since it's a laptop, I'm guessing you don't have a floppy drive though)

The only way for you to guarantee Windows will start back up is to get grub working correctly at this point, unless you can come up with a Windows installation disk (that's karma for you, I suppose.  :)  )

Now, this isn't your fault at all, but your extended partition is confusing for me to read from fdisk output.  Is there any way you could post a screenshot from gparted?  It would make it easier for me (a very tired person who can't think too well right now) to see how your partitions are set up.

I'm pretty sure Windows HAS to be installed on a primary partition.

---

### Post by Thor (Hammer of God) on 2007-11-11
> **Tooplex said:**
> Lol No the reason why i want to is to put ubuntu on my laptop (which i have already) and i want just XP on this and by the way i don't have my XP installation disk any more I kind of got it for free :/ Anyway i can delete ubuntu perfectly on this and make sure XP will load up 100%?
You'll need to "borrow" someone's XP install disk then - go into recovery mode and run FIXMBR.  Alternately, you could try to boot off an XP boot floppy, and copy FDISK over to it and run FDISK /mbr to fix the master boot record.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> If you don't have an XP installation disk, you'll have to get a Windows 98 boot disk and use fdisk /mbr from there.  (Since it's a laptop, I'm guessing you don't have a floppy drive though)

The only way for you to guarantee Windows will start back up is to get grub working correctly at this point, unless you can come up with a Windows installation disk (that's karma for you, I suppose.  :)  )

Now, this isn't your fault at all, but your extended partition is confusing for me to read from fdisk output.  Is there any way you could post a screenshot from gparted?  It would make it easier for me (a very tired person who can't think too well right now) to see how your partitions are set up.

I'm pretty sure Windows HAS to be installed on a primary partition.

Ok sorry i confused you a bit but Leave the laptop out of the way now. It has nothing to do with anything now. Im talking about my computer which has ubuntu and xp installed but xp wont boot.

Where would i get a 98 boot disk from? and can someone explain what fixing this mbr would do please?

How can i post a screenie of Gparted when it runs it through a boot disk it runs the app on no OS so how would i save it its not exactly possible.

---

### Post by Tooplex on 2007-11-11
> **Thor (Hammer of God) said:**
> You'll need to "borrow" someone's XP install disk then - go into recovery mode and run FIXMBR.  Alternately, you could try to boot off an XP boot floppy, and copy FDISK over to it and run FDISK /mbr to fix the master boot record.

No body i know has xp disc T_T and where would i get a xp boot floppy? and whats the master boot record? 

Sorry about all these questions but i have no desire to kill my PC.

---

### Post by jordanmthomas on 2007-11-11
Sorry, your last post was less than coherent.  I thought you had installed Ubuntu on your laptop.  

Anyway, to create a boot disk, see this link:  [http://www.computerhope.com/boot.htm#71](http://www.computerhope.com/boot.htm#71)
You'll need a working windows installation (shouldn't be too hard to find one somewhere).

You can post a screenshot of gparted by booting off the LiveCD, taking a screenshot and saving it to your Desktop, then uploading it to the forum or to imageshack or something.

To clarify:  can you still boot Ubuntu?  If so, you can install gparted so you don't need to boot off a CD:
```
sudo apt-get install gparted
```

finally, the master boot record is what your computer looks at when it boots off your hard drive to know what OS to load (to put it very simply).
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

finally v2.0:  don't worry, your computer is not dead.  Software can't kill it off for good.  The absolute worst that will happen is data loss in the case you have to install a new OS.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> Sorry, your last post was less than coherent.  I thought you had installed Ubuntu on your laptop.  

Anyway, to create a boot disk, see this link:  [http://www.computerhope.com/boot.htm#71](http://www.computerhope.com/boot.htm#71)
You'll need a working windows installation (shouldn't be too hard to find one somewhere).

You can post a screenshot of gparted by booting off the LiveCD, taking a screenshot and saving it to your Desktop, then uploading it to the forum or to imageshack or something.

To clarify:  can you still boot Ubuntu?  If so, you can install gparted so you don't need to boot off a CD:
```
sudo apt-get install gparted
```

finally, the master boot record is what your computer looks at when it boots off your hard drive to know what OS to load (to put it very simply).
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

finally v2.0:  don't worry, your computer is not dead.  Software can't kill it off for good.  The absolute worst that will happen is data loss in the case you have to install a new OS.

This is what is displayed on gparted
[IMG]http://i109.photobucket.com/albums/n50/Tooplex/Screenshot.png[/IMG]

also i have no blank floppy disks but about 75 blank disks anyway i can do this with them?

---

### Post by jordanmthomas on 2007-11-11
OK...here is your problem (and one I admittedly do not know how to fix)
Your Windows is installed in a logical partition.  Windows will only boot from a logical partition if there is a primary partition with NTLDR (loads its kernel) on it.  

Odds are, your /dev/sda2 has NTLDR on it so it is the one that needs to be pointed to with grub (change that 4 back to a 1, basically)

If you're ever able to get a FIXMBR run, Windows will be back...no problem.
Also, I think (not 100% here) that if you manage to get a Windows CD and run FIXBOOT on it, grub will work.

> also i have no blank floppy disks but about 75 blank disks anyway i can do this with them?
what?  This confuses me.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> OK...here is your problem (and one I admittedly do not know how to fix)
Your Windows is installed in a logical partition.  Windows will only boot from a logical partition if there is a primary partition with NTLDR (loads its kernel) on it.  

Odds are, your /dev/sda2 has NTLDR on it so it is the one that needs to be pointed to with grub (change that 4 back to a 1, basically)

If you're ever able to get a FIXMBR run, Windows will be back...no problem.
Also, I think (not 100% here) that if you manage to get a Windows CD and run FIXBOOT on it, grub will work.

Hmmm ok then So all i have to do is run FIXMBR and windows XP will run from grub perfectly fine? So how can i do that with no windows disk and no blank floppy disks?

> **jordanmthomas said:**
> 
what?  This confuses me.

Lol i said that i have no blank floppy disks but i have about 75 blank Cd roms

---

### Post by jordanmthomas on 2007-11-11
Running FIXMBR:  basically takes Linux out of the picture.  Its data will still be there but you won't be able to run Ubuntu unless you reinstall Grub.  If you're able to run this Windows will boot fine as soon as you start your computer (no Grub)

Running FIXBOOT:  might fix your problems with booting XP from Grub...might not do anything at all.

I believe there is a way to create a bootable CD with fdisk on it, but my memory's failing me at the moment.  Google should help on that one.  ;)

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> Running FIXMBR:  basically takes Linux out of the picture.  Its data will still be there but you won't be able to run Ubuntu unless you reinstall Grub.  If you're able to run this Windows will boot fine as soon as you start your computer (no Grub)

Running FIXBOOT:  might fix your problems with booting XP from Grub...might not do anything at all.

I believe there is a way to create a bootable CD with fdisk on it, but my memory's failing me at the moment.  Google should help on that one.  ;)

So with FIXMBR i can run it then it will boot straight to XP without the Grub coming up right? and then i can reformat the linux drive and then re add it to the 200gb partition?

---

### Post by Tooplex on 2007-11-11
Also how can i do this with no XP setup disk?

---

### Post by jordanmthomas on 2007-11-11
> **Tooplex said:**
> So with FIXMBR i can run it then it will boot straight to XP without the Grub coming up right? and then i can reformat the linux drive and then re add it to the 200gb partition?

Yes.

> Also how can i do this with no XP setup disk?
You cannot.  You have to find one.  I don't condone piracy, but maybe one of those 75 CDs of yours is looking for a torrent?  If you catch my drift...

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> Yes.


You cannot.  You have to find one.  I don't condone piracy, but maybe one of those 75 CDs of yours is looking for a torrent?  If you catch my drift...

Maybe there might be a away for me not having to torrent it. If i get a blank floppy disk will this work perfectly?

"Windows 98 Floppy Disk Method
(Works for Windows 98 or Windows XP without an 'install' CD)
You will need a blank, formatted floppy disk.
I have used this method to restore the bootsector on both my Windows XP Home Edition computer and also my Windows 98SE computer.
Your computer may have come with a Windows XP 'Recovery Disk' instead of an 'Install' disk, or maybe you lost your Windows XP CD or have Windows 98 or some other version.
You can download a self extracting file to make your own Windows 98 boot floppy disk from Bootdisk.com.  The one I use is called 98SE OEM.
To make the boot disk, once the boot98se WinImage Self Extractor file is downloaded, place a formatted floppy in the floppy drive and then just double-click on the file. I it will make a boot floppy automatically.
A Windows 98 boot floppy will work just as well as an install CD to restore your 'boot sector'.
You must first of course have your computer's BIOS set to boot from the floppy disk drive before the hard disk in the BIOS boot sequence. See this website's BIOS Page.
 Just pop the floppy in the drive and boot your computer. You will soon see a black background in your monitor and will be given three choices.
These are,

                     1. Start computer with CD-ROM support
                     2. Start computer without CD-ROM support  
                     3. View the Help file.
  Choose number 2, 'Start computer without CD-ROM support'.

After a few minutes, you will see a prompt that looks like this,

A:\_
 After the     A:\_   prompt and type the command fdisk /mbr and wait for the command to work.

A:\ fdisk /mbr_
When it is finished, press 'Ctrl'+'Alt'+'Del' to reboot, and remove the floppy disk.
Your 'boot sector' will be pointing to Windows again."

---

### Post by jordanmthomas on 2007-11-11
Yes, it should work fine if you're able to obtain a floppy disk.
You shouldn't have to download anything for it if you just format it as an MS-DOS boot disk from windows as described somewhere earlier in the thread.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> Yes, it should work fine if you're able to obtain a floppy disk.
You shouldn't have to download anything for it if you just format it as an MS-DOS boot disk from windows as described somewhere earlier in the thread.

How would i format it from windows if i cant get into windows lol

---

### Post by jordanmthomas on 2007-11-11
You can use any windows machine.  I just assumed you had access to one somewhere.

---

### Post by Tooplex on 2007-11-11
> **jordanmthomas said:**
> You can use any windows machine.  I just assumed you had access to one somewhere.

Never though of that Lol :( Well ill do that with the floppy disk instead of spending ages downloading a 600mb file Thanks for all your help and i hope it works later on when i get one from my freind.

One last question how would i reinstall ubuntu on a computer that already has windows on it withough messing up the MBR like i did somehow?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
> **jordanmthomas said:**
> Running FIXMBR:  basically takes Linux out of the picture.  Its data will still be there but you won't be able to run Ubuntu unless you reinstall Grub.  If you're able to run this Windows will boot fine as soon as you start your computer (no Grub)

Running FIXBOOT:  might fix your problems with booting XP from Grub...might not do anything at all.

I believe there is a way to create a bootable CD with fdisk on it, but my memory's failing me at the moment.  Google should help on that one.  ;)

well you can still boot linux later you just have to set up the windows boot loader to boot linux .... i dont know how to do .... i had this very same problem yesterday :) we just reinstalled it all though lol

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
> **Tooplex said:**
> Never though of that Lol :( Well ill do that with the floppy disk instead of spending ages downloading a 600mb file Thanks for all your help and i hope it works later on when i get one from my freind.

One last question how would i reinstall ubuntu on a computer that already has windows on it withough messing up the MBR like i did somehow?

as long as you dont reformat the partiton that linux is on you should not have to reinstall it you just have to configure windows boot loader i think you can do that in side of windows :) for get how can find out though one min

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
aaa go here

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by jordanmthomas on 2007-11-11
> **<<joe>> said:**
> well you can still boot linux later you just have to set up the windows boot loader to boot linux .... i dont know how to do .... i had this very same problem yesterday :) we just reinstalled it all though lol

You can do it, but it's not as simple as setting up grub:
[http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)

---

### Post by jaybombalous on 2007-11-11
OMG, just d/l supergrub and fix the MBR in that program, U can download the supergrub rescue CD on their site then right click on the iso u downloaded and '**write to disc**'. Then boot back to cd and proceed to follow instructions on how to repair the MBR. 

:)

Do u need an addy of the supergrub website or do you think U can handle that???

---

### Post by jaybombalous on 2007-11-12
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)


make sure u read the instructions and take the time to learn something. Read this part closely...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Select_the_appropriate_Super_Grub_Menu](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Select_the_appropriate_Super_Grub_Menu)

---

### Post by jordanmthomas on 2007-11-12
Nice, I didn't know the Super Grub Disk could do the equivalent of FIXMBR / FIXBOOT (I've also never used it though).
Learn something new every day.  :)

Anyway, Tooplex, your answer lies at jaybombalous's link for sure...I saw it there.

---

### Post by Tooplex on 2007-11-12
Thanks but can you tell me what options to run exactly to make it straight boot to XP when you turn on the computer please?

---

### Post by jaybombalous on 2007-11-12
click on the second link in my post, it takes u to the part u need to READ!!!! I can't stress that enough, just read it!

---

### Post by jordanmthomas on 2007-11-12
you should really read the page instead of just asking, but here you are:
[quote=that page] I  want my MBR pointing to Windows  bootloader again  - right now!

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows
[/quote]

---

### Post by Tooplex on 2007-11-12
Thanks wish me luck

---

### Post by jaybombalous on 2007-11-12
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

then read this ^^^ part, read very well, maybe even print them out. :)

---

### Post by Tooplex on 2007-11-12
> **jordanmthomas said:**
> you should really read the page instead of just asking, but here you are:

Well i did that but the only thing there was the option Syslinux(didn't select it) and it still came up with the grub loader :( Any Help

---

### Post by jaybombalous on 2007-11-12
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_in_a_logical_partition](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_in_a_logical_partition)

for when u get back, read this.

---

### Post by jaybombalous on 2007-11-12
> **Tooplex said:**
> Well i did that but the only thing there was the option Syslinux(didn't select it) and it still came up with the grub loader :( Any Help

one option? I think u should really read the webpage and the links I provided. If u go about **** irrationally u are doomed to fail horribly.

---

### Post by Tooplex on 2007-11-12
> **jaybombalous said:**
> one option? I think u should really read the webpage and the links I provided. If u go about **** irrationally u are doomed to fail horribly.

Well i have and its helped none Need some more help here please :(

---

