---
title: "How to respond to grub&gt; at startup?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by kpfuser on 2007-05-19
I just installed Ubuntu 7.04 to my hard drive. Upon restarting, I only got to a command line looking like

grub>

It looks like I am supposed to enter a command but which one and why? Where can I find info relating to this?

---

### Post by chamberlain2006 on 2007-05-19
Hmmm.  It seems to me that you don't have any entries.  Could you boot the Live CD, and find the /boot/grub/menu.lst file on your hard drive?  Note: You have to look in the folder on the desktop marked disk or drice or something.

---

### Post by seshomaru samma on 2007-05-19
> Hmmm. It seems to me that you don't have any entries. Could you boot the Live CD, and find the /boot/grub/menu.lst file on your hard drive? Note: You have to look in the folder on the desktop marked disk or drice or something.

and post the output of the command
```
sudo fdisk -l 
```
(from the terminal in the live CD)

---

### Post by kpfuser on 2007-05-19
What entries are we talking about here? Why should I make them and where when there was no prompting whatsoever? By the way, I did find a folder called 'Boot' under 'File System' but it contains files but no subfolders. None of them is named 'Grub.' As for the Desktop, it shows only 'Examples' and 'Install' as subfolders. Needless to say, I got all of the above by running the live CD as requested.

---

### Post by kpfuser on 2007-05-19
The output of the command 

sudo fdisk -l

is as follows:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2289    18386361    7  HPFS/NTFS
/dev/sdc2   *        2290        4752    19784047+  83  Linux
/dev/sdc3            4753        4865      907672+   5  Extended
/dev/sdc5            4753        4865      907641   82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14592   117210208+   e  W95 FAT16 (LBA)

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       14592   117210208+   e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

Does this help?

---

### Post by kpfuser on 2007-05-19
Some literature search that I did while waiting for more enlightenment from this forum points to the fact that GRUB is a boot loader program which must be instructed to load the OS of my choice (Ubuntu in this case).. The recommended procedure is to

   1. Set GRUB's root device to the drive where the OS images are stored with the command root
   2. Load the kernel image with the command kernel
   3. If you need modules, load them with the command module (see module) or modulenounzip
   4. Run the command boot

My problem now is to (1) discover(how?) where Ubuntu is installed and (2) the exact set of commands through which the above 4 steps can be carried out. Can anyone help with this at least?

---

### Post by mahiyar on 2007-05-19
You have 5 hard disks and you should know in which hard disk Ubuntu is installed. From the output of fdisk it seems to be installed in "sdc 2" hard disk. Look at partition types. I guess you could not boot into windows also? Anyway after reboot when you get the grub command line grub> , type this command and enter >find /boot/grub/menu.lst, most probably your out put will be something like (hd2,1). By any chance did you try installing Ubuntu more than once?

p.s: Its a small L in menu.lst

---

### Post by kpfuser on 2007-05-19
I have indeed 5 physical hard disks of which one (SATA) does not show at all and one of the IDE drives appears to be partitioned, judging from listed disk sizes, so we come to 5 virtual disks anyway. Do I know where Ubuntu is installed? Well, sort of. From 'Places' --> 'Home Folder,' I see in the left panel of the File Browser the folder hierarchy Ubuntu, Desktop, File System, Floppy Drive followed by 17.5 GB Volume, 18.9 GB Volume, 37.3 GB Volume, 37.3 GB Volume (2). Of these volumes, the 17.5 and 18.9 GB represent partitions of the same physical hard disk. When these volumes are mounted, their names in File Browser change to disk, disk-1, disk-2. and disk-3 respectively. Listing their contents in File Browser shows that Ubuntu was installed in disk-1 while disk-3 (a combination of two physical disks) contains an original installation of Win2000, which I saw no reason to delete. Of course, the output of the command "sudo fdisk -l" given earlier does not identify the disks in the manner the File Browser does (why?) which makes life harder for me.

