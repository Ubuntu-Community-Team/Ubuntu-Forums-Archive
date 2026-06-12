---
title: "Ubuntu 6.06 has crashed and gone &quot;Blue screen&quot; indefinately."
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-13
After circa 2 years and 6 months my Ubuntu has finally turned on me denying me access to my Linux :(
I was just doing my first CD/DVD burning ever on my Ubuntu when all hell broke loose.  I was backing up my personal data on DVD and I did 2 copies which went fine.  When I was about to do my 3rd copy then Ubuntu started to get laggy and unresponsive and finally freeze.  I wasn't exactly getting a "Blue screen" more like a "Multi colored Brown screen" but the effect was the same however.  Nothing works.

**[SIZE="4"]1[/SIZE]st reboot**.
I couldn't even access GRUB it said this every time I did a reboot.
> 
GRUB Loading stage1.5.

GRUB loading, please wait...
Error17

**[SIZE="4"]2[/SIZE]nd reboot with my Ubuntu 6.06.1 Alternative CD**
I got a menu and I chose Rescue broken system or something and followed the instructions which kind of resembled some of the steps when doing a clean install.
After that I think I got stuck somewhere when there weren't any more instructions given.  So I ejected the CD and restarted the PC at least now I got GRUB access.

**[SIZE="4"]3[/SIZE]rd reboot got access to GRUB this time: memtest86+**
So in the good old GRUB menu I chose memtest86+.  It chugged along for some 54 minutes before I got tired not knowing how long this will go on doing the same kind of tests.  So I escaped the test and rebooted....

**[SIZE="4"]4[/SIZE]th reboot Ubuntu 2.6.15-28-386 (recovery mode)**
I chose the recovery mode in GRUB menu and got several pages of Error messages.  It was so much and so fast that I couldn't even write down on paper what they said.
But at the very end of the Error messages it says this which I don't understand. :confused:
> ...
...
...
BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commans.
/bin/sh: can't access tty: job control turned off
#

**[SIZE="4"]5[/SIZE]th reboot Ubuntu 2.6.15-28-386**
So when recovery mode didn't wan't to play with me I rebooted and went with the ordinary Ubuntu choice from the GRUB menu.  Now I get this Error message every time I try to reboot into it.

> Booting 'Ubuntu, kernel 2.6.16-28-386'
root (hd0,2)
          Filesystem type is ext2f, partition type 0x83
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
          [Linux-bzimage, setup=0x1c00, size=0x157a47]
initrd /boot/initrd.img-2.6.15-28-386
          [Linux-initrd @ 0x1f979000, 0x6761 ce bytes]
savedefault
boot

Uncompressing Linux... Ok, booting the kernel.

mount: Mounting [COLOR="Magenta"]/dev/hda3[/COLOR] on /root failed: Invalid argument
mount: Mounting [COLOR="Magenta"]/root/dev[/COLOR] on /dev/.static.dev failed: No such file or directory
mount: Mounting [COLOR="Magenta"]/sys[/COLOR] on /root/sys failed: No such file or directory
mount: Mounting [COLOR="Magenta"]/proc[/COLOR] on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init


[COLOR="Red"]Questions???[/COLOR]
I don't need to make a full clean install again do I?  I mean backing up your data on Ubuntus included CD/DVD burner shouldn't= Full re-installations in order to get back to ordinary life.
What can I do to fix this and get back to my Ubuntu life?
Now I'm pretty much forced back to my Windows XP partition but most of my valuable stuff are done on the Linux. [COLOR="Red"][SIZE="4"]S.O.S [/SIZE][/COLOR]somebody 	#-o

---

### Post by felicity on 2007-07-13
You say your Windows XP works OK and is on the same drive? Otherwise I would guess that maybe your drive is dying,

---

### Post by dpar on 2007-07-13
Just a shot in the dark........could your linux partition be full??? I think that when you backup stuff, it makes a copy of the backup and stores it on your drive. If the backup is large, it could have filled it up.
Maybe???

---

### Post by ajgreeny on 2007-07-13
If you have a liveCD of some sort available to boot into, do so and then check out your partitions with fdisk -l.

This will show you where your various ubuntu partitions are and ensure that the grub menu is correct.  If not you can mount the appropriate partition and edit the menu.lst file accordingly.


> So in the good old GRUB menu I chose memtest86+. It chugged along for some 54 minutes before I got tired not knowing how long this will go on
This memtest will just continue until you stop it, repeating again and again.  You need to look at the number of errors it shows at the bottom to see if all is OK.

Let us see the output of the fdisk command I mentioned above, and your menu.lst file and it may help us to help you further.

---

### Post by Hendrixski on 2007-07-13
yeah, there's stuff you can do with the liveCD to recover grub... it's not the easiest thing to do in the world, but shouldn't take more than an hour if you know how to use a terminal.

---

### Post by sailor2001 on 2007-07-13
you may have to alt/f2  sudo dpkg-reconfigure -phich xserver-xorg

---

### Post by jingo811 on 2007-07-13
> Let us see the output of the fdisk command I mentioned above, and your menu.lst file and it may help us to help you further.

My partitions is setup somewhat like this.  I have 2 physical harddrives each consisting of 40 Gb.  My first HD have 3 partitions that looks like this:

* Windows XP (10 Gb)
* Program_Files_for_XP (20 Gb)
* Ubuntu 6.06 (10 Gb)

My second HD also have 3 partitions which looks like this:

* Windows XP pagefile (1 Gb)
* Linux swapfile (1 Gb)
* Linux /home (38 Gb)


> 
ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/hda: 41.1 Gb 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
units= cylinders of 16065 * 512= 8225280 bytes

Device ___ Boot ___ Start ___ End ___ Blocks ___ Id ___ System

/dev/hda1 ___ * ___ 1 ___ 1278 ___ 10265503+ ___ c ___ W95 FAT32 (LBA)
/dev/hda2 ___   ___ 1279 ___ 3831 ___ 20506972+ ___ c ___ W95 FAT32 (LBA)
/dev/hda3 ___   ___ 3832 ___ 4998 ___9373927+ ___ 83 ___ Linux


Disk /dev/hda: 41.1 Gb 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
units= cylinders of 16065 * 512= 8225280 bytes

Device ___ Boot ___ Start ___ End ___ Blocks ___ Id ___ System

/dev/hdb1 ___   ___ 1 ___ 131 ___ 1052226 ___ b ___ W95 FAT32
/dev/hdb2 ___   ___ 132 ___261 ___ 1044225 ___ 82 ___ Linux swap / Solaris
/dev/hdb3 ___ ___ 262 ___ 4998 ___ 38049952+ ___ 83 ___ Linux

All that I got from using the Live CD but I had trouble finding my personal menu.lst when I searched for it in terminal I got this.  I looked into the second menu.lst I got from the search but it doesn't look like my original file.

> ubuntu@ubuntu:~$** locate menu.lst**

locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old

/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/doc/grub/examples/menu.lst

It seems like I can't access my installed Linux partitions either nor my Windows partition through Live CD.
So I can't extract my original menu.lst with this method. 
When trying to access all my partitions through Nautilus I got this error message.

> Unable to mount the selected volume.

   error: device /dev/hda3 is not removable
   error: could not execute pmount


PS.
There could be some numeric typos here and there, that's because I have to type so much from my hand written error logs.  I'll fix it later if you pin point some crucial parts that you need better info on!
Otherwise things pretty much looks like this.

---

### Post by jingo811 on 2007-07-13
Also just recently on my second Windows XP boot I think whatever strange thing happened on Ubuntu affected certain files on my Windows partition acording to Window's automatic Checkdisk.  There was some unrepairable damage done on some file in the **Windows/Desktop/Users/something_file** and on my MySQL Server, **mysql folder files.**  I can no longer login into my Databases anymore.

I've been experimenting with WAMP and LAMP learning things I'm still newbie level with Apache stuff.  So** maybe I caught some worm attack? ** Being that I don't fully know how to protect my webserver at this stage :confused: also I had a pretty weakass password for my MySQL root user....

Is this a probable cause or did things simply get ugly for Ubuntu internally?

---

### Post by rfurman24 on 2007-07-13
Maybe someone with more knowledge will come along to verify but it sounds like during your burning session you wrote to much to the temp and fill up your / partition which is more than likely why you can not boot to your system. Can you use a live disk and find the temp folder and delete some files?

---

### Post by jingo811 on 2007-07-14
> Can you use a live disk and find the temp folder and delete some files?

Well when I use Live CD I'm automatically logged in as user **ubuntu@ubuntu** my HD user account is **mike@ubuntu**.  I don't know how to access another user account's partitions and how to mount things?
All my CLI commands notes are being held hostage on my unreachable Linux.

---

### Post by ajgreeny on 2007-07-14
You can mount hard disk partitions from the live CD using sudo mkdir /media/hda3 to make a new directory to mount to then sudo mount /dev/hda3 /media/hda3 -t ext3.  Then using your live disk file manager (nautilus) you can navigate to /boot/grub/menu.lst to find what that says and if needed edit it.

If you need to reinstall grub from the live CD use the following info in the attached txt file.  Good luck, I hope it all works out without the need for a reinstall of the whole system; I'm sure that shouldn't be necessary!

---

### Post by jingo811 on 2007-07-15
Making the directory went fine but mounting my /root partition gave this error message.
```
sudo mkdir /media/hda3
```
```
ubuntu@ubuntu:~$** sudo mount /dev/hda3 /media/hda3 (-t ext3)**

mount: [COLOR="Red"]wrong fs type, bad option, bad superblock on /dev/hda3[/COLOR],
missing codepage or other error
In some case useful info is found in syslog - try
dmesg | tail or so
```

When I tested doing the mount command on my /home partition things worked however.  So all my personal data seems intact but I still can't access /root partitions thus my menu.lst file.
```
sudo mkdir /media/hdb3
```
```
ubuntu@ubuntu:~$ sudo mount /dev/hdb3 /media/hdb3
```

I'm just gonna proceed with your GRUB restore instructions now I'll see you on the other side if things don't pour over onto my Windows XP partition.......

---

### Post by jingo811 on 2007-07-15
I did everything in the Grub restore instructions.  But I still get that error message when starting up Ubuntu :(

> Booting 'Ubuntu, kernel 2.6.15-28-386'
root (hd0,2)
          Filesystem type is ext2f, partition type 0x83
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
          [Linux-bzimage, setup=0x1c00, size=0x157a47]
initrd /boot/initrd.img-2.6.15-28-386
          [Linux-initrd @ 0x1f979000, 0x6761 ce bytes]
savedefault
boot

Uncompressing Linux... Ok, booting the kernel.

mount: Mounting [COLOR="Magenta"]/dev/hda3[/COLOR] on /root failed: Invalid argument
mount: Mounting [COLOR="Magenta"]/root/dev[/COLOR] on /dev/.static.dev failed: No such file or directory
mount: Mounting [COLOR="Magenta"]/sys[/COLOR] on /root/sys failed: No such file or directory
mount: Mounting [COLOR="Magenta"]/proc[/COLOR] on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init






This is some of the info I got from doing the Grub thingy.
```
grub> **find /boot/grub/stage1**
     (hd0,2)
grub>** root (hd0,2)**
     Filesystem type is ext2fs, partition type 0x83
grub>** setup (hd0)**
...
... a bunch of OK messages ...
...
grub>** quit**

```

Now what should I do?
[LIST]
[*]If I do a clean install on /root then my /home partition will be treated as some foreign partition like Windows.  I don't want that, because I tried it once and it's not pretty having to mount your /home everytime you want to listen to your music files, watch some video clips, work on Office and GIMP related stuff, open up some Textfiles, etc. etc.
Last time I did this scenario I ended up with 2 /home partitions!!
[/LIST]

[LIST]
[*]If I DO make a full clean install I still have some personal data to backup to 3 copies which means I would end up breaking my newly installed Ubuntu 6.06 once again.  I don't wanna live a life were you have to re-install your OS everytime you make 3 copies of DVD backups :(
[/LIST]

---

### Post by ajgreeny on 2007-07-15
OK, so you have a grub installed on hda3 (hd0,2) and you put it now on to the mbr of your first hard disk (hd0).  If you still can't get the thing to go then obviously your grub menu must be incorrect in some way ior you don't have the correct linux kernel in your boot folder, so we need to at least have a look at it to see what's going on, and then hopefully go from there.

If you can't get anywhere with mounting from ubuntu try explore2fs in windows.  This is a freeware explorer of all your linux partitions from within windows and I have used it myself.  You cant use it to write to the linux partitions (there are other utilities you can use for that but I've never used or seen any of them so will stick with what I know).  When you start it it will look at your disks and open up an explorer window with all the ext3 partitions showing, and you can then look for /boot/grub/menu.lst and see what it says.

More help than that is beyond me I'm afraid but other people may be able to help you, and if you do need to reinstall the system but keep your home partition, you do not need to end up with two /homes, you need to set hdb3 as /home but then make sure it is not formatted in the install.  Unfortunately you may need the alternate install CD to do that but I'm not certain if that is the case.

Good luck, You'll get there, I'm sure.

---

### Post by LinuxNathan on 2007-07-15
I got the "cannot access tty: jobs turned off" too.

I'd like some help with that.

Jingo, try using Mandriva Linux. It's live CD works, it's install is smooth, and I've NEVER had an error with it in my entire Linuxing life.

- Nathan:)

