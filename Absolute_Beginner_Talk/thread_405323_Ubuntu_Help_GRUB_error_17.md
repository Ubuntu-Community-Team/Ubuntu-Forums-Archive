---
title: "Ubuntu Help GRUB error 17"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by DeltaUK on 2007-04-09
Hey all,

Yesturday I downloaded Ubuntu 6.10, the boot cd worked fine, and the OS worked on from the cd.

I decided to install, these are my hard drives:

1:   hda  80GB, has windows XP
2:   hdb  160GB, has lots of stuff on it and 30GB free

So i wanted to install on F: without effected winxp or any of my files, i had to edit the partition tables manually

I resized my F: and created a new partition ext3 at 17GB this is called hdb2
then i created a subpartition of that as 256mb swap this is called hdb3

i then mounted just the root and swap

the next screen says ready to install, it also shows where the grub will be installed, as default it showed hd0. at first i left it, it installed successfully

but then my pc wouldnt boot, i got an error

GRUB Loding stage1.5

Error 17
I was able to boot up windows by using the recovery console from the xp boot disk.

But what went wrong, i know the grub installation was wrong, how do i find out where to install it? hd0 must be my drive hda, and thats not the drive i want it to go to.

Help much appreciated

Thanks

Matt

---

### Post by terdon on 2007-04-09
We need to see your /etc/fstab and  /boot/grub/menu.lst files. Check out my post at [http://ubuntuforums.org/showthread.php?t=405225](http://ubuntuforums.org/showthread.php?t=405225) to see a way of getting them.

---

### Post by DeltaUK on 2007-04-09
Well i have deleted my ubuntu partitions and also done a fixmdr to get rid of grub cuz it errored and nothing would boot.

so atm i have winxp how it was b4, no ubuntu or grub at all

And i cant reinstall ubuntu cuz i dont know how to install grub properly, it will error again then i cant get back to windows..

---

### Post by igknighted on 2007-04-09
> **DeltaUK said:**
> Well i have deleted my ubuntu partitions and also done a fixmdr to get rid of grub cuz it errored and nothing would boot.

so atm i have winxp how it was b4, no ubuntu or grub at all

And i cant reinstall ubuntu cuz i dont know how to install grub properly, it will error again then i cant get back to windows..

I think you probably had a bad burn, or your partition tables were wrong.  It sounds like you did a lot of weird stuff with them before.  Try this:

1) Unplug your windows HD and set the bios to boot from the second drive
2) boot the live cd to the other HD and use a default layout (you will want more than 256mb for swap).
3) install, letting grub install to the only HD available.
4) boot into Ubuntu, and add windows to grub (see the example in the grub.conf file for the syntax or look in the wiki for help)
5) plug in the windows drive again, leaving the bios to boot from Ubuntu's drive

This should allow you to boot from either OS off the Ubuntu drive via grub.  If you need more help, anything you could ever need to know is in the wiki.

---

### Post by DeltaUK on 2007-04-09
Thankyou for this info, i know it isnt a bad burn as it installed fine on my friends pc. he only has 1 hard drive so this wasnt a problem

i will try this soon

---

### Post by DeltaUK on 2007-04-09
4) boot into Ubuntu, and add windows to grub (see the example in the grub.conf file for the syntax or look in the wiki for help)

Im not sure what u mean, how do i get to grub.conf? do i need to use terminal? i need to make sure of this becuz once i have done this, and this step i cant do, i will never get back to windows.

---

### Post by DeltaUK on 2007-04-09
this is driving me mad now, i followed the steps, i only had 1 hard drive connected, installed ubuntu and got the same error, nothin will boot.

I found an old hard drive that no1 used to test on, i did a full format thingy on the setup so it was automatic, and that worked. i then went back into the partitions of that drive that worked to make sure i was partitioning my other drive right. i dno what im doin wrong and im going crazy


HELP!