To make matters worse, the command "grub> find/boot/grub/menu.lst" was not recognized as a legitimate command by grub and returned an error message. Finally, I installed Ubuntu just once without much more by way of selections other than the absolutely ordinary, i.e., language, time zone, etc. So how can the grub beast be tamed? Incidentally, the live CD works just fine. And yes, I have no clue as to how to boot Win2k either.What next?

---

### Post by kpfuser on 2007-05-19
Well, success at last! After hitting 'Escape' a couple of times at the prompt grub>, grub reverted to booting Ubuntu as the default choice apparently. Oh, why aren't such things explained? So much frustration for something as simple as this! I hope my acquaintance with Ubuntu is a lot friendlier than that with the utterly unfriendly grub.

---

### Post by mahiyar on 2007-05-19
There is a space between "find" and "/grub....", and that is the difference between linux and windows, in windows everything is given on a platter, here you have to learn. I had an ide disk and I spent 15 days searching the web to add another SATA and still managed to land in to problems, but then I was prepared. I must commend your bravery to install Ubuntu with 5 disks and all. Anyway if you want to learn about grub one of the best and easy to understand page is here [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by kpfuser on 2007-05-20
Thank you for replying to a thread that is virtually closed. Thank you for your insights too. With respect to the latter, I think that there is a lot to learn in Windows and most likely even more so in Linux. For the moment, the major difference appears to be that Windows tries to entice newcomers (with ease of initial operability, that is) while Linux tries to scare them off (inadvertently perhaps?). I was not knowingly brave when I took the plunge into Ubuntu. I merely assumed erroneously that if I gave Ubuntu its own entire physical hard disk to occupy, it would confine itself to this hard disk only allowing me to boot other OS's by merely changing the hard disk booting order via a BIOS manipulation at startup. It wasn't to be. Now there is more to learn as a result. I welcome this but I regret the fact that there appears to be no guidance as to what to do, where to go, etc. It seems to me that this would scare a lot of newcomers off once and for all. No one could strike a more decisive blow at Linux in this respect than Linux itself.

---

### Post by drowner on 2007-05-20
I understand your frustration at the difficulties you have encountered, but i have to pick you up on a couple of points:

1. GRUB is not Linux. It is a program that allows you to boot more than one operating system. If windows were less of a megalomaniacal, egocentric, despotistitc operating system, there would be no need for GRUB to be installed.

2. Linux is no more or less easy to learn than windows, in itself. Infact, I was having this exact discussion tonight, you plug a printer into an XP box, it doesnt work, and you say 'bloody stupid printer!'. Plug a printer into a linux box, it doesn't work, and you say 'bloody stupid linux'! People assume what they already know (in most cases Windows) is the right, and easy thing to know.

3. Your error is unusual, and most people do not get these problems.

---

### Post by kpfuser on 2007-05-20
Well, no need to be a Linux defender with me. I am here because I do not like Microsoft, its products, and most of all its practices. I am concerned, however, that others who want to give Linux a try may be scared off and run back to the MS fold for good. With this in mind, does it matter that GRUB is not a part of Ubuntu? I am afraid not! Quite predictably (after the fact for me), it will be the first thing you will see on screen when rebooting after installing Ubuntu, provided, of course, that you decided to try Ubuntu on a machine that has already some version of Windows installed. Is this a rare occurrence? Hardly I would think. What then do you expect one to do when is staring at grub> on screen? Is it too much to expect that some who have never done anything from a DOS command line may panic? What if they know enough to comprehend that some sort of a command is needed but they have no clue as to which one? Or, if they could divine that they must direct GRUB to the folder where the Linux kernel is installed, how could they get there? If they give up at this point and want to boot up Windows, can they do so? Not, I am afraid without managing to get past GRUB. Need I continue? All it would take to avoid this mess would be a set of simple instructions on how to get past the GRUB prompt to get to the GRUB table of bootable OS's from where any idiot can find the way home. And yes, it should be Ubuntu (or Fedora, or Gentoo, or...) who should put these instructions together in as prominent a place as possible. Isn't it disproportionate to issue painstakingly detailed sets of instructions on how to download the iso, verify hashes, burn the image correctly, etc., but fail to give any instructions at all as to what to do when the blinking grub> appears on reboot?

---

### Post by drowner on 2007-05-20
Yeah, but meh

GRUB, as far as i can tell, causes less problems than whatever windows does to the MBR, and at the end of the day, whatever OS people choose to use is up to them

I like linux, if someone else doesn't, thats fine.

---

### Post by kpfuser on 2007-05-20
As I see it, the question is whether GRUB is adequately documented for the sake of the newcomer who runs into it without warning. It is good to know that it causes fewer problems than Windows. With an extra stitch in time it may cause even fewer where it matters most, i.e., to the unsuspecting and unprepared newcomer. As to what OS one likes, I don't think you can:popcorn: find too many people who would disagree on this issue in this forum

---

### Post by mahiyar on 2007-05-20
Before suggesting something I want to ask you this .. are you willing to shuffle your disks, fiddle your bios?

---

### Post by kpfuser on 2007-05-20
I presume you mean to change booting order through BIOS. If I am correct, the answer is yes. If you intend to suggest taking turns to boot each of my 4 hd's first, I have tried it already, the result being that only the present configuration results into booting (GRUB) while all other configurations lead to boot failures.

On the other hand, if you mean to crawl on the floor in order to eviscerate my pc, well, the spirit is willing but my knees are decidedly weak. Finally, if it is something else you have in mind, go ahead and I will see what I can do.

---

### Post by lutherhert on 2007-05-20
Thanks for posting the information. After installing Ubuntu, all my computer's information seems to be intact. I believe my problem is I cannot access the MBR to repair it. I really appreciate the information and research that you have provided and made available. Thank you.  

So far,I am unable to access the listed linux site to obtain Super GRUB. In my situation, it is difficult for me to panick and reformat the disk to re-install the familiiar Win-Xp because I cannot boot to Windows or Ubuntu Linux. I will try to remain calm and develop a plan to repair the MBR. I will use the information you provided to develop the plan. Now I have to look around the Internet to locate Super Grub.

I want to use Linux on the Internet and WIN XP to run the software that I needs windows run and is not yet Linux compatible. 

Thank you again.

---

### Post by confused57 on 2007-05-20
> **lutherhert said:**
> Thanks for posting the information. After installing Ubuntu, all my computer's information seems to be intact. I believe my problem is I cannot access the MBR to repair it. I really appreciate the information and research that you have provided and made available. Thank you.  

So far,I am unable to access the listed linux site to obtain Super GRUB. In my situation, it is difficult for me to panick and reformat the disk to re-install the familiiar Win-Xp because I cannot boot to Windows or Ubuntu Linux. I will try to remain calm and develop a plan to repair the MBR. I will use the information you provided to develop the plan. Now I have to look around the Internet to locate Super Grub.

I want to use Linux on the Internet and WIN XP to run the software that I needs windows run and is not yet Linux compatible. 

Thank you again.

Here's an excellent website that should provide all the info you'll need:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

In the index, you'll see sections on Grub, Super Grub Disk, Uninstalling Ubuntu(repairing Window's IPL code to the mbr), and much more info on bootloaders, mounting filesystems, etc.  The link to download SGD was working 30 seconds ago.  The second link in my signature is also an excellent resource.