---

### Post by jingo811 on 2007-07-15
Yeah maybe but I prefer staying with the Ubuntu community the support in here is better than anything I've ever experienced.  
And I don't think anything is wrong with the Ubuntu Live CD it's just saying that it has trouble opening up my HD's /root partition.
Besides most of my stuff and software is connected to the Ubuntu once I switch I'll have to find out how to install things all over again, that took me some months to figure out.  And different distros install things differently.

---

### Post by jingo811 on 2007-07-15
> If you can't get anywhere with mounting from ubuntu try explore2fs in windows.
That's some powerful program!  Here's GRUB by the way :-) But I don't see anything suspicous compared to what things were 1 year ago...

```
[COLOR="Sienna"]#splashimage (hd0,2)/boot/grub/images/GrEdSplash.xpm.gz
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
# array will desync and will not let you boot your system.[/COLOR]
default		0

[COLOR="Sienna"]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).[/COLOR]
timeout		3

[COLOR="Sienna"]## hiddenmenu
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
# kopt=root=/dev/hda3 ro

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##[/COLOR]

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

[COLOR="Sienna"]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.[/COLOR]
title		Other operating systems:
root


[COLOR="Sienna"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1[/COLOR]
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

By the way I didn't write most of the stuff in my GRUB I just used the software GUI GrubEd to change my values.

---

### Post by ajgreeny on 2007-07-15
Just a final check.  Have you got the listed vmlinuz-2.6.15-28-386 in your /boot folder along with the initrd.img-2.6.15-28-386 as well?  These are the two files pointed to by your menu.lst and I just wonder if something has happened to them.

---

### Post by jingo811 on 2007-07-15
I see those 2 files in the /boot folder along with 2 previous versions of the same type of files.  When I try and open them up in Notepad/Wordpad in Windows it just displays a bunch of unreadable things.  When I try and open them up in Gedit it cannot open them and display the contents like in Notepad.

So how do you want me to present those 2 files?
**vmlinuz-2.6.15-28-386**
Is 1.4 Mb
**initrd.img-2.6.15-28-386**
Is 6.5 Mb

---

### Post by ajgreeny on 2007-07-15
I was just querying whether or not they were there, not what they contain, so don't bother trying to open them.  Sorry but my knowledge is exhausted and hopefully someone else will be able to tell you where to go to solve the problem now.

---

### Post by jingo811 on 2007-07-15
ok tnx for you help I couldn't have come this far without you.
Somebody else I need [COLOR="Red"][SIZE="4"]S.O.S [/SIZE][/COLOR]	:-k

---

### Post by Tomosaur on 2007-07-15
GrubEd won't be the cause of your problems here, it seems like something wrong with your disk or your kernel. However, once you get everything working again, you should uninstall your version of GrubEd, and install the latest version. I know you're using an old version because of the very first line in your menu.lst, since the splash image is called something different now, and has several bug fixes for stuff which can cause issues.

---

### Post by jingo811 on 2007-07-15
Nice a celebrity :KS is in da house.

---

### Post by jingo811 on 2007-07-16
I'm no Doctor but it seems like my next logical step would be to revert back to my previous kernel version right?
That is I go from this:
[B]vmlinuz-2.6.15-28-386
initrd.img-2.6.15-28-386[/B]
to this:
[B]vmlinuz-2.6.15-27-386
initrd.img-2.6.15-27-386[/B]



[SIZE="4"]How do I do that?[/SIZE]
Because ever since Synaptic recommended this kernel update and I clicked "OKEY why not".  
[LIST]
[*]My HP Laserjet 1020 stopped working alltogether.
[*]Ripping my CDs to .ogg format produced no files (or maybe I just made some wrong commandlines!)
[*]Now this backing up 3 DVD copies of my personal data makes Ubuntu not work.
[/LIST]
Going back might solve all my troubles in one nice slap, so everything works like normal again?
With minimal extra troubleshooting time and energy.

---

### Post by jingo811 on 2007-07-17
Do I simply change the numbers for my GRUB menu.lst:
[LIST]
[*]title
[*]kernel
[*]initrd
[/LIST]
in order to go back one kernel version is it that simple or is there more to it than meets the eye?
I'm starting to loose my patience soon, my PHP work has been delayed for some week now.  I want to get back to my Linux :(
I'm tired of playing Battlefield2 on my Windows XP all the time.

```
[COLOR="Sienna"]## ## End Default Options ##[/COLOR]

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

