---
title: "[SOLVED] Grub problem - can't boot Vista without USB drive connected"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Jeztastic on 2007-12-02
Hi,

I have just installed Gutsy on my USB HDD. However, I can no longer boot the Vista on my Laptop without my HDD connected.

Please help! I have done a search, but found nothing relevent.

Jez

---

### Post by meierfra on 2007-12-02
Open a terminal in ubuntu (Applications->Accessories->Terminal) and 
type
```
sudo fdisk -l
```
(l is a lowercase L)
Post the  output and  I will give you detailed instruction how to fix the problem

---

### Post by gn2 on 2007-12-02
I would suggest you disconnect the USB drive then repair the MBR on the internal drive, (by whatever method is required for Vista)

Next, reconnect the USB drive and run a Super Grub Live CD and install GRUB onto the USB hard drive.

Next set the USB drive before the internal drive in the BIOS boot list, when you want to boot from the USB drive, just plug it in before booting.

---

### Post by meierfra on 2007-12-02
gn2 instruction only solve 2/3 of the problem. You will also need to edit "/boot/grub/menu.lst" Click on "DualTwo" in my signature for  an example how to the whole thing rather quickly  (no need for any LiveCD) 

But the actual numbers in the example might be different for you. That's why I need  the output  of  "sudo fdisk -l"

---

### Post by SilverAdder on 2007-12-02
I actually have the exact same problem. Been wrestling with this for some time now... The output of the fdisk command is as follows: 

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff9eaa05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12162    97683456    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3735    30001356   83  Linux
/dev/sdb2            3736        4233     4000185   82  Linux swap / Solaris

```

I thought of trying the super grub disk but so far grub has been nothing but trouble for me :) How would you go about setting it up with the super grub live cd?

---

### Post by meierfra on 2007-12-02
SilverAdder: Just click on "DualTwo" in my signature and follow the instruction.  (Your setup is the same as in that post)

Edit: (this is to late but  just so that other people reading this thread don't run into problems)

Got that wrong. Windows is a on different partition. You need to use 

title Microsoft Windows Vista
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

for the windows item. Otherwise follow the instruction in "DualTwo"

---

### Post by SilverAdder on 2007-12-02
alright so i can boot into vista without the drive! That is awesome! More than i have accomplished so far. But i cant boot ubuntu... I get an error 17: cant mount drive... or device... or something like that. cant mount something. i take it i mapped the drives wrong. my menu.lst info said: 
```

title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```

that is root (hd0,0) instead of (hd0,1) as stated in tour post. So instead of changing root to (hd1,1) i changed it to hd(1,0), along with all the other stuff of course... was that wrong? 

Also, how do i change it now that i cant boot to ubuntu? can i do it from the live ubuntu cd?

---

### Post by Jeztastic on 2007-12-02
> Also, how do i change it now that i cant boot to ubuntu? can i do it from the live ubuntu cd?

Yes, I also now cannot boot Ubuntu... Just hanging on a black screen... Do I need re-install or can it be sorted as above?

---

### Post by meierfra on 2007-12-02
SilverAdder: Sorry, I was sure that the other post also had windows on (hd0,0).  But you actually did the correct thing: Use "root (hd1,0)" instead of "root (hd1,1)" in the windows item.  Did you change anything else?

Yes the problem can be fixed from the LiveCD. First I would like you to post the file "menu.lst". To open it:

boot from the LiveCD, open a terminal and type

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst
```

---

### Post by meierfra on 2007-12-02
Jeztastic:

> Yes, I also now cannot boot Ubuntu... Just hanging on a black screen... Do I need re-install or can it be sorted as above?

What is going on? Never had problems with this before.
So also boot from the LiveCD

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst

```

and post the content of the  file.
This assume that Ubuntu is on sdb1. In addition post the output of

```
sudo fdisk -l
```

---

### Post by SilverAdder on 2007-12-02
My menu.lst looks as follows:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6e90237-c99d-4b26-ae58-d51a8e78f44e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6e90237-c99d-4b26-ae58-d51a8e78f44e ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
savedefault
makeactive
chainloader	+1
```

So the info i changed/added is under windows vista/longhorn. everything else is default. When i did it i didnt use gksudo. I was in root. Does that matter?

---

### Post by meierfra on 2007-12-02
SilverAdder:  

Either you did'nt run "update-grub" or you weren't root then you run it or you forget to change "#groot(hd1,0)" to "#groot(hd0,0)". Anyway

