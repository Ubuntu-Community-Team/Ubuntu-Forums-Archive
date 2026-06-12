---
title: "Still having &quot;Grub error 17&quot;  after many tries!!!"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by lieobry on 2007-02-06
Sorry for making a new thread for such a common problem as grub errors, but I've been trying for three days and still I can't find the solution.

I'm installing  Ubuntu 6.06 on a computer with Windows XP. The installation ends perfect but when the system reboots there is error 17 in grub bootloader (it doesn't show the list with boot options, just reports the error).

I know what error 17 means, I've reinstalled Ubuntu for many many times (from LiveCD and from alternateCD),(with ext2 and ext3 format),(I've tried  with Ubuntu 6.10, the same problem). I 've also reinstalled grub (from the live CD).

There is an attached picture with the  partitions of my hard disk. Keep in mind that I don't want to format Windows XP partition and of course Data partition. 

I really need your help!!
Thanks in advance!

---

### Post by revilodraw on 2007-02-06
I'm having the exact same problem except i dont want xp on a partition or anything... i just want ubuntu to have one big partition to itself...

When using the livecd it gives me three partitions to put

/
/root
swap 

on and whatever i do it wants me to format some of them which i cant do or ill lose everything (wont i?)

OR when using command 

sudo find /root/grub/stage1 (or whatever it is) i get error 15...

HELP!!

---

### Post by frodon on 2007-02-06
I would try booting the live CD and then reinstall grub then check the device.map and the menu.lst file.

To reinstall grub, do as following, type :
```
sudo su
grub
find /boot/grub/stage1
```You will get a number like (hd0,4) (i will take this example for the following commands.
Now use this command using the number you get :
```
root (hd0,4)
setup (hd0)
quit
```At this step you have reinstalled grub.

Now if you still have problems and you may still have some give me the output of the "sudo fdisk -l" command and the content of your /boot/grub/menu.list file and your /boot/grub/device.map file then i will have a look to it and see if there's something wrong.

---

### Post by revilodraw on 2007-02-06
Wow, very fast response!! Thank you SO much for your help and if you can help me fix it i would appreciate that very much (might even restore my faith in humanity!!)

when i do **[B]find /boot/grub/stage1**[/B] in terminal i get
[I]
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: /boot/grub: No such file or directory
ubuntu@ubuntu:~$[/I]

_here the result of fdisk..._

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       13941       14201     2096451    c  W95 FAT32 (LBA)
/dev/sda2           14000       14593     4771305    5  Extended
/dev/sda5           14000       14593     4771273+  82  Linux swap / Solaris

---

### Post by frodon on 2007-02-06
I think you forgot to enter in the grub shell no ?

Did you type "sudo su" then "grub" before typing this command ?

---

### Post by revilodraw on 2007-02-06
Thank you for helping me!

No, i didnt forget to type in sudo grub...

this  is what happens when i do
[I]
grub> find /boot/grub/stage1

Error 15: File not found[/I]

???

---

### Post by lieobry on 2007-02-06
frodon thanks for helping me and revilodraw but I'm afraid we don't have the same problem. As far as my problem I tried to reinstall grub but as you can can imagine the problem remains. So these are my results for what you have asked.

1)The results of **fdisk -l**:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/hda2            4463       17290   103040910    f  W95 Ext'd (LBA)
/dev/hda3           17291       17354      514080   82  Linux swap / Solaris
/dev/hda4           17355       19457    16892347+  83  Linux
/dev/hda5            4463       17290   103040878+   7  HPFS/NTFS


2)When I write "gedit /boot/grub/menu.list"  I see an _empty_ document named *menu.list (/boot/grub)

3)The same with /boot/grub/device.map

Obviously I'm doing something wrong. Help me little more.. (I've boot from LiveCD)

---

### Post by revilodraw on 2007-02-06
Hi lieobry my 

gedit /boot/grub/menu.list

and

/boot/grub/device.map

are empty too so i think our problem *is* the same...

---

### Post by lieobry on 2007-02-06
revilodraw I think I've misunderstood your first post. You said something about / , /root, etc and also aboout formatting. I have finished my installation successfully and I can't boot.