[COLOR="Sienna"]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.[/COLOR]
```

---

### Post by ajgreeny on 2007-07-17
It looks as though you uninstalled the 2.6.15-27-386 kernel as it is not shown in your menu.lst but I suppose it is worth trying just in case the grubed program simply removes the grub entry rather than the kernel itself.  So edit to 27 instead of 28 and see if you can now boot again (I suspect not).

Sorry, I've just noticed this in a previous post of yours
>  I see those 2 files in the /boot folder along with 2 previous versions of the same type of files. When I try and open them up in Notepad/Wordpad in Windows it just displays a bunch of unreadable things. When I try and open them up in Gedit it cannot open them and display the contents like in Notepad.
so you do still have another kernel there so it may help.


If that is no help, I don't know if or how you can get back to your previous kernel if you can't boot into ubuntu first.

---

### Post by jingo811 on 2007-07-17
Ok it just slipped my mind I don't have write accees to my /root partition with the** Explore2fs** tool.
However this tool seem to have both read/write access to Linux filesystems when using Windows.
**Ext2 IFS**
But I seem to have trouble mounting it like Ubuntu LiveCD did so I did like the FAQ said regarding my problem.
[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

> E:\temp\programs> **mountdiag K:**

The volume has an Ext2/Ext file system, but the Ext2 IFS 1.10 software did not mount it because there is at least one incompat feature flag set.  
The Ext2 IFS sofware does not implement:
* needs_recovery *

Here we have an Ext3 file system which has transactions left in its journal. A pure Ext2 driver must not access such a volume which is in that state (to prevent data loss!).

You may solve it by mounting it on Linux (which has a kernel with Ext3 support).  Be sure that you cleanly dismount it, before you shutdown Linux.
After that the Ext2 IFS software should be able to access the volume.

E:\temp\programs>

There's no way out for me :confused:
Is my only solution to format /root partition and re-install a fresh Ubuntu and avoid updating my kernel to 2.6.15-28-386 ?  
If it comes to that how do I re-activate my user account MIKE in the new system?  Coz the last time I did a Ubuntu re-install it treated my /home partition like some foreign Windows partition.  Can I just re-create a user named MIKE with the same password to connect it to my old User account's MIKE personal data?

---

### Post by jingo811 on 2007-07-19
It's solved now.  I deleted the old /root and reinstalled a brand new Feisty.  I must say I like it very much especially the partition editor it has become much more robust compared to 6.06 Live CD.
I'm glad 6.06 crashed on me otherwise I would never have made the upgrade to 7.04.

I've learnt my lesson never clean out all the kernel versions on the GRUB list.  Had I never done that I might still be able to gain access to my corrupted /root.

---

