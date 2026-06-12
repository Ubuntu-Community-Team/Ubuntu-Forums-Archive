---
title: "kernel update overwrites menu.lst with wrong root partition"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Bigbluecat on 2006-09-30
Hi all,

I'm dual booting with WinXP on separate hard drives.

WinXP is on hd0,0 and Ubunutu is on hd2,0 (in grub speak) - this is /dev/sda1.

So I'm still a total noob with only a few hours Ubuntu under my belt. I took the option offered to me to upgrade the kernel from 2.6.15.26.386 to 2.6.15.27.386.

When I did this I could no longer boot into an linux kernel (even recovery).

I did some invesitgation with grub CLI and tried to manually boot the kernels.

My original v26 kernel would not boot. It complained of missing libraries. I'm sorry I did not get a detailed note of this (it seemed to be looking for v27 libraries).

I then manually booted the v27 kernel successfully. I took a look at menu.lst and all my linux entires had been re-written with hd0,0 as the root. No wonder I could not boot.

Corrected this and now booting again to v27. I'll go back and see if v26 will boot.

My question is how can I stop the kernel update process from re-writing menu.lst with incorrect root partition information. It's kind of annoying.

Looking for some insightful comments to prevent future frustration :-k

---

### Post by bulldog on 2006-09-30
Well,you had some bad luck I suppose.

Did the upgrade a while a go and only broke X-server :D 

No probs with the menu.lst,so think everybody gets a fair amount of trouble :D 

But don't think you can do anything else,and your option is not to update.........but if that's a 'solution' ](*,)

---

### Post by petri on 2006-09-30
Could you post you menu.lst here. I think there is something wrong with groot :confused:



EDIT: and **sudo fdisk -l** too

---

### Post by Bigbluecat on 2006-09-30
I'm not sure about bad luck here. It seems to me that the install and update process does not cope well with a dual drive system.

When I first installed I had to adjust menu.lst to point at the correct root partitions also.

Maybe I should avoid using grub as the MBR and just use the bios to switch between WinXP and Ubuntu. That way my /dev/sda1 would look like hd0,0 when I boot into linux and all may be happy. Just don't really like that solution.:rolleyes:

I did ignore the kernel update for a while but what the hey - I'm here to learn a bit as well. And the kernel update must be there for a reason

---

### Post by Bigbluecat on 2006-09-30
Here's my menu.lst

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
default         6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=/dev/sda1 ro

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
# updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


With your comment I just notice the groot area commented out. If I set this to (hd2,0) then this may solve my problem - correct?

---

### Post by petri on 2006-09-30
do not comment it out... sudo fdisk -l ?

---

### Post by Bigbluecat on 2006-09-30
Here's the result from sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30023   241159716   83  Linux
/dev/sda2           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       11473    61440592+   f  W95 Ext'd (LBA)
/dev/sdb3           11474       19457    64131480    7  HPFS/NTFS
/dev/sdb5            3825       11473    61440561    7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163927556096 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19928   160071628+   7  HPFS/NTFS

---

### Post by petri on 2006-09-30
Have you been fiddeling in BIOS already? :mrgreen: 


Now you have Ubuntu on sda1 and windows on sdb1. In Grub language Ubuntu on hd(0,0) and windows on hd(2,0). 

The problem you describe shouldn't be a grub problem but the update problem...

the #groot(0,0) should now be as it is. If Ubuntu would have been on hd(2,0) then #groot(2,0). I hope I can keep it together now 8) 

You can leave it as it is and paste this in terminal
```
sudo update-grub
```
Then you should have grub working. If not feel free to yell at me :rolleyes:

---

### Post by Bigbluecat on 2006-09-30
Thanks Petri,

I'll change groot to hd(2,0).

I have not fiddled the bios. I steered clear of this and generally try not to fiddle. Although I did notice as you did that my windows partition was /dev/sdb and yet this is hd(0,0) accoring to grub CLI.