Maybe we have the same problem!

Make sure that you type "sudo **su**". (For the grub installation.

---

### Post by frodon on 2007-02-06
Ok, sorry i was maybe a bit quick, first i made a typo the file is called "menu.lst" and not "menu.list" and it is the file on the partition where you installed ubuntu.
That means that you need to boot the live CD then mount your ubuntu partition, For example command to mount your ubuntu partition in your case lieobry would be :
```
sudo mkdir /mnt/ubuntu-partition
sudo mount -t ext3 /dev/hda4 /mnt/ubuntu-partition
```Then go in this partition to find the files i'm talking about.

Am i clear ?

---

### Post by revilodraw on 2007-02-06
thanks frodon... what does this mean?

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu-partition
mkdir: cannot create directory `/mnt/ubuntu-partition': File exists

---

### Post by lieobry on 2007-02-06
I'm afraid you're not frodon. Sorry for making you "suffer"(I'm newbie) but what do you mean with "go in this partition "?I tried sudo chroot /mnt/ubuntu-partition but I couldn't open gedit. What else do I have to write apart from mounting... ?

P.S.I have ext2 format.

---

### Post by frodon on 2007-02-06
Hum, strange just change the name ubuntu-partition to something else, the name of the directory doesn't matter anyway.

---

### Post by frodon on 2007-02-06
> **lieobry said:**
> I'm afraid you're not frodon. Sorry for making you "suffer"(I'm newbie) but what do you mean with "go in this partition "?I tried sudo chroot /mnt/ubuntu-partition but I couldn't open gedit. What else do I have to write apart from mounting... ?Ok i'll focus on lieobry's problem because i can't handle 2 different issues at the same time, sorry. You should open a thread dedicated to your problem revilodraw, then give me the link and i will try to help you as soon as i get the time for.

To open the file, this command should be enough if all works well :
```
sudo gedit /mnt/ubuntu-partition/boot/grub/menu.lst
sudo gedit /mnt/ubuntu-partition/boot/grub/device.map
```

---

### Post by lieobry on 2007-02-06
Really really sorry.......!!!!!!...!!!!!!


**This is the ...device.map:**

> (hd0)	/dev/hda 


**This is ...menu.lst:**

> # menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

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

---

### Post by revilodraw on 2007-02-06
ok i'll try what u tell lieobry and if it doesnt work ill start my own thread...

---

### Post by frodon on 2007-02-06
Ok lieobry, your device.map and menu.lst are both well generated so the the problem is not here for me, could you give me your fstab file please :
```
sudo gedit /mnt/ubuntu-partition/etc/fstab
```

---

### Post by lieobry on 2007-02-06
There it is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by frodon on 2007-02-06
There's something strange, why your file system is ext2 instead of ext3, did you choose explicitly to use ext2 file system instead of ext3 during install ?
If not edit the file and modify the "/dev/hda4" line to look like that : 
```
/dev/hda4 / **ext3** defaults,errors=remount-ro 0 1
```
To bring insight on what is your issue the grub 17 error happen when grub try to boot a partition which exist but the filesystem is not the one expected it why i asked for all these files.

---

### Post by lieobry on 2007-02-06
Yes I changed the file system to ext2 because I was trying so I did that to see if anything happens.

I tried many times installing in ext3 format but I had the same problem. Is there any possibility to have any problem in my WinXP installation that causes the error?

If you want to see anything else tell me.
Thank you very mych anyway!!!!!!!!!!!!!

---

### Post by frodon on 2007-02-06
First, it's better to have ext3 even if it's almost the same than ext2.

Now if all your files are good then i think to hardware issues or BIOS setup, check that your drive is the first device in the BOOT list in your BIOS setup.

Just in case tell me the exact name of your motherboard and hard drive.

---

### Post by frodon on 2007-02-06
And i forgot 2 other possibility as last attempts, you can try to install ubuntu 6.10 rather than 6.06 or/and during the install choose to use LILO instead of GRUB as boot manager.
LILO is an alternive to GRUB, it's also a boot manager which do the same job and some users prefer it, you may have no problems with LILO.

---

### Post by lieobry on 2007-02-06
**[SIZE="5"]If anyone can help I'd be very glad sending further information so that he/she solves the problem!![/SIZE]**


Thanks......

---

### Post by lieobry on 2007-02-06
Do I have to download the alternate CD for Ubuntu 6.10 to install it with LILO.

Because as I said in the beginning I tried to install 6.10 with the Live CD but I didn't see anything about LILO.

---

### Post by frodon on 2007-02-06
I'm not sure of which ISO you need maybe someone could point us the right ISO to download.

---

### Post by lieobry on 2007-02-06
Can anyone tell me if I can install LILO bootloader instead of GRUB from a CD of Ubuntu 6.10!!!!!!!!!!

Or is there any other way to do this?

---

### Post by confused57 on 2007-02-06
You could try downloading & burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's only about a 500 kb download & is an excellent tool for booting Windows or Linux.

Are you formatting your partitions with Partition Magic before installing Ubuntu?  I ask this, because you listed your partitions in your first post with PM...you're probably not, but if so, it's best to let the live cd do the formatting.

There's definitely something wrong, since "find /boot/grub/stage1" doesn't show anything.
(My mistake, it was revilodraw who mentioned this)

You can install lilo with the alternate cd:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)[SIZE="1"][/SIZE]

---

### Post by lieobry on 2007-02-06
[SIZE="5"]I'd like to conclude the hole thread so that someone else could easily help me.[/SIZE]

1) You can read my problem in my first post about my main problem!!

2)frodon has already checked some things:
    -the file /boot/grub/menu.lst
    -the file /boot/grub/device.map
    -the file /etc/fstab
All of them, as he said have no problems. (the only thing is that I have ext2 format for the root partition, but as I said I've tried many times with ext3 format)


[SIZE="3"]Anyone who wants to help (I repeat) to read carefully my first post!!!!!!!!!![/SIZE]

I'd honestly appreciate any more help.
thank you

---

### Post by geek_Man on 2007-02-06
(Quoting Frodon...)
> **frodon said:**
> <snip />To reinstall grub, do as following, type :
```
sudo su
grub
root (hd0,3)
setup (hd0)
quit
```At this step you have reinstalled grub.
<snip />


I've changed it a little bit, so now it's hd0,3. Lieobry, run these commands and hopefully it'll fix GRUB.

---

### Post by lieobry on 2007-02-06
geek_Man I wrote **the number that "find /boot/grub/stage1" gave me as output** (confused57 understood that I had no output from this but he was wrong, another person who had the same problem said that). frodon said (hd0,4) but it was an example. 
Although (I don't remember very well) I think that (hd0,4) was the output, so if you are meaning something else(with number 3) correct me and I will test if it works.


P.S.In a link that confused57  gave about installing LILO it says "Set the boot flag to the Ubuntu partition". That means to make the winXP partition unactive and **ubuntu partition active**. As I remember from the installation with the alternateCD, it was by default checked as active partition the on with winXP.
[LIST]
[*]Is this correct?
[*]If I change that (as the link says) is there a possibility to "ruin" my winXP partition.(not working  the fixmbr command)?
[/LIST]

---

### Post by geek_Man on 2007-02-06
Well, you got no output from that 'cause you were using the live CD. That would only work if you were booted into Ubuntu, not the CD. Have you tried doing hd0,3? I was a little confused by your last post. I'd recommend using the Super GRUB Disk. That's a really neat tool.

---

### Post by bodhi.zazen on 2007-02-06
Wow, this is a hard thread to follow, my head is spinning ...

I suspect the problem may be with your original partitioning as I thing was previously mentioned ... Partition magic does not always play well with Linux.

Hence what I would advise, as I think this may be the fastest solution:

First, try geek_Man 's advice re re-installing grub.



If that fails, and I am afraid it will, then boot the Ubuntu live (desktop) CD

1. Delete your Linux partitions. If you can not do this, delete them from partition magic and leave the space UNPARTITIONED free space.

2. Start the Ubuntu installer, install to free space, use default partitioning, and install GRUB to the MBR.

---