Change all the  "root (hd1,0)" to "root (hd0,0)" (except for the one in the Windows item)

and just  to make sure lets reinstall grub:

```
sudo grub
root (hd1,0)
setup (hd1)
quit
```

That should do it.

---

### Post by gn2 on 2007-12-02
> **meierfra said:**
> gn2 instruction only solve 2/3 of the problem. 

Oops, forgot to mention to remove or physically disconnect the internal hard drive when installing Grub to the USB drive.

---

### Post by SilverAdder on 2007-12-02
i forgot the #groot(1,0), sorry ... can i just change it and update grub? and if so how? sudo update-grup doesnt work

---

### Post by meierfra on 2007-12-02
```
update-grup doesnt work 
```

That's right (I learned that the hard way)

You don't need to update-grub after you made the changes.

---

### Post by meierfra on 2007-12-02
Don't run "sudo update-grub" from the LiveCD. It will screw up your "menu.lst"

Edit: Actually, "sudo update-grub" will not alter menu.lst.  It just produces an error message.

---

### Post by meierfra on 2007-12-02
Just to make sure: You need to manually change "root (hd1,0)" to "root (hd0,0)" (three times)
also change "#groot (hd1,0)" to "#groot (hd0,0)"

Save the file and reboot . Do NOT use "update-grub"

---

### Post by SilverAdder on 2007-12-02
Well following your last advice worked! this is fantastic. Despite the problems ive had i cant help but love ubuntu :) thanks for the help!

---

### Post by meierfra on 2007-12-02
Good!  One down, two to go (I was working three of these cases simultaneously. All three did go wrong)

---

### Post by Jeztastic on 2007-12-02
> **meierfra said:**
> Jeztastic:



What is going on? Never had problems with this before.
So also boot from the LiveCD

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst

```

and post the content of the  file.


Here...

```


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=d9e254ef-5440-4422-99bf-ffdd8d221f15 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d9e254ef-5440-4422-99bf-ffdd8d221f15 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d9e254ef-5440-4422-99bf-ffdd8d221f15 ro single
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
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

> **meierfra said:**
> 
This assume that Ubuntu is on sdb1. In addition post the output of

```
sudo fdisk -l
```

And here...

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a51a9f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7488    58609664    7  HPFS/NTFS
/dev/sda3            7488       14594    57073664    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f719f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris


```

Hope this is what you're after...

Jez

---

### Post by meierfra on 2007-12-02
It seems you either did not edit menu.lst or the changes to not get saved..

If you turned your computer off since the last time you did this:

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu

```


Open the file  menu.lst via

```
gksudo gedit /ubuntu/boot/grub/menu.lst
```

Change  "#groot (hd1,0)" to #groot (hd0,0)"

Change   "root (hd1,0)" to "root (hd0,0)" (three times)


Change :
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

to 
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1


Make sure you save the file.


Just in case lets reinstall grub:


```
sudo grub
root (hd1,0)
setup (hd1)
quit
```

Reboot with the ubuntu drive first in the boot order

---

### Post by Jeztastic on 2007-12-02
OK, so I have re-installed gutsy now, but the Grub problem remains.

 /ubuntu/boot/grub/menu.lst just came up blank at first. However, after a few tries I got it working and made the changes. On rebooting the problem remains, and now Vista will not load.  /ubuntu/boot/grub/menu.lst is now showing as blank again. /boot/grub/menu.lst does exist.

Please help!

---

### Post by meierfra on 2007-12-02
Why did you reinstall Gutsy?   And if you reinstall you should have at least follow "gn2" suggestion and physically disconnect the internal drive.  Are you able to boot into ubuntu?

Let's start all over.  I will add a few steps so that I can see what you are doing.
 Boot into Ubuntu or Boot from the LiveCD.


Step 1: Fix menu.lst:

Open a terminal and type

```
sudo mkdir /ubuntu
sudo mount  /dev/sdb1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst &
```

If the file comes up blank, check for typos. If it still comes up blank copy the content of the terminal and post it here.

If the file opened successfully:

change (of course only if it has not been changed yet)

"#groot (hd1,0)" to "#groot (hd0,0)"

Change all "root (hd1,0)" to "root (hd0,0)" (there are three of them)

Change :

title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

to

title Windows Vista/Longhorn (loader)
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

Save and close the file. Open it  again

```
gksudo gedit /ubuntu/boot/grub/menu.lst &
```

and make sure the file was really changed.