---

### Post by kpfuser on 2007-05-20
lutherhert,

No need to panic! All things will clear up eventually. Look at me. I was so utterly frustrated when I rebooted after installing Ubuntu and got an unbudging GRUB prompt. Despite the fact that no instant answer to my problem came through the forum, I managed first to find a work-around (never underestimate the role of sheer luck!) and now with much better info in hand I was able to locate and view /boot/grub/menu.lst and with a little more reading I begin to understand better what it is doing and why and have no doubt that with a little more diagnostic work with my pc's BIOS settings my problem will be put to rest. In your case, if you find SuperGrub, please post the source here for me and others to know. As for your problem, (1) are you sure that it relates to a corrupted MBR? (2) Did you try to access the MBR by booting from the live Ubuntu (or other live Linux distro) CD?

---

### Post by mahiyar on 2007-05-20
Well if the spirit is willing then here we go...
1)Make a back up of everything important on all the disks.
2)Look carefully at the output of fdisk -l. You say that you have one SATA drive and the rest are IDE, but in your output everything is shown as sd_ , which means SATA. DO not worry in my output I have the same anamoly (I wonder why?). From the output there are 5 disks[LIST=1]
[*]SDA -- 40 GB No partition, Windows drive (HPFS/NTFS) + bootable
[*]SDB -- 40 GB No partition, Windows drive. non bootable
[*]SDC -- 40 GB 2 primary + 1 Extended partition[LIST]
[*]First primary is windows drive
[*]Second primary is Linux drive and bootable
[*]Third extended contains swap logical drive.[/LIST] 
[*]SDD & 5. SDE -- Seems to be a single partition drive used to store data.
[*]Now of all these drives before laoding Ubuntu from where did you boot windows, was it from SDA, or SDB, or SDC or is it installed in all three.
[*]If it is just SDA or SDB (I doubt SDB) try **booting windows** from these drives alone.
[*]If you are successful , then I suggest that you dedicate the SDC drive wholly to Ubuntu. Install Ubuntu after removing all other drives (physically). Then add just the windows drive, modify the menu.lst to add the windows lines (go through the site confused57 has given), and then add other drives.
[*]If you want to windows and linux to co-exist on your sdc then again remove all other drives physically, make sdc master and try booting windows. If it goes into grub then grub is installed in your "MBR", remove the grub from your "MBR" by going to the windows recovery console and using command >fixmbr. After successfully going into windows, try installing Ubuntu on the single disk again, after installing Ubuntu you should have no problem in grub, it will correctly guide you to both windows and Ubuntu. After the single disk install is successful try adding other disks one by one.[/LIST]I know thats too long but can think of no better way.