My wife has played with the bios though and installed the Ubuntu disk for me while I was travelling. Although I don't think we changed anything with the way the windows drive was connected.

I'll make a backup of 
of menu.lst and change the groot lines.

Thanks for your help.

---

### Post by petri on 2006-09-30
NO KEEP YOUR #groot(0,0) :-#

Your grub folder is there!

EDIT:
Cable from motherboard has two connectors(?) sorry my english :rolleyes: 

The frist one in the middle is for SLAVE and sdb* the second one, 
on the another end of the cable is for MASTER sda*

That is if your harddisks are configured as "Cable select".

---

### Post by Bigbluecat on 2006-09-30
I should read more carefully.:rolleyes:

grub is working at the moment so what will sudo updtate-grub do to my system?

Also when I use the grub command line interface find /vmlinuz definitely returns hd(2,0) as the root partition.

I'm not on my linux machine at the moment. We had a thunderstorm pass over and I have not got the UPS running yet (we are prone to power cuts out here in the sticks). So I shut down to be safe.

---

### Post by petri on 2006-09-30
```
sudo update-grub
``` fixes your messed up grub which you apparently don't have right now so just forget it for now :mrgreen: 

It goes through your harddrives and writes every OS on menu.lst so if you have done som changes in menu.lst they will be gone. Therefore is a good thing to back it up first like this ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

EDIT:
btw you do know you can copy by highlighting with your left mousebutton and paste it with clicking your scrollwheel? Then you will not do typos like this > grub is working at the moment so what will **sudo updtate-grub** do to my system? in terminal. ;)

---

### Post by Bigbluecat on 2006-09-30
Hi Petri,

Tak. (sp??)

I'm learning slowly. Don't get much time to play. And your English is great. Much better than my non existent Swedish.

I have a feeling that the WinXP drive has been connected up as /dev/sdb from the beginning. The PC was custom built by a friend and we had no need to look until I wanted to try Ubuntu and my wife insisted on a separate drive to try to protect her WinXP.

It's probably selected as primary boot in the bios and that is causing some confusion.

my /boot/grub files are definitely on hd(2,0) according to grubs CLI. I have written grubs IPL to the MBR on hd(0,0) which happens to be /dev/sdb1.

Just done a little more reseacrh on the following page:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Hermans guides were a big help in my initial install. It looks like there are two perameters in menu.lst that come into play.

kopt in my case I think should be:
kopt=root=/dev/sda1 ro

This is for kernel options and is applied to all kernels in my menu.lst

And groot which specifies where kernels are installed and should be where my /boot resides. In my case hd(2,0)

groot=(hd2,0)

I'm going to research a bit more before doing anything. I'm actuallly reasonably comfortbale doing a manual kernel boot now if it all goes pear shaped and my WinXP is protected.

Learning more all the time.:-D

---

