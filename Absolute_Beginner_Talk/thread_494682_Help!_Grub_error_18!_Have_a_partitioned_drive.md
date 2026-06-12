---
title: "Help! Grub error 18! Have a partitioned drive"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-07-07
Can somebody help me with this problem? 

I love xubuntu, but I also like to try other OS. I found Puppy very good for an for an obsolete computer such as this.

Therefore I purchased a 160 giga HD with the intent of partitioning it and instal a lot os OS.

After a week of partitioning, formating, installing, etc. etc. I still can't make it work

Grub is installed but gives an ERROR 18, and doesn't boot.

I also tried a dowload manager in windows wich boots and recognise all the OS in the discs. But doesn't load any of the OS except for windows 2000. Is gives an error OUT OF RANGE when I try to boot form the other OS.

Right now I have 3 Hds

A 10 giga primary master wich has windows 2000 installed

A 160 giga secondary master wish has 4 ext3 partitions. Partition 1 has Xubuntu installed, partition 2 has dreamlinux, partition 3 has PC-BSD, and partition 4 has rudy Puppy Linux

The secondary master is the dvd drive and the secondary slave is a 4 giga HD wich has Puppy linux standard installed.


Befor i had the partitioned drive to the system it all worked fine, but now grub fails. What am I doing wrong? Is it from the PC-BSD OS? Sould I partiton the drive with extended partitons instead of prymary ones? In gparted I noticed something called flags. Do I need to set a flag to the partitions? Wich one?


I would apreciate any help because I'm tottaly lost.

---

### Post by Bothered on 2007-07-07
See here: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

Did one of your later installs install GRUB? If so, it may not be able to boot as it is too far into the drive. You need to change the master boot record so that the first linux partition is booted (I'm not sure how to do this - a later poster may help), and then add the other OSs to the menu.lst in that partition.

This is certainly not a logical/primary partition type problem.

---

### Post by omkarwagh on 2007-07-07
do you have any xubuntu live cd?

if so run it. then mount your xubuntu hard drive on /mnt
now if you hard disk is say /dev/hda type the following
sudo grub-install --ROOT-DIRECTORY=/mnt /dev/hda
this will change the master boot record to boot from xubuntu.

if this doesnt work then its probably because your bios cannot access that block on which the booting kernel is installed. one sure shot way to make it run would be to have all of you OS's on the first "x" cylinders of your hdd. im not too sure on how much memory this means(try googling for the exact number. i think its 1024 but im not sure) but essentially what you do is
install your kernels on minimum partitions(say 2GB each whatever it needs) and then keep your /home mounted on another partition altogether.

---

### Post by Old Pink on 2007-07-07
I remember my first GRUB Error 18. 

I formatted. Went 100% Ubuntu. Never looked back. :P 

Fair enough, it was a ridiculous choice then, and I lost *a lot* but I've never regretted it. :)

Been almost a year now. :)

---

### Post by razeshkale on 2007-07-07
try to boot with Live CD and reinstall Grub 
if u cant get through I think better way formatt HDD n everything will b sweet 
for forever!!!

---

### Post by Bothered on 2007-07-07
> **omkarwagh said:**
> if this doesnt work then its probably because your bios cannot access that block on which the booting kernel is installed. one sure shot way to make it run would be to have all of you OS's on the first "x" cylinders of your hdd. im not too sure on how much memory this means(try googling for the exact number. i think its 1024 but im not sure) but essentially what you do is
install your kernels on minimum partitions(say 2GB each whatever it needs) and then keep your /home mounted on another partition altogether.

I thought you only needed /boot on the first "x" cylinders? Not the whole kernel?

---

### Post by Ganda_Melga on 2007-07-07
> **Bothered said:**
> See here: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