---

### Post by kpfuser on 2007-05-20
Oh my! And I was afraid of a single crawl-under-the-desk session! Thanks for the suggestion but I must pass it up. The way things stand now is that GRUB and I have come to a mutual accommodation, i.e., at the appearance of the prompt, which will remain on screen forever if left alone, I hit TAB and when the list of acceptable GRUB commands appears I hit ESC twice in doubleclick fashion and this takes me to the list of bootable OS's, which will also remain on screen forever and a day if left alone. From there I can boot either Ubuntu or Win2k without further ado. Inelegant but a lot easier on the knees than what you suggest. For the moment, I can live with this. Next goal is to beat GRUB into shape somewhere down the line by way of the keyboard, if at all possible.

---

### Post by drowner on 2007-05-20
> **kpfuser said:**
> Oh my! And I was afraid of a single crawl-under-the-desk session! Thanks for the suggestion but I must pass it up. The way things stand now is that GRUB and I have come to a mutual accommodation, i.e., at the appearance of the prompt, which will remain on screen forever if left alone, I hit TAB and when the list of acceptable GRUB commands appears I hit ESC twice in doubleclick fashion and this takes me to the list of bootable OS's, which will also remain on screen forever and a day if left alone. From there I can boot either Ubuntu or Win2k without further ado. Inelegant but a lot easier on the knees than what you suggest. For the moment, I can live with this. Next goal is to beat GRUB into shape somewhere down the line by way of the keyboard, if at all possible.

Good, a workaround!

Now you can show us the output of GRUB's menu.lst ;)

---

### Post by kpfuser on 2007-05-21
drowner,

Hot off the press especially for you my friend!

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
# kopt=root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Awaiting developments.

PS Hey, I didn't put the smiley's in the output! What is going on?

---

### Post by drowner on 2007-05-21
Don't worry about the smileys, that happens when you type 8 and ) 8) 8)

Your menu.lst looks ok, but im no expert.

Certainly it appears grub is pointing to the right drives... mind you i got mixed up! You got a lot of drives!

---