:( :mad:

---

### Post by confused57 on 2007-04-09
Maybe the Window's entry in this thread will work:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by DeltaUK on 2007-04-10
Thanks for this, but i cant actually get to the terminal since ubuntu doesnt boot

When i installed ubuuntu i disconnected my windows drive, but left my other drive as it was in the slave position, could this be the problem? would switching the cables around in my pc make the same hard drive primary?? :S

ATM i have this:

If i boot up with windows drive, everything loads ok and windows boots

If i boot up with ubuntu, i get Error 17

:confused:

---

### Post by igknighted on 2007-04-10
hmm, sounds like grub is getting confused with how your system is naming the disks.  Try booting into grub, then hitting 'e' over the ubuntu entry to edit it.  Take note of the line "root (hd0,#)" (where # is the number to remember).  Then go to the line that starts "kernel ..." and hit 'e' again.  Now, arrow back you get to the pathname to the kernel file (starting with /boot/...).  It should be right after the word kernel.  Delete the path, but don't delete the root= part right after it.  Now, in the spot the path was, try adding this: "(hd1,#)/boot/" (no quotes, and # is the number from before).  Then hit tab.  If it doesn't give you a list of files, you have the wrong partition.  Try again with (hd0,#).  Keep expirimenting until you find the right partiton, then make sure to finish the path to the file named before.  You will need to add the same partiton (hd$,#) before the initrd file in the next line, as well as change the root(hd0,#) line to the same as well.  Remember the changes you made, as they won't be saved.  Once the system boots, you need to edit the file /boot/grub/menu.lst as root to the one that successfully booted the system.  This is also the file where you add the instructions to boot windows.

Hope this helps... it seems greek at first, but grub is a tremendous program once you've spent the time to figure it out.

---

### Post by DeltaUK on 2007-04-10
But i cant boot into grub...

---

### Post by confused57 on 2007-04-10
You could burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download and may be able to boot your Linux install

If you want to mount your Ubuntu, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by DeltaUK on 2007-04-10
The super grub disk wouldnt work, all the options to fix grub fail..  

so in the end i chose uninstall grub, this worked, but then restore grub didnt work

i got error 15

"unlucky"

sumthihg like that :S

and thats the same for all the auto installs/restores and all the manual ones also

:(

---

### Post by DeltaUK on 2007-04-10
Well now i am completly confused

I used the option on the ubuntu intall "resize hard drive"

and i only had 1 hard drive connected as primary master

I did this so that i knew the partitioning would be done by the installer and cant be wrong, and i STILL got Error 17

So how do i fix error 17!!!

Help

---

### Post by dstew on 2007-04-10
So now, do you have only one hard drive in your system? Is Ubuntu installed on it?

If Ubuntu Linux is installed, all we need to do is install grub correctly. Error 17 only means that the grub menu is looking for a linux partition in the wrong place. It is a configuration problem only, not a serious disk problem or anything that threatens your system.

Grub problems can appear menacing, but it is really a benign program, and will not hurt your system.

---

### Post by DeltaUK on 2007-04-10
yes ubuntu is installed and was a clean install everything went fine, i installed with only 1 hard drive in.

i know that its only the grub that needs sorting

but i dont know how

help?

---

### Post by dstew on 2007-04-10
You will probably need to re-install grub. Here is a link that tells how to do it. 

[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

Boot the live CD, open a terminal, and start grub. You get the grub> prompt, and this is where you enter the commands to re-install it. I recommend using the **find /boot/grub/menu.lst** command rather than guessing. And, use **setup (hd0)** to put the grub boot loader in the MBR.

After you have re-installed grub, you will probably have to edit the grub configuration menu (/boot/grub/menu.lst) also. But first, re-install it and get the menu screen up.

---

### Post by DeltaUK on 2007-04-10
i have tried reinstallin grub from terminial b4, i did:

sudo grub

find /boot/grub/stage1

it said (hd0,1)

i then did 

root (hd0,1)

and then 

setup (hd0)   i also tried   setup (hd0,1)

and then it duz the install thingy i get a fail msg:

Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  failed (this is not fatal)

everything else succeeds

but same error 17

---

### Post by dstew on 2007-04-10
You should not have done setup (hd0,1). This installs the boot loader onto the boot sector of the partition, but you do not want it there, you want it in the MBR. So, if you do root (hd0,1) followed by setup (hd0), do you still get the embed error message, and the error 17?

Please boot the CD, open a terminal, and post the output of **sudo fdisk -l**

---

### Post by DeltaUK on 2007-04-10
heres what i got from Sudo fdisk -l

Disk /dev/hdb: 163.9GB
255 head, 63 sectors/track, 199929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


Device	        Boot	Start	     End	Blocks	              ID	    System

/dev/hdb1		  1	    17874	143572873+	 7	     HPFS/NTFS
/dev/hdb2	*      17875	19841	    15799927+	      83	 Linux
/dev/hdb3		19842	 19929	     706860	         5	     Extended
/dev/hdb5		19842	 19929	     706860+	        82	   Linux swap / solaris

---

### Post by dstew on 2007-04-10
It looks like Linux gives this disk the name /dev/hdb, but you are giving grub the name (hd0). Usually (hd0) has the linux name /dev/hda.

Post the output of this command:

cat /boot/grub/device.map

Grub uses this map file to match the grub/bios names (hd0) to the Linux disk names. If your original grub installation mis-matched the names, that could be the source of your problem.

If the device.map file shows mis-matches, they can be corrected.

---

### Post by DeltaUK on 2007-04-10
well i did that and i got this

File or directory not found

then i reinstalled grub, it did this perfectly no errors

did the cat /boot/grub/device.map

and got file not found again

then i did to check cat /boot/grub

directory does not exist.. WTF??

ideas?

---

### Post by confused57 on 2007-04-10
You have to mount the partition first, if you're using the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb2 /media/ubuntu
```

then you can check files on your root partition:
```
gksudo gedit /media/ubuntu/boot/grub/device.map
gksudo gedit /media/ubuntu/boot/grub/menu.lst
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by DeltaUK on 2007-04-10
device.map I got

(hd0)	/dev/hda

Menu.lst I got

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
# kopt=root=UUID=c17e662b-f98c-4702-b9ff-e89bdb558875 ro
# kopt_2_6=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Fstab I got

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c17e662b-f98c-4702-b9ff-e89bdb558875 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3b0f6a4c-b968-4252-892b-e91345465f14 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by DeltaUK on 2007-04-10
sry for quick bump but i need help quick cuz i want this up n runnin by midnight. 10:45 now

---

### Post by DeltaUK on 2007-04-10
right im on a laptop so i can do things in ubuntu live cd whilst bein on the forums, so if you post a suggestion ill be tryin it as soon as i see ur post so keep on this thread. also if anybody here has an idea what is wrong with mine and have some IM program i would be most grateful if u could talk me through the steps in IM as i do them with my pc.

thanks

---

### Post by DeltaUK on 2007-04-10
no replies for a couple of hours, does this mean no1 knows how to fix this?

im kinda desperate for this to be fixed like now, but no1 seems to know..

---

### Post by dstew on 2007-04-10
Here is the way I see it at present. When you installed Ubuntu the first time, it went in Ok, and Linux system was installed on /dev/hda2. At that time grub made the map connection of (hd0) to /dev/hda.

But now, since the drives were switched, and one removed, Linux is naming the first hard drive as /dev/hdb. Grub thinks the drive is (hd0) and that Linux is on the partition (hd0,1). This is based on the output of the grub find command.

However, the device.map file is telling grub that (hd0) is /dev/hda. However, /dev/hda does not exist. This might be the cause of the problem. Here is a quote from the GNU GRUB Manual 0.97:

> If the device map file exists, the grub shell reads it to map BIOS drives to OS devices. This file consists of lines like this:

     device file

device is a drive specified in the GRUB syntax (see Device syntax), and file is an OS file, which is normally a device file.

The reason why the grub shell gives you the device map file is that it cannot guess the map between BIOS drives and OS devices correctly in some environments. For example, if you exchange the boot sequence between IDE and SCSI in your BIOS, it gets the order wrong.

Thus, edit the file if the grub shell makes a mistake. You can put any comments in the file if needed, as the grub shell assumes that a line is just a comment if the first character is `#'. 

I see two ways to try to fix it. The easiest is to edit the /boot/grub/device.map file, and change the entry to **(hd0) /dev/hdb**. After that you will need to edit the /boot/grub/menu.lst and replace the /dev/hda's with /dev/hdb's.

The other way is to reformat the partition and re-install the Ubuntu linux.

---

### Post by DeltaUK on 2007-04-10
ok i done that, changed all hda to hdb, made sure uding the search

on the terminal when i opened the map and the lst files, it would say things like no rights or sumin, does that mean the file wont be saving?  it seemed to save ok

anyway still got error 17

---

### Post by DeltaUK on 2007-04-10
i just booted super grub disc, although it wont repair my grub, it shows my linux drive as hda

this is so confusing

EDIT

now i gone to gparted and it shows linux as hdb

wow this is messed up

---

### Post by dstew on 2007-04-10
I agree, this is messed up.

For changing the device.map file, I think you need to use **sudo**. That is, to edit the file, assuming you have booted the live CD, and mounted the hard drive to the /media/ubuntu directory as confused57 showed, you would use the command

sudo gedit /media/ubuntu/boot/grub/device.map

A similar command would be needed for menu.lst. Sudo gives you temporary root privileges so you can edit these system files, which are owned by root.

Try that first. If it still doesn't work, format the linux partition and reinstall. 

Just an overall observation, from many times trying to help people with similar problems, the worst grub problems occur when disk positions are changed, or disks are unplugged and plugged in later. Grub is just not smart enough to deal with the new configurations. People often unplug a drive to protect it from harm during the OS installation procedure. But this usually is not necessary, and leads to grub confusion.

Anyway, if you think you will install again, maybe the best thing would be to put your disks in, in just the way you want them to be, and go from there. Use GParted to format the Linux partition and do a fresh install.

---

### Post by DeltaUK on 2007-04-10
well the very first time i installed i had both my drives in, and the grub mdr went over my windows on, and still got error 17.

i have switched the leads over so that this is definatly the primary drive, so, from scratch i have

1 hard drive, in the primary position, i will install ubuntu to it using resize drive option which makes partitions automatically

i cannot see why this can go wrong, but i bet it will

---

### Post by DeltaUK on 2007-04-10
amazingly that didnt work, im starting to think about giving up.

i still get error 17.

i have absolutly no idea why

---

### Post by confused57 on 2007-04-10
> **DeltaUK said:**
> amazingly that didnt work, im starting to think about giving up.

i still get error 17.

i have absolutly no idea why

I don't know what's going on with your hard drive...did you change the jumper to master or is it already set to cable select?...maybe try the Super Grub Disk again.

Usually if a drive is bigger than bios supports, it results in grub error 18, not error 17.

---

### Post by DeltaUK on 2007-04-10
thats it.  the drive is bigger than the bios supprts, i remember sumin in super gub disk sayin about cylinders error 18, erm sumin like the exceeded maximum bios capability or sumin

so theres no way around this one,  just cant use it, i dont think there are any BIOS updates and from rememberin the last time i flashed the BIOS i rele dont wanna do that again!!

---

### Post by confused57 on 2007-04-10
> **DeltaUK said:**
> thats it.  the drive is bigger than the bios supprts, i remember sumin in super gub disk sayin about cylinders error 18, erm sumin like the exceeded maximum bios capability or sumin

so theres no way around this one,  just cant use it, i dont think there are any BIOS updates and from rememberin the last time i flashed the BIOS i rele dont wanna do that again!!

Here's a description of grub error 18 and possible "fixes":
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

The most common method is a separate /boot partition close to the beginning of the hard drive...other suggestions are reducing the size of the Ubuntu root partition.  One person reported making the root partition a logical partition solved it for him.  Hopefully, the above link will give a solution...good luck.

---

### Post by DeltaUK on 2007-04-10
ok thanks for all the info, i will try this 2moro

---

### Post by DeltaUK on 2007-04-11
i looked at the help page, and the bios thingy comes under error 18, so actually i will probly still have error 17 even if do sumin to make it work with bios.

I only used 15GB for the linux root/boot partition, and that wont boot, becuz of BIOS????

My windows partition boot is 80GB. so howcome that works?

:confused:

---

### Post by dstew on 2007-04-11
I don't think it is a BIOS problem. Really, the old BIOSes that  aren't able to access large disks give you the error 18. I still think your problem is grub mis-configuration.

It is interesting that SuperGrub sees your hard disk as /dev/hda, but that GParted (which I assume you are running from the Ubuntu Live CD) sees your disk as /dev/hdb. I don't understand that, but I would like to.

Did you successfully edit the device.map file as I mentioned before?

---

### Post by DeltaUK on 2007-04-11
yes i edited them and changed them all from hda to hdb

same error

i have deleted my linux partitions and used thr super grub cd to uninstall grub completly

so im back to square one.

---

### Post by DeltaUK on 2007-04-11
Now that i have linux all gone, and my drives back to how they usually are, im gonna boot super grub disk and see what it shows my drives as, then boot live cd and look at gparter, if they are the same then i might try again, but if they are inverted i have no idea whats goin on

also, i went into the microsoeft xp boot cd and looked at my partitions from there, it showed my first drive as C and second as D.  but in windows my second drive is F. :confused: 

Do u think it is a good idea to try to install to my first drive with windows, i havnt tried any linux on my windows drive yet

---

### Post by DeltaUK on 2007-04-11
ok i checked gparter and the super grub disc and they boh show my drives the same now, windows as hda and second drive as hdb

i free'd up sum space on my windows drive so im gonna attempt a dual boot from that drive this time. i have my windows cd hand to fix mbr when that goes wrong.

---

### Post by DeltaUK on 2007-04-11
Looks like i cant put it on my windows drive, gparted wont let me resize the NTFS windows boot partition, it errors

*Sigh*

---

### Post by DeltaUK on 2007-04-11
Well gparted says i have a physical problem with the disk

i booted with windows cd and did a chkdsk and it said

there are one or more errors on this drive

so now what

---

### Post by dstew on 2007-04-11
To fix the problems, use **chkdsk /f** to fix problems on the NTFS partition.

---

### Post by DeltaUK on 2007-04-11
ill do that now

---

### Post by DeltaUK on 2007-04-11
well it wont let me use the /f parameter in xp recovery thingy

so i started in safe mode with cmd. and it said it couldnt do it as the drive was in use, do u want to do it on next reboot, u put yes

but on the reboot it just did a normal chkdsk not a repair..  how do i boot up in dos??

---

### Post by dstew on 2007-04-11
The only thing I can think of now is that the disk must be in use when you try to use chkdsk /f, and that is why it won't let you repair it. This is what happens if you boot XP in safe mode and then try chkdsk /f. Are you sure you booted the recovery CD, and that the XP disk is not active when you tried it before? You have to boot from a disk other than the one you are going to fix. If you have an old DOS floppy lying around, that might work, but I don't know if ancient chkdsk or other tools would be able to repair NTFS.

---

### Post by DeltaUK on 2007-04-11
i looked around sum forums, apparently its impossible to boot dos if u only have xp installed.

the only way u can do it is make a new partition and install dos to that then boot from it, but of course i cant resize my partition

anyway i managed to fix my drive i think, i used tune up disk docter.

do u think its worth tryin to install ubuntu on windows drive, will that make a difference?

---

### Post by dstew on 2007-04-11
It is fine to install Ubuntu on the same drive that Windows is on, but of course it needs to be installed on its own partition(s). Hopefully, you can shrink your Windows partition now so you can create an ext3 root partition and a linux swap partition. Then you can install Ubuntu no problem.

---

### Post by DeltaUK on 2007-04-11
yeh installin it is no problem, gettin grub to work is another story

im gonna try installin 2moro, thanks for the help so far

---

### Post by revilodraw on 2007-04-11
would the super grub disc help our friend?

---

### Post by DeltaUK on 2007-04-12
well i thought my drive was fixed but it wasnt, gparter still wont resize partition

I can find anywhere i can run chkdsk /f

where do i run it? it wont run while im in windows, even safe mode with cmd

---

### Post by dstew on 2007-04-12
In order to do chkdsk /f, you need to boot a Windows system off of a disk other than your hard disk. You cannot repair a disk that is being used.

I think you can make a bootable windows floppy recovery disk with chkdsk on it. Here is a link to make the floppy for XP professional:

[http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=55820EDB-5039-4955-BCB7-4FED408EA73F#QuickInfoContainer](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=55820EDB-5039-4955-BCB7-4FED408EA73F#QuickInfoContainer)

And here is one for XP home edition:

[http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=E8FE6868-6E4F-471C-B455-BD5AFEE126D8](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=E8FE6868-6E4F-471C-B455-BD5AFEE126D8)

I have never used these disks, so I don't know how they work, but [this]("http://www.pcworld.com/printable/article/id,112479/printable.html") page says it will work.

---

### Post by DeltaUK on 2007-04-12
im in the middle of a chkdsk from tuneup again, it seems to fix it, but then as soon as i go into gparter and try to resize, it errors, then chkdsk finds the error. its as if gparter is making the bad sectors.

the chkdsk is takin yonks, is it safe to hard reset when its running?

---

### Post by dstew on 2007-04-12
I would not hard reset while chkdsk is working, especially if it is being run with the /f switch. Are you sure that version of chkdsk you are using is OK?

---

### Post by DeltaUK on 2007-04-12
well i give up now, ive done so much and im tired of it.

i may try again when ubuntu 7 is released.

thanks for trying

Matt

---

