---
title: "total noob GRUB question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-02-16
i can't resolve my grub error 17 when booting ubuntu from an external drive. so...

i'm wondering if i could reinstall grub onto my internal harddrive, then use fixmbr to erase it, then put grub back onto my external harddrive using a live cd.

this could be the dumbest thing u have ever heard, but i would appreciate it if somebody with any experience what-so-ever could just clarify that for me. 

thx, any help is greatly appreciated

---

### Post by alyoung on 2007-02-16
If you boot using the LiveCD, surely you could just edit the MBR and anything else on the external drive directly?

Also, what filesystem is on the external drive? If it's anything other than ext2 or ext3, that could be the problem.

---

### Post by gameman12 on 2007-02-16
thx a lot for the speedy reply

nothing else is on the drive yet, but i will use it for backup for my internal hard drive wants ubuntu problmes are solved

filesystem is ext3 i believe. ubuntu installed it and i haven't changed it so....

btw, how would i edit the mbr with the cd?

---

### Post by bulldog on 2007-02-16
If you install GRUB on an external drive you must have the possebillity to boot from an USB device in order to use it.
Reinstalling GRUB from the live cd is easy.
Just enter the right disk you want to install to.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Grub will be installed to the mbr of the hdd which contains Ubuntu.
If you change the setup into an other disk you have to alter your menu.lst to let ubuntu boot.

EDIT,
Maybe it's a lot easier to set GRUB on the hdd you boot from and alter menu.lst to point to the ubuntu install on the external drive.

---

### Post by gameman12 on 2007-02-16
once again, thx for speedy reply, but i've tried that already and i get the same error

and yes, i do have the option to boot from usb device.

i'll try agiain, see what i get

---

### Post by alyoung on 2007-02-16
I hate to say this, but try reinstalling Ubuntu, and when you are asked to set up the partitions on the external drive, delete the partitions which already exist and set up the partitions again, making sure the filesystem is ext2 or ext3; that is, if no one else has a more desirable answer.

---

### Post by bulldog on 2007-02-16
If you can boot the live cd can you give me the output of ```
sudo fdisk -l (l as in like)
```
Also your menu.lst will be nice so we can have a look how things are setup.

---

### Post by alyoung on 2007-02-16
> **bulldog said:**
> If you can boot the live cd can you give me the output of ```
sudo fdisk -l (l as in like)
```
Also your menu.lst will be nice so we can have a look how things are setup.

Ha, maybe I should have asked him for the output of 'fdisk -l' before offering that recommendation...

---

### Post by gameman12 on 2007-02-16
i have no idea how to set up partions....sry i really am a [I]super[I] nooob


thanks for the suggestion though

if you have an instructions u want to share, feel free[/I][/I]

---

### Post by bulldog on 2007-02-16
> **alyoung said:**
> I hate to say this, but try reinstalling Ubuntu, and when you are asked to set up the partitions on the external drive, delete the partitions which already exist and set up the partitions again, making sure the filesystem is ext2 or ext3; that is, if no one else has a more desirable answer.
Reinstalling is not necessary in most cases,just make the menu.lst point to the right partitions.
This kind of things happens a lot with multiple hdd's.
It's also easy to fix if you know what you're doing.

---

### Post by alyoung on 2007-02-16
I know, but I prefer a brute force option....

He should definitely post the output of 'sudo fdisk -l', though.

---

### Post by gameman12 on 2007-02-16
another noob question: how do i give u "the menu.lst" u need??

---

### Post by alyoung on 2007-02-16
menu.lst is in /boot/grub.

You can open it in gedit, and copy and paste what's in the file.

---

### Post by bulldog on 2007-02-16
> **alyoung said:**
> menu.lst is in /boot/grub.

You can open it in gedit, and copy and paste what's in the file.

Yes after you mount your ubuntu install,otherwise you get nothing we can use.

@TS,
Give the outcome of the fdisk command with the external drive connected.
This way we can see what command you have to use to mount your ubuntu.

---

### Post by alyoung on 2007-02-16
> **bulldog said:**
> Yes after you mount your ubuntu install,otherwise you get nothing we can use.
.

Yeah, I'm not at my best, it's half-past midnight. Sorry.

---

### Post by bulldog on 2007-02-16
It's 1:30 AM here [The Netherlands] I just wanted to go to sleep.
But if TS isn't too slow,we can solve his problem before we call it a day.

---

### Post by alyoung on 2007-02-16
> **bulldog said:**
> It's 1:30 AM here [The Netherlands] I just wanted to go to sleep.
But if TS isn't too slow,we can solve his problem before we call it a day.