Copy the content of the file and post it here.


Step 2: Install Grub to the MBR of the external drive:

```
sudo grub
```

and at the "grub>" prompt

```


root (hd1,0)

setup (hd1)


```

Copy the content of the terminal and post it here.

```

quit

```

Don't close the terminal.


Step 3 Remove grub from the MBR of the internal drive:

Go to Systems-> Adminstration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
(of course only if the box isn't already checked)
Click on Close (twice)

Next  in  the terminal:

```


sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

Copy the whole content of the terminal and post it here.

Step 4 Reboot with the external drive first in the boot order in the bios.

---

### Post by Jeztastic on 2007-12-03
I re-installed because nothing was working - the Grub thing wasn't my only issue. I'm glad I did, because a few other issues seem to have sorted themselves.

I couldn't disconnect the internal drive, I am using a laptop.

I'll run through the instruction in the above post later tonight, and post results.

---

### Post by meierfra on 2007-12-03
> I couldn't disconnect the internal drive, I am using a laptop.

Just for future reference: For my laptop I just need to loosen  a couple of screws  and the hard drive slides out. (I learned that the hard way then my son spilled a glass of water on my laptop)

---

### Post by quandary on 2007-12-03
<snip>
I'm currently tripple booting Linux, Windows XP MCE, and Vista...
So why do people always give improper description, <snip>?
And why always mapping drives instead of just fixing the wrong numbers? Of course mapping it works, but...
you can do that in one search and replace, without needing to start the live-disc or supergrup, which takes ages...

See:
[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

for how to solve your GRUB problems.

---

### Post by meierfra on 2007-12-03
quandary::

About LiveCD: My method, when done correctly, does not require any CD. But yours requires the  Windows CD (if grub was installed to the MBR in the internal drive) > Now you can boot-up using your WinXP/Vista install CD.   
You also used the LiveCD to install Ubuntu (and made sure that grub is installed to the correct drive).  All my cases start with Ubuntu already being installed and grub on the wrong drive. My method does not require reinstalling Ubuntu.

About mapping :  
> title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
chainloader +1

As far  I know this does not work. One needs to add "map (hd0) (hd1)" "map (hd0) (hd1)". At least it does not work on my computer. And there are lots and lost of cases in the forums there mapping solves the problem. Maybe there is something special with your computer that you get away without mapping. But in general it is required. 

> And why always mapping drives instead of just fixing the wrong numbers?

Mapping does not fix wrong numbers. It sometimes needed in conjunction with correct numbers.

---

### Post by meierfra on 2007-12-03
One point for quandary: In this [thread]("http://ubuntuforums.org/showthread.php?t=627776") one could have used the last part of quandary method  to avoid the use of the Ubuntu LiveCd.

In that case only "menu.lst" needed to edited (grub was already installed to the external drive, and the windows MBR was restored). So instead of using the LiveCD to access "menu.lst", one can access "menu.lst" through windows.

---

### Post by Jeztastic on 2007-12-03
Well done meiefra, that's all 5 now, makes you an Ace I believe! :)

All works fine now. 

That still leaves me with all my other Linux problems though! Is Linux always like this?

Thanks again.

Jez

---

### Post by meierfra on 2007-12-03
> That still leaves me with all my other Linux problems though! Is Linux always like this?

No. Most people just have a few little problems  which can be sorted out quickly. Some lucky people have no problems and a few unlucky people have lots of problems.  

But the great thing about Ubuntu  is the forums. Just about every problem can be solved by searching the forums, googeling, asking for help in the forums and patience. And at the end you should have a system  you are perfectly happy with.

---

### Post by Duck2006 on 2007-12-03
> **meierfra said:**
> No. Most people just have a few little problems  which can be sorted out quickly. Some lucky people have no problems and a few unlucky people have lots of problems.  

But the great thing about Ubuntu  is the forums. Just about every problems can be solved by searching the forums, googeling, asking for help in the forums and patience. And at the end you should have a system  you are perfectly happy with.

+1 on that for sure.

---

### Post by Jeztastic on 2007-12-03
> **meierfra said:**
> No. Most people just have a few little problems  which can be sorted out quickly. Some lucky people have no problems and a few unlucky people have lots of problems.  

But the great thing about Ubuntu  is the forums. Just about every problems can be solved by searching the forums, googeling, asking for help in the forums and patience. And at the end you should have a system  you are perfectly happy with.

OK, well, I'm off for more help!

---