### Post by petri on 2006-09-30
Yes Herman is the man :) another good guide is [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Have you tried Reinstall grub with Hermans guide [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Thanks to LiveCD there is always a possibility to rescue Ubuntu instead of reinstalling as in windows :rolleyes: 

P.S. By now you probably know more about grub than I do. :mrgreen:

EDIT: At [http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST) you can read about the automatic update of menu.lst. That should not be your problem anyway because you have only one Ubuntu/Linux installation. I have four of them and everyone has it's own /boot and grub and menu.lst. When their kernels gets updated they mess my grub up. It happens not so often so I haven't fixed it. Quite. :rolleyes: :mrgreen:

---

### Post by Bigbluecat on 2006-09-30
Thanks for the help Petri. 

My grub is working so I don't need to reinstall it. I'll research what the kernel update does to menu.lst. 

Herman's pages are a good starting point.

---

### Post by Herman on 2006-09-30
Hello Bigbluecat petri and other freinds,
>  kopt in my case I think should be:
kopt=root=/dev/sda1 ro
This is for kernel options and is applied to all kernels in my menu.lst
And groot which specifies where kernels are installed and should be where my /boot resides. In my case hd(2,0)
groot=(hd2,0)
 I think with in your particular set-up, Bigbluecat, the above will most likely prove to be correct (for you). 
They say that 'two wrongs do not make a right', but we all know that three left hand turns do add up to a right-hand turn, :D. He, he. So I think that editing your menu.lst to match the way your computer has been set up will prove to be the best solution. Basically, whatever causes your computer to behave the way you would like it to is the correct answer. :D

petri, 
When we have more than one Linux distro running Grub in the same computer, each successive Linux installation normally detects the preceding ones and adds them automatically to the newest Linux's menu.lst, which will normally be then written to MBR. That is wonderful for most of us. We will have things set up well enough  that way, but it isn't the best way to multiple boot Linux systems.
I'll let you in on a better way, one that doesn't seem to be very well known.  I use the 'configfile' command.  I prefer to re-install Grub from my oldest and most well seasoned Ubuntu installation to MBR after I install another system, and keep my original install as my main installation, whose grub menu the others can boot from, and add the new entries myself.
The commands for booting the other Linux systems that are given automatically are not the best ones for multiple booting other Linuxes. The problem is, those commands boot a specific kernel and ramdisk only. While the main system will have its grub entries updated when a new kernel is installed, and update-grub is run automagically, it just copies the other system's entries to the new menu.lst that is generated. So we are still booting the other systems by their possibly older kernels.
A better way to boot your other Linuxes, is by their own configfiles (menu.lst)s, with a '**configfile**' command in the operating system entry for them. That way each operating system can update it's own menu.lst independantly, as and when needed. You will be booting each one through their own grub menu, so you will always be booting the most up to date kernels. For example,
>                                          ## ## End Default Options ##
                                              
                                        title        Ubuntu, kernel 2.6.15-25-386
                                        root        (hd0,1)
                                        kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
                                        initrd        /boot/initrd.img-2.6.15-25-386
                                        savedefault
                                        boot
                                              
                                        title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
                                        root        (hd0,1)
                                        kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
                                        initrd        /boot/initrd.img-2.6.15-25-386
                                        boot
                                              
                                        title        Ubuntu, memtest86+
                                        root        (hd0,1)
                                        kernel        /boot/memtest86+.bin 
                                        boot
                                              
                                        ### END DEBIAN AUTOMAGIC KERNELS LIST
                                              
                                        # This is a divider, added to separate the menu items below from the Debian
                                        # ones.
                                        title        Other operating systems:
                                        root
                                              
                                              
                                        # This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/hda6
                                        title        Ubuntu EXPERIMENTAL INSTALL configfile boot
configfile       (hd0,5)/boot/grub/menu.lst


                                        # This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/hda8
                                         title        damn small linux configfile boot
configfile       (hd0,7)/boot/grub/menu.lst
EDIT, You don't need to delete your existing, (working, trusted) grub entires for your other Linuxes if you aren't sure. Just test a 'configfile' boot entry by adding one to try it out first, without deleting anything else. Once you have tried it, I think you will prefer it though, and want to convert to them. :D

On a related subject, I tried an experiment and deleted everything out of my /boot directory except for my kernel and initrd.img file, to see if I could still boot my system without any of those other files. I found out that my system would still boot up perfectly from CLI Grub using the commands for booting the kernel and initrd.img directly.
Then, I found that Ubuntu can regenerate all of the necessary files for booting except for the menu.lst with the 'sudo grub-install /dev/hda' command, providing I make an empty /boot/grub directory for it first. (sudo mkdir /boot/grub). The 'sudo update-grub' command generates a new menu.lst file. If there is another menu.lst file already, it copies the other operating system's boot entries information from that one. If there is no other menu.lst in existence, the new one will only have entries for the operating system which the new grub menu belongs to. We can add others manually if we wish. 
I just though you might find that story interesting.
Regards, Herman :D

---

### Post by petri on 2006-10-01
Thanks Herman, I see you've been there what I just finally succeeded to accomplish yesterday with this guide [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
and the third alternative which was ```
title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst
```

That gives me a chance to make up my mind which OS to boot and always have a chance to go to an another menu.lst.

Why do I get the feeling that you have something to do with the *hermanzone*? :rolleyes:   Is it your name or you coming from Australia or the way you wrote? :mrgreen:


EDIT: I have to stop posting to this forum now, I have reached **Way Too Much Ubuntu** 8) I always liked the sound of that. :rolleyes:

---

### Post by Bigbluecat on 2006-10-01
Thanks Herman,

Nice ot have confirmation.

I know it's a bt screwy but:

Rule #1 - if it works leave it alone.

Seems I understand menu.lst and grub better than I do drive cables and bios. I could go and switch the cables and change the bios but probably more chance of getting something wrong that way. 

I'll see what happens when dist-upgrade comes along. That should be interesting.:p

---

### Post by Herman on 2006-10-02
>  I'll see what happens when dist-upgrade comes along. That should be interesting Bigbluecat, Yes, just give it some time. 

I have tried dist-upgrading, it works well. However, what I prefer to do when each more modern edition of Ubuntu is released is to just keep my existing version and add the newer one after it on my hard disk. I still have my old 'Breezy' install in this computer, and I can always take a trip down memory lane by booting it. I resized it to a smaller size with GParted liveCD, so it doesn't take up very much disk space. 
I like to begin each new edition with a clean slate,as a fresh install, and start accumulating information in that all over again. 
But that's just a matter for personal preference. It is perhaps a slightly more cautious and conservative approach, too.:D

petri     > Thanks Herman, I see you've been there what I just finally succeeded to accomplish yesterday with this guide [http://users.bigpond.net.au/hermanzo..._Linux_Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
and the third alternative which was (configfile boot) That's good, petri, that's my favorite method for multiple booting now too. :D
>  Why do I get the feeling that you have something to do with the *hermanzone*? :rolleyes:   Is it your name or you coming from Australia or the way you wrote? :mrgreen: Yes, that's me, I'm the villian! (he-he) :D
Regards, Herman :D

---

### Post by Bigbluecat on 2006-10-02
Thanks for the suggestion Herman. I might just create a partition for the new upgrade.

I was going to watch the forums for a while after the official Edgy release anyway. A lot can be done in beta testing but once a full release is done and it gets onto more hardware and in more hands more issues can be found.

As I'm just starting out I'll defer to others have this fun for now. And in any case a separate clean install on a new partition would give me the chance to play while still keeping my working Dapper system in place. I have plenty of space on my drive.

---

### Post by petri on 2006-10-03
> **Herman said:**
> 
 Yes, that's me, I'm the villian! (he-he) :D
Regards, Herman :D

Great site you've made! Thanks.

---

### Post by jaktar on 2008-02-22
I hate to resurrect such an old post but...I've been having this problem on my XP/7.10 dual boot.  Every time I do a kernel update I have to go back and edit menu.lst to correctly point at (0,1).  I have been having this problem since initial install.  

I'm confused why grub wants to point to (2,1) yet linux is on (0,1).  Any help would be appreciated.  Here is the result of mount and my menu.lst.

mount
<quote>
john@john-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/D2ScrewyDrive type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/D3Treehugger type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.1.2/C on /media/kaijuc type smbfs (rw)
//192.168.1.2/F on /media/kaijuf type smbfs (rw)
/dev/sda1 on /media/D1Pikachu type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
</quote>

menu.lst (comment lines removed)
<quote>
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=510a4c1e-b7d5-41de-9a21-7f5a64e0ff28 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=510a4c1e-b7d5-41de-9a21-7f5a64e0ff28 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
</quote>

---