Us Europeans, always working. :)  (I'm in the UK)

---

### Post by gameman12 on 2007-02-16
here are the results


Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           6       48163+  de  Dell Utility
/dev/hdc2   *           7        9336    74943225    7  HPFS/NTFS
/dev/hdc3            9337        9729     3156772+  db  CP/M / CTOS / ...

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29929   240404661   83  Linux
/dev/sda2           29930       30401     3791340    5  Extended
/dev/sda5           29930       30401     3791308+  82  Linux swap / Solaris

---

### Post by gameman12 on 2007-02-16
here is menu.lst

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
# kopt=root=UUID=72d191a1-f3d6-48d1-9ca9-d271568f5681 ro
# kopt_2_6=root=/dev/sda1 ro

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by alyoung on 2007-02-16
'# groot=(hd1,0)'

Delete the hash at the beginning of this line, save and try to boot from your USB drive again.

---

### Post by bulldog on 2007-02-16
We have to mount sda1 to reach the menu.lst.
```
sudo mkdir /mnt/rescue
```
```
sudo mount /dev/sda1 /mnt/rescue
```

Now you can reach the menu.lst by```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

Give us the menu.lst to see were it is pointing at.
Another question is on which disk is grub installed?
Is it the sda disk or your internal.

---

### Post by alyoung on 2007-02-16
He's already posted the menu.lst

'# groot=(hd1,0)'
 
 Delete the hash at the beginning of this line, save and try to boot from your USB drive again.

---

### Post by gameman12 on 2007-02-16
last noob question of the night, i'm in the file, but what's the Hash?

---

### Post by alyoung on 2007-02-16
The hash is the '#' symbol. It makes grub ignore that line.

---

### Post by gameman12 on 2007-02-16
sda disk, NOT internal

---

### Post by bodhi.zazen on 2007-02-16
> **alyoung said:**
> '# groot=(hd1,0)'

Delete the hash at the beginning of this line, save and try to boot from your USB drive again.

NO ...

In meun.lst comments in the configuration section have a double ##

The single hash is correct here :p

(Outside of the configuration section you are correct a single hash will comment out the line)

Example:

> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## **DO NOT UNCOMMENT THEM**, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=72d191a1-f3d6-48d1-9ca9-d271568f5681 ro
# kopt_2_6=root=/dev/sda1 ro

Notice the format with kopt

## = comments
# kopt=root=UUID=72d191a1-f3d6-48d1-9ca9-d271568f5681 ro = configuration

:)

---

### Post by gameman12 on 2007-02-16
thanks, sry,

---

### Post by gameman12 on 2007-02-16
should i delete it or not????!?!?!

---

### Post by alyoung on 2007-02-16
No, sorry. My mistake.

---

### Post by gameman12 on 2007-02-16
ok then, what should i do?

---

### Post by bulldog on 2007-02-16
Don't remove the hash please just tell me on which disk you installed GRUB.
You have to understand your hdd's are numbered hd0 and hd1.
If GRUB is on the internal drive (hd0),ubuntu is on hd1.
If GRUB is on the external drive this would be hd0 for ubuntu and is the internal disk hd1,in this case you have to alter the hdd numbers.
Don't change things if you don't know what you're doing.
Make a copy of menu.lst before changing anything please.

Edit,Hi friend Bodhi,long time no see.
Hope everything is well?


# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=72d191a1-f3d6-48d1-9ca9-d271568f5681 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title Microsoft Windows XP Home Edition
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1


Take a look at this changed menu.lst and alter your's the same way or copy this one over it.
You have to boot from the USB disk to let GRUB work but I think you know this already.

---

### Post by bodhi.zazen on 2007-02-16
> **gameman12 said:**
> ok then, what should i do?

You are in good hands with Bulldog ;)

Bulldog : Good to see you on the fourms :p

---

### Post by alyoung on 2007-02-16
Try reinstalling grub.

Give the command 'sudo grub'. You'll get a 'grub>' prompt. Run:

```
grub>  find /boot/grub/stage1
grub> root (hd1,0)
grub> setup (hd1)
```

If 'find /boot/grub/stage1' reports (hd1,0).

If it doesn't, please tell us what it does.

---

### Post by bulldog on 2007-02-16
> **bodhi.zazen said:**
> You are in good hands with Bulldog ;)

Bulldog : Good to see you on the fourms :p

Been rather busy lately and hadn't much time to visit the forums.
Have to think how things are being done in Linux again.:lolflag:

---

### Post by bulldog on 2007-02-16
> **alyoung said:**
> Try reinstalling grub.

Give the command 'sudo grub'. You'll get a 'grub>' prompt. Run:

```
grub>  find /boot/grub/stage1
grub> root (hd1,0)
grub> setup (hd1)
```

If 'find /boot/grub/stage1' reports (hd1,0).

If it doesn't, please tell us what it does.

No offence,but if you aren't too familiar with GRUB,maybe you can learn something,if you pay some attention.
Reinstalling GRUB isn't necessary in this case,just point menu.lst to the right partitions and it should be fine.
Maybe we have to change something in fstab too,but I don't think so.

---

### Post by alyoung on 2007-02-16
> **bulldog said:**
> No offence,but if you aren't too familiar with GRUB,maybe you can learn something,if you pay some attention.
Reinstalling GRUB isn't necessary in this case,just point menu.lst to the right partitions and it should be fine.
Maybe we have to change something in fstab too,but I don't think so.

My reference to that was mostly for the sake of the 'find' command: it'd definitely point to the GRUB partition. The ubuntu installer defaults to installing GRUB on hd0, MBR.

---

### Post by bulldog on 2007-02-16
> **alyoung said:**
> My reference to that was mostly for the sake of the 'find' command: it'd definitely point to the GRUB partition.

Yep.you're right about that,but I've posted a menu.lst which is already changed to point to the right partitions.:) 
So we already know were the root is,don't we?

If we know the outcome of fdisk and we see a ubuntu partition and a swap we know which one contains the root partition.
Next step is to determine were the GRUB is installed,on which disk that is,so we know what is hd0 and hd1.
That's all we need to know to make a correct menu.lst entry.

---

### Post by alyoung on 2007-02-16
I do indeed apologise. It's too late for me - I shall now live in your shadow eternally, as I have shamed myself.

---

### Post by bulldog on 2007-02-16
> **alyoung said:**
> I do indeed apologise. It's too late for me - I shall now live in your shadow eternally, as I have shamed myself.

You're aproach is good but it's a little annoying if we both come with different solutions,it will make it not much easier for TS to see what to do.
I didn't mean you have to shame yourself,I appologize for that.

---

### Post by confused57 on 2007-02-16
> **alyoung said:**
> Try reinstalling grub.

Give the command 'sudo grub'. You'll get a 'grub>' prompt. Run:

```
grub>  find /boot/grub/stage1
grub> root (hd1,0)
grub> setup (hd1)
```

If 'find /boot/grub/stage1' reports (hd1,0).

If it doesn't, please tell us what it does.

Welcome back, bulldog.   The above might work, if you want to be able to boot your Windows without your external hard drive connected...you'd also need to restore your Windows mbr, using fixmbr.  Once Windows is able to boot independently, then set your external drive as the first boot device, then highlight the Ubuntu entry, press "e" to edit, then change root to (hd0,0), then "b" to boot...IF it boots, then make it permanent in your /boot/grub/menu.lst.

Or after repairing Windows mbr, you could just reinstall Ubuntu on the external hd, as described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

Forgive my intrusion, thought I'd offer another option, hopefully, without making it too confusing for the OP.

---

### Post by bulldog on 2007-02-16
> **confused57 said:**
> Welcome back, bulldog.   The above might work, if you want to be able to boot your Windows without your external hard drive connected...you'd also need to restore your Windows mbr, using fixmbr.  Once Windows is able to boot independently, then set your external drive as the first boot device, then highlight the Ubuntu entry, press "e" to edit, then change root to (hd0,0), then "b" to boot...IF it boots, then make it permanent in your /boot/grub/menu.lst.

Or after repairing Windows mbr, you could just reinstall Ubuntu on the external hd, as described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

Forgive my intrusion, thought I'd offer another option, hopefully, without adding too much additional confusion.

Hi confused57,nope it's always better to see more options.
You and I know what the easiest way is in this case,but if TS just want to be able to boot from his external drive and launch ubuntu it's fine by me.
We try to make this happen,and if TS decides it's better to boot from the internal disk [windows]and just connect the external drive to boot ubuntu we can make that happen too.:)

---

### Post by confused57 on 2007-02-16
> **bulldog said:**
> Hi confused57,nope it's always better to see more options.
You and I know what the easiest way is in this case,but if TS just want to be able to boot from his external drive and launch ubuntu it's fine by me.
We try to make this happen,and if TS decides it's better to boot from the internal disk [windows]and just connect the external drive to boot ubuntu we can make that happen too.:)

You and I know this, but I wasn't sure if gameman12 knew he wouldn't be able to boot his computer without the external drive connected, if grub is installed to Windows mbr...might be good experience to go ahead and get grub working from Windows mbr, as you suggested...then at a later time, consider other options.

I don't think gameman12 is on the forums currently, he'll have plenty to "digest" when he reports back.

---

### Post by gameman12 on 2007-02-16
i'm back, i installed grub onto hd1, my external harddrive, on purpose so i could boot windows w/o the external drive.

---

### Post by gameman12 on 2007-02-16
anybody know who to save a new menu.lst 

it says i don't have permission

---

### Post by confused57 on 2007-02-16
> **gameman12 said:**
> anybody know who to save a new menu.lst 

it says i don't have permission

I missed it the first time, but just noticed that bulldog's suggested menu.lst for booting from the external hd is excellent...so he's already given you an entry to boot Windows.

You need to use sudo:
```
gksudo gedit /boot/grub/menu.lst
```
if you're using nano
```
sudo nano /boot/grub/menu.lst
```

If you decide to restore Windows mbr:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see the section "Uninstall Ubuntu"

and the section "Super Grub Disk"
it's an excellent tool to have to boot both Windows & Linux, as well as, restore Windows mbr or Linux grub

---

### Post by gameman12 on 2007-02-16
and this will alow me to change the file to the one bulldog made?

---

### Post by confused57 on 2007-02-16
> **gameman12 said:**
> and this will alow me to change the file to the one bulldog made?
Yes, it "should", if you've installed grub to your external drive's mbr and then select to boot it first.  I don't think you'd need to copy the entire menu.lst that bulldog gave, just change the root entries to (hd0,0), then add the Windows entry to very bottom of your current menu.lst.

Here's how to install grub from the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
you've already been instructed how to do this, but thought I'd give you the above thread

---

### Post by gameman12 on 2007-02-16
ok, now i'm completely stumped.

i keep getting an error saying "could not save the file /boot/grub/menu.lst unexpected error: file not found"

i'm just going to reinstall grub on the external hard drive like you sugested

---

### Post by confused57 on 2007-02-16
> **gameman12 said:**
> ok, now i'm completely stumped.

i keep getting an error saying "could not save the file /boot/grub/menu.lst unexpected error: file not found"

should i try reinstalling grub to my external drive mbr?

Here's what I'd try, since grub is on your Windows mbr...set up your bios to boot first to your Windows drive & your external drive second...then boot up the live cd, then install grub to hd1, see the link I gave you.
```
find /boot/grub/stage1
```
should return root (hd1,0)
if it does, enter:
```
setup (hd1)
```
this should install grub to your external drive's mbr
to exit grub:
```
quit
```

Then remove the cd, change your boot order to boot your external drive first...you "should" get a grub menu at boot(may need to press "esc" to enter menu)...highlight the entry to boot Ubuntu, press "e" to edit, then change the root line to **root (hd0,0)**, then press "b" to boot...if Ubuntu boot OK from your external drive, then you can make your changes permanent in your /boot/grub/menu.lst.

To be able to boot Windows, without the external drive connected, you'll need to restore Windows mbr.

---

### Post by gameman12 on 2007-02-16
i'll try that, thx.

---

### Post by gameman12 on 2007-02-16
YES!!!!! It WORKED!!!

 THANK YOU SOOO MUCH, CONFUSED!!! 

I can't thank you all enough (except i have to thank confused most because his advice finally did the trick)!!!! 

thanks a lot guys ur amazingly helpful

ps. will ubuntu always boot correcly now from my external drive?

---

### Post by confused57 on 2007-02-16
> **gameman12 said:**
> YES!!!!! It WORKED!!!

 THANK YOU SOOO MUCH, CONFUSED!!! 

I can't thank you all enough (except i have to thank confused most because his advice finally did the trick)!!!! 

thanks a lot guys ur amazingly helpful

ps. will ubuntu always boot correcly now from my external drive?

Great, I'm amazed you were able to do all that so quickly...yes, it should continue to work, if you made the necessary changes permanent in your /boot/grub/menu.lst and added the entry to boot Windows(similar to the one bulldog mentioned)...here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
You mainly just need to check out the entry I use to boot Windows, either Windows entry should work...

The menu.lst that bulldog gave you covered about everything you need in yours, you need to change to the following for this section(taken from bulldog's):
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

When you get on the internet & have a kernel update, this is what update-grub will use to make the new kernel boot entries.

---

### Post by gameman12 on 2007-02-17
Thanks soo much for your help.

no i'm having problems connecting to my wifi network at home....

---