Did one of your later installs install GRUB? If so, it may not be able to boot as it is too far into the drive. You need to change the master boot record so that the first linux partition is booted (I'm not sure how to do this - a later poster may help), and then add the other OSs to the menu.lst in that partition.

This is certainly not a logical/primary partition type problem.


Ok... First I installed windows 2000 in the drive C:  (hda) Everything went fine

Then I instaledd Puppy linux in HDD. Puppy installed grub. It went fine

Then I installed PC_BSD in hdb3 with no grub install

Then I installed RudyPuppy in hdb4 with no grub install

Then I installed DreamLinux in hdb2 witho no grub install

The I installed Xubuntu in Hdb1 (the bigger partition) with grub install

After all that tried to boot. Error 18

Inserted the windows 2000 Cd opened the console and types "fixmbr"

The Pc now boots form windows, as expected.

Re-installed xubuntu in Hbd1 to make a fresh grub install

Xubuntu installs fine, but on reboot, grub gives error 18 again

Tried several variations an permutations. Some times installed Xubuntu first, others times installes bsd first, etc. etc.

Tried at least 8 variations. Also tried with extended partitions.


Always the same result (grub error 18 )

This HD is quite big and I would like to have several OS in it. I know it would be easier to use the entire hd with xubuntu, but that would spoil my original intent

---

### Post by Bothered on 2007-07-07
If you don't mind reinstalling OSs then I would try a new install, this time using custom partitioning to place a /boot partition right at the front of the (non-Windows) hard drive.

---

### Post by Ganda_Melga on 2007-07-07
> **Bothered said:**
> If you don't mind reinstalling OSs then I would try a new install, this time using custom partitioning to place a /boot partition right at the front of the (non-Windows) hard drive.


I have installed  so many times, one more wont hurt.

Errr.... what is a boot partition anyway? Is it a specific partition or its a primary partition with the boot flag on?

---

### Post by Bothered on 2007-07-07
It's a partition with mount point set to /boot. It doesn't need to be very large, ~100MB should be enough (my /boot partition is 128MB).

---

### Post by Bothered on 2007-07-07
Additionally, beware that you can only have 4 logical partitions on a hard drive. If you want to have more than 4 partitions, then create 3 logical partitions, one extended partition, and then create additional partitions within the extended partition (the extended partition is a partition in which additional logical or extended partitions can be created). The simplest way to do this might be to partition your hard drive using gparted or similar before running the xubuntu installer.

---

### Post by Ganda_Melga on 2007-07-07
> **Bothered said:**
> Additionally, beware that you can only have 4 logical partitions on a hard drive. If you want to have more than 4 partitions, then create 3 logical partitions, one extended partition, and then create additional partitions within the extended partition (the extended partition is a partition in which additional logical or extended partitions can be created). The simplest way to do this might be to partition your hard drive using gparted or similar before running the xubuntu installer.


Ok.... so I'll do the following.


Boot with windows 2000 CD. Delete all partitions in drive D. Create a partition with 60 giga in NTFS. Leave the rest of the space raw.

Boot with PuppyLinux live cd. Using gparted will create second partition (primary). Create 3rd Partiton (primary). Create 4th partion (extended) Inside the 4th partion will create that boot partition, a swap partition and a logical partition.

Next I will copy all the windows files from Hda to hdb1. This will allow me (I think) to remove the 10 giga disk and place the 160 giga as primary master still booting from windows.

On partition 4 (logical) will install Rudy puppy with no grub

On Partion 3 (primary) will install PC_BSD with no grub

On partition 2 (primary, will install Xubuntu with grub)


So.....do you think doing this will make it work?

---

### Post by Bothered on 2007-07-07
I don't think so, as the /boot partition should be right at the start of the 160GB disk. Also, I don't think you need to move the Windows partition - I would leave that where it is. Unfortunately I'm not familiar with the installers for Dreamlinux, PC-BSD or Puppy Linux. However, the procedure I would use would be something like:

1. Delete all partitions off the non-Windows hard drive.
2. Using gparted (e.g. using the Puppy Linux live CD, if it supports it) create four partitions as follows (in this order on the disk):

Partition 1: Logical ~100-200MB ext3 (will be boot)
Partition 2: Logical swap partition (e.g. 1GB, 2GB, depending on preference)
Partition 3: Logical, size of your choice ext3, for xubuntu
Partition 4: Extended, size of your choice, to contain all other operating systems
Within partition 4: Could leave this blank for now. If you wish, create a home partition in here to be shared between operating systems.

3. Now run the install for the non-xubuntu operating systems, ensuring they only install to the extended partition (but can, of course, use partition 2 as swap) and not to partitions 1 or 3. Also, if you created a home partition, make sure they set the mount point for this partition to /home. Do not include GRUB in these installs.
4. Finally run the install for xubuntu, using custom partitioning to select partition 1 with mount point /boot and partition 3 with mount point / (root) (and the home partition, if you created one, with mount point /home).

---

### Post by Ganda_Melga on 2007-07-07
> **Bothered said:**
> I don't think so, as the /boot partition should be right at the start of the 160GB disk. Also, I don't think you need to move the Windows partition - I would leave that where it is. Unfortunately I'm not familiar with the installers for Dreamlinux, PC-BSD or Puppy Linux. However, the procedure I would use would be something like:

1. Delete all partitions off the non-Windows hard drive.
2. Using gparted (e.g. using the Puppy Linux live CD, if it supports it) create four partitions as follows (in this order on the disk):

Partition 1: Logical ~100-200MB ext3 (will be boot)
Partition 2: Logical swap partition (e.g. 1GB, 2GB, depending on preference)
Partition 3: Logical, size of your choice ext3, for xubuntu
Partition 4: Extended, size of your choice, to contain all other operating systems
Within partition 4: Could leave this blank for now. If you wish, create a home partition in here to be shared between operating systems.

3. Now run the install for the non-xubuntu operating systems, ensuring they only install to the extended partition (but can, of course, use partition 2 as swap) and not to partitions 1 or 3. Also, if you created a home partition, make sure they set the mount point for this partition to /home. Do not include GRUB in these installs.
4. Finally run the install for xubuntu, using custom partitioning to select partition 1 with mount point /boot and partition 3 with mount point / (root) (and the home partition, if you created one, with mount point /home).


Great help! Thank you very much!!! Will start working on it right now! Already booted with the puppylive cd, going to run gparted to delete the partitions, etc, etc...

Later I will let you know how it went. Many thanks for your guided help!

---

### Post by Ganda_Melga on 2007-07-09
Negative negative. Followed your guide, step by step, but still fails. Tried several variations but all failed. In the end I managed to wipe out the entire contents of hdd which had Puppy linux installed and built with additional modules and a lot of files, musics, photos etc....

At this point I had to go back to windows, which is familiar ground. Hda (10 giga) has windows 2000, I installed Pc-Bsd in hdd (4 giga) and i suppose I have to use the entire hdb for a linux distro, either xubuntu or puppy. Xubuntu is better,l but puppy is very light and this pc is obsolete.

Any way, many thanks for all your help. This one is way over my head!

---

### Post by Bothered on 2007-07-09
Bah, I really thought that would work. Sorry for all the hassle.

---

### Post by Ganda_Melga on 2007-07-10
> **Bothered said:**
> Bah, I really thought that would work. Sorry for all the hassle.

No problem. I really thank you for all the help!

---

### Post by alienexplorers on 2007-07-10
Boot into your Ubuntu Live-CD.  Enter Terminal and Enter
> sudo grub
Now at the grub> prompt enter:
> find /boot/grub/stage1
You will get an output such as (hdz,x)  The "z" is your drive number and "x" is your partition number
enter at the grub prompt:
> root (hdz,x)
setup (hdz)
for the setup line leave off the partition data.
quit grub
reboot

---

### Post by alienexplorers on 2007-07-10
Can you list your menu.lst file.  Copy the following commands to Terminal:
> cat /boot/grub/menu.lst

---

### Post by Ganda_Melga on 2007-07-16
> **alienexplorers said:**
> Can you list your menu.lst file.  Copy the following commands to Terminal:

Well....I gave up on having so many O.S. Just to complicated for me! Right now I only have windows 2000 on hda (10 giga) and xubuntu on hdd (4 giga) hdb is a 160 giga disk wich is asleep now. I mean it does have 2 partitions of 80 gigas, but it's only usefull for storing files (musics videos etc...)


Type the command you gave me produces this:

melga@retrotech:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=269dbb40-2eeb-4177-a2b8-083eb886ceef ro
# kopt_2_6=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

melga@retrotech:~$ 

Too much for me to understand, I'm afraid. Also I would like to re-install grub or modify it and don't have a clue what to do. But I'm going to open a new thread for that.

---

