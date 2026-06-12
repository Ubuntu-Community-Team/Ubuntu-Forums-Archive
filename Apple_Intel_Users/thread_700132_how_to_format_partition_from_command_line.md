---
title: "how to format partition from command line"
date: 2008-02-18
forum: Apple Intel Users
---

### Post by lex1 on 2008-02-18
i have been following a howto it tells me how to create the partitions but how to for example format a partition with unix and another with fat32 from command line?


lex1:popcorn:

---

### Post by lloyd_b on 2008-02-18
> **lex1 said:**
> i have been following a howto it tells me how to create the partitions but how to for example format a partition with unix and another with fat32 from command line?


lex1:popcorn:

Use the "mkfs" command, specifying the correct FS type:
```
mkfs -t ext3 /dev/hda2
mkfs -t vfat /dev/hda3
```
"ext3" is the current standard for Linux.  "vfat" is (IIRC) "fat32" with support for long filenames.  The "/dev/hda?" entries are examples of the device - substitute with whatever's correct for your system.

Lloyd B.

---

### Post by cyberdork33 on 2008-02-18
while that will format the filesystem, it will not partition the hard drive. I would stick to gparted, otherwise it is 'parted' at the commandline since fdisk and such are not capable of editing the GPT.

---

### Post by lex1 on 2008-02-18
it seems that linux install is more of a challene

i am looking at the ubuntu part of how-to

[http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success](http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success)

and also here for swap(is swap needed with i gig ram)

what does this line mean please?

>I finally got it to work when copying the sda.mbr back to /dev/sda at the time-zone selection screen, before beginning any type of installation, and right after saving changes to the disk.<




also i am going to use the 7.10 cd ubuntu alternative iso


but if you read what roner says in the thread of the howto on 3rd june 2006

at the end he says 

n the meanwhile, I have a "constructive criticism" suggestion: your howto skips some steps that I had to poke around to figure out (well, I am rather newbish). For instance, the path for running lilo (/sbin/lilo), or the necessity to have both the regular live installation CD (for lilo installation) and the alternative one (for installing the actual system and recovering from mishaps). You did mention it, but not clear

this is confusing for me as i am not sure which unbuntu disk to use

lex1

---

### Post by cyberdork33 on 2008-02-18
what you are using is very old (and confusing). Try this one:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

I can't really follow what you are doing. A swap partition is a section of the hard drive that is used by linux from temporarily storing information. Though it is recommended, you do not HAVE to have one.
Basically you should have a EFI partition and an OSX partition on your default hard drive. You need to resize the OSX partition down and create a Linux partition and a Windows partition in the freed space. You will then install Ubuntu to the partition you create for Linux. The Ubuntu LiveCD includes a graphical partition editor that you can use to shrink your OSX partition.

---

### Post by Gen2ly on 2008-02-18
Well said.  1G Ram is plenty, I never went above 512 MB of Ram used on my MacBook, only if you plan a real workhorse laptop will it be needed.  

Also for additional info see the Ubuntu wiki (in the FAQ on the top of the Intel forum page) and the Gentoo Linux Wiki in MacBook.

---

### Post by lex1 on 2008-02-19
Thanks for the howto.

here is my disk 

[B]/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Untitled           121.7 GB  disk0s2
   3:   Microsoft Basic Data                    12.0 GB   disk0s3
   4:   Microsoft Basic Data NO NAME            15.0 GB   disk0s4[/B]

I have win xp on the 15gb partition

I will use the 12gb partition for ubuntu



in the howto you sent me ([http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu))

  when it gets to the unbuntu install it says:

>Boot off of the Ubuntu installation disc. The majority of the Ubuntu >install walkthrough came from this site. [http://bin-false.org/?p=17](http://bin-false.org/?p=17)(dual boot)

Bearing in mind i have windows installed which howto's should i follow?

The reason for asking this  is that in the MBR of windows can be eaily erased this is not mentioned in two howtos mentoned above. below is what is mentoned in the old howto.[http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success](http://ubuntuforums.org/showthread.php?t=187465&highlight=MacBook+triple+boot+success) **is it important? (see below)**

(and Ubuntu in these steps

            Use ALT-F2 to switch to a console, and make a backup of the master boot record:
            Code:
           dd if=/dev/sda of=/tmp/sda.mbr bs=512 count=1

           Switch back to the installer with ALT-F1 and continue the disk partition setup, making    sure only to modify mount points and format the Linux partition, mounting it at /
Here's the partition layout:
/dev/sda1 - EFI boot partition
/dev/sda2 - Mac OS X
/dev/sda3 - Linux partition
/dev/sda4 - Windows XP

           After setting up partitions and networking, but before you continue to install packages,   stop and switch to the console with ALT-F2 and restore the master boot record:
           Code:
     dd if=/tmp/sda.mbr of=/dev/sda


lex1

---

### Post by cyberdork33 on 2008-02-19
> **lex1 said:**
> Bearing in mind i have windows installed which howto's should i follow?First, you don't have to worry about "erasing" the mbr. Grub is fully capable of booting windows. However, I would recommend not overwriting the windows bootloader in the MBR to make things nicer when booting from rEFIt. There is a link in my signature about multi-booting. This gives a lot of information about this.

Making a backup of your MBR, and copying it back is uneccessary for three reasons: 
[LIST=1]
[*]You don't have to overwrite it to install Ubuntu like that is suggesting.
[*]Even if you do overwrite the MBR, Grub can boot windows, so it doesn't hurt you
[*]The Windows install disc has tools to rewrite the windows mbr (without reinstalling windows) if you need to fix it anyway.[/LIST]Follow the how-to I have posted, but near the end of configuring the Ubuntu install (just before it actually starts installing), there is a button near the bottom that says "Advanced". You can click this and set where to install grub to (the Ubuntu partition). This will prevent it from overwriting the MBR. You can checkout the link in my signature for more details about this.

---

### Post by lex1 on 2008-02-19
Thanks for your post.

You in fact answered two questions.

In the howto you posted in tells how to install the lilio boot loader as grub does not work with a triple boot. but i am pleased you confirmed that it does.
I will use the 7.10 live cd 32 bit

In the howto you gave it gives two forms of command one for dapper and one for Edgey
i will use **gutsy gibbon.**
eg
Open Applications-Accessories-Terminal and type  (I assume at this point we are at the desktop)
 sudo parted
 mkfs 3 ext2
 quit

In Edgy, you may need to do this instead:
 sudo mkfs -t ext3 /dev/sda3

Finally in the howto a few lines after what is written above it says:

>When it comes time to set up the partitions, do so manually. Because we only are able to have four primary partitions >setup for the MBR mirror and Apple has already taken the first spot with the EFI System Partition, we will need to only >mount the / drive to /dev/sda3, nothing else, not even a swap.

I**s the above still relevant **? and if so why is this explained now after ubuntu has been installed?


I will do this tomorrow and let you know how it turns out.

once again many thanks

lex1:)

---

### Post by cyberdork33 on 2008-02-19
> **lex1 said:**
> In the howto you posted in tells how to install the lilio boot loader as grub does not work with a triple boot. but i am pleased you confirmed that it does.
I will use the 7.10 live cd 32 bit
That is correct, there was a problem in grub before but it has since been resolved. Lilo will also work.

> **lex1 said:**
>  In the howto you gave it gives two forms of command one for dapper and one for Edgey
i will use **gutsy gibbon.**
eg
Open Applications-Accessories-Terminal and type  (I assume at this point we are at the desktop)
 sudo parted
 mkfs 3 ext2
 quit

In Edgy, you may need to do this instead:
 sudo mkfs -t ext3 /dev/sda3

Finally in the howto a few lines after what is written above it says:

>When it comes time to set up the partitions, do so manually. Because we only are able to have four primary partitions >setup for the MBR mirror and Apple has already taken the first spot with the EFI System Partition, we will need to only >mount the / drive to /dev/sda3, nothing else, not even a swap.

I**s the above still relevant **? and if so why is this explained now after ubuntu has been installed? You really don't need to do either of these if you have already adjusted the size of your OSX partition. In fact, I think you had mentioned that you already created the partitions you want for Windows and Ubuntu. That will be fine. Gparted is a gui front-end for parted, so that is essentially the same command. There is a 4 partition limitation (for windows). You can put a swap after 4 (idk why it says that). The line about setting up partitions manually still applies because there is really not a valid option for you to choose to let it do it automatically. This is part of the installation process. It will ask you how you would like to partition. Choose "manually". You can then tell Ubuntu how to mount and use the partitions on the hard drive. You do not need to mount the EFI partition, but you will probably want to have your windows partition mounted automatically, so you can add that. You really just need to set your ext3 partition (that you partitioned previously) as /. I don't know how the swap might affect Windows, so if it says not to use one, I wouldn't (maybe someone else can give better advice).

---

### Post by lex1 on 2008-02-20
Thanks for your post.

Ubuntu got to the live screen on the 3rd attempt something about the diplay being shutdown 
about 6 times in the last 90 secouns etc etc . well on the third attempt it srated in to the live cd.

Just befoe i go ahead i just want clear up three points

a)  In the live cd i can format the partition to ext3? is there anything
else that needs to be done at this point before i clikck on the install disk?

b)  You mentioned in a ;prevoius post that just before it actually starts installing there is a button 
"advanced" and i can set this to install grub in the ubuntu partition in my case sda3,
from what I remember from installing ubuntu before on my labtop after the paritioning screen
it starts to install the core base system. Sorry to be a thickhead but is this where the advanced button will be**?**

c) In the partition i choose manual ok, 

1) do not mount EFI
2)add windows to auto mount
3)mount the ext3 partition as /


I think thats it.

many thanks for your detailed explaination your a star.


lex1:)

---

### Post by cyberdork33 on 2008-02-20
> **lex1 said:**
> a)  In the live cd i can format the partition to ext3? is there anything else that needs to be done at this point before i clikck on the install disk?Judging from your previous post, no. select sda in gparted, format to ext3, and go. You really don't even have to do that as you can format in the installer too.

> **lex1 said:**
>  b)  You mentioned in a ;prevoius post that just before it actually starts installing there is a button "advanced" and i can set this to install grub in the ubuntu partition in my case sda3, from what I remember from installing ubuntu before on my labtop after the paritioning screen it starts to install the core base system. Sorry to be a thickhead but is this where the advanced button will be? After selecting the partition to install and mount, etc, the installer takes you through some screens where you set the time, create a user, etc. At some point, The installer will present a summary of what it is going to do (where it is installing, settings, etc, and there is a Button labeled advanced at the bottom, just look for it. It is not a big issue anyway as it won't break anything if you don't change it.

> **lex1 said:**
>  c) In the partition i choose manual ok, 

1)do not mount EFI
2)add windows to auto mount
3)mount the ext3 partition as /
It will likely try to set the EFI partition as automounting automatically, so you will have to select it, and tell it "do not use this partition". If your windows is ntfs, you might not want to automount it here, and instead use ntfs-3g later. Also, after you get all the partition stuff situated, and you click next or whatever, it may give you an error message about the FATs not being the right size or something. Just ignore that, as it refers to the EFI partition which you are not using anyway.

---

### Post by lex1 on 2008-02-20
Thanks for your post and your help on this install.

I have windows on fat32 so auto install should be ok.

I will finish it tommorow.

lex1:)

---

### Post by lex1 on 2008-02-21
There are a  few issues that i may need to address

I am in the live cd. thought would stay here untill everything is ok.

OK i was asked where grub needs to go it suggested hd0 i changed that to hd2
i based this on my limited knowleage that hd0 was efi partition?
perhaos it should have been sda3?

gparted gui reads:
/dev/sda3 (then a lock symbol) ext3 /target  12.00g(size)   2.38g(used)  9.62g(unsued)


i choose efi do not use this partition,

On finishing the install it gave fatal error for grub here is the log below.

Feb 21 10:55:54 ubuntu grub-installer: info: Installing grub on '(hd2)'
Feb 21 10:55:54 ubuntu grub-installer: info: grub-install supports --no-floppy
Feb 21 10:55:54 ubuntu grub-installer: info: Running chroot /target grub-install  --no-floppy "(hd2)"
Feb 21 10:55:54 ubuntu grub-installer: Probing devices to guess BIOS drives. This may take a long time.
Feb 21 10:55:54 ubuntu grub-installer: Searching for GRUB installation directory ... 
Feb 21 10:55:54 ubuntu grub-installer: found: /boot/grub
Feb 21 10:55:54 ubuntu grub-installer: Due to a bug in xfs_freeze, the following command might produce a segmentation
Feb 21 10:55:54 ubuntu grub-installer: fault when /boot/grub is not in an XFS filesystem. This error is harmless and
Feb 21 10:55:54 ubuntu grub-installer: can be ignored.
Feb 21 10:55:54 ubuntu grub-installer: xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Feb 21 10:55:55 ubuntu grub-installer: 
Feb 21 10:55:55 ubuntu grub-installer:        [ Minimal BASH-like line editing is supported.   For
Feb 21 10:55:55 ubuntu grub-installer:          the   first   word,  TAB  lists  possible  command
Feb 21 10:55:55 ubuntu grub-installer:          completions.  Anywhere else TAB lists the possible
Feb 21 10:55:55 ubuntu grub-installer:          completions of a device/filename. ]
Feb 21 10:55:55 ubuntu grub-installer: grub> root (hd0,2)
Feb 21 10:55:55 ubuntu grub-installer: grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd2)
Feb 21 10:55:55 ubuntu grub-installer:  Checking if "/boot/grub/stage1" exists... yes
Feb 21 10:55:55 ubuntu grub-installer:  Checking if "/boot/grub/stage2" exists... yes
Feb 21 10:55:55 ubuntu grub-installer:  Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Feb 21 10:55:55 ubuntu grub-installer:  Running "embed /boot/grub/e2fs_stage1_5 (hd2)"... failed (this is not fatal)
Feb 21 10:55:55 ubuntu grub-installer:  Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Feb 21 10:55:55 ubuntu grub-installer:  Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd2) /boot/grub/stage2 p /boot/grub/menu.lst "... failed
Feb 21 10:55:55 ubuntu grub-installer: 
Feb 21 10:55:55 ubuntu grub-installer: Error 21: Selected disk does not exist
Feb 21 10:55:55 ubuntu grub-installer: grub> quit
Feb 21 10:55:55 ubuntu grub-installer: error: Running 'grub-install  --no-floppy "(hd2)"' failed.
Feb 21 10:56:35 ubuntu python: log-output -t ubiquity umount /target/cdrom


it i have made a mistake how can i make it ok?

thanks

lex1:)

ps whats the root password in a live cd?

---

### Post by cyberdork33 on 2008-02-21
> **lex1 said:**
> OK i was asked where grub needs to go it suggested hd0 i changed that to hd2
i based this on my limited knowleage that hd0 was efi partition?
perhaos it should have been sda3? No, you told it to install to the MBR on the 3rd hard drive, which does not exist. 
```
 Feb 21 10:55:55 ubuntu grub-installer: Error 21: Selected disk does not exist
```Please read the tutorial for multi-booting in my signature. It will explain how to set the correct partition. You will not need to reinstall Ubuntu completely, just grub. You can do this from the livecd in a terminal. 

> ps whats the root password in a live cd?No idea. It is not a known, set password on purpose for security reasons. you can run commands with root privileges by using 'sudo'. Additionally, you can become root with 'sudo su'.

---

### Post by lex1 on 2008-02-21
Thanks for your post

I think it will be better for me to delete the ext3 partition which has a lock attached and install
again as I do not fully understand how to do it from the command line.(how to remove the lock in gparted?)

what would be the correct entry to install grub when i clicked the advanced tab.


lex1:)

---

### Post by cyberdork33 on 2008-02-21
> **lex1 said:**
> I think it will be better for me to delete the ext3 partition which has a lock attached and install again as I do not fully understand how to do it from the command line. (how to remove the lock in gparted?)
That has no bearing, you do not need to use gparted anymore.

> **lex1 said:**
>  what would be the correct entry to install grub when i clicked the advanced tab.You do not need to reinstall, the system is already installed. You just need to install grub. Start the LiveCD, Open a terminal, and follow the direction in my how to. It tells you EXACTLY what commands to use, step-by-step.
[http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/#InstallGrubManually](http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/#InstallGrubManually)

---

### Post by lex1 on 2008-02-21
Well it may seem step by step to you but for me its more difficult, me and the command line seem to have problems.

lex1:)

---

### Post by cyberdork33 on 2008-02-21
> **lex1 said:**
> Well it may seem step by step to you but for me its more difficult, me and the command line seem to have problems.
You will always have trouble in Linux if you cannot use the commandline.

---

### Post by lex1 on 2008-02-21
see post 21 in this thread

lex1

---

### Post by lex1 on 2008-02-21
i typed sudo grub in the live cd

i got:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,2)


so based on the above should i now finish with:

grub> root (hd0,2)

grub> setup (hd0,2)

grub> quit


lex1

---

### Post by cyberdork33 on 2008-02-21
sounds good.

---

### Post by lex1 on 2008-02-21
After installing grub i then came out of the live CD and restarted

there were three icons on restart

apple, ubuntu and windows

when i choose the ubuntu i got this:


Grub loading Stage 2

[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

grub>


kex1:popcorn:

---

### Post by cyberdork33 on 2008-02-21
It looks like none of the rest of grub installed (the part on the disk, files, configuration, etc) so you might have to reinstall everything afterall. You did the part at the commandline right though!

---

### Post by lex1 on 2008-02-22
ok I reinstalled and it seems to be working now.

I have the windows HD on my OSX deasktop and with the help of the Ext2fs package ubuntu DH appears

it would be nice if the OSX HD could appear on linux desktop to. that way if ubuntu was on i could
ssh into it, i can maybe do it into MAC osx but I am more failiar with the linux command line
although you would not think so.






once again many thanks for your help on this project


lex1






lex1

---

### Post by cyberdork33 on 2008-02-22
If you are saying you want to mount your OSX partition in linux so that you can access files, then:
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

You have to disable journaling on the HFS+ (OS X) filesystem. Then add an entry to your /etc/fstab to mount the partition automatically at boot.

There are some limitations about accessing files though because permissions are handled the same way on Linux as in OS X. It can get rather complicated. There are quite a few topics about this in the forum.

---

### Post by lex1 on 2008-02-22
Its seems that by disableing journaling in OSX then this will work under linux .
the howto seems to have many points.


whats the latest bottom line with working out of ubuntu 


.lex1

---

### Post by cyberdork33 on 2008-02-22
> **lex1 said:**
> Its seems that by disableing journaling in OSX then this will work under linux .
the howto seems to have many points.


whats the latest bottom line with working out of ubuntu I don't really know what you are asking. HFS+ support is in the kernel, so there is no extra software to install or anything. You just need to disable journaling in OSX, then mount the partition. The link shows how to do both.

---

### Post by lex1 on 2008-02-22
I will print the howto off and take a closer look.
can you just explain what you mean by mount the partition? which partition.

lex1:)

ps how come vmware fusion if you load windows it also loads the OSX folder with complete acess to OSX from windows any reason why i cannot do that?

---

### Post by cyberdork33 on 2008-02-22
> **lex1 said:**
> I will print the howto off and take a closer look.
can you just explain what you mean by mount the partition? which partition.

lex1:)

ps how come vmware fusion if you load windows it also loads the OSX folder with complete acess to OSX from windows any reason why i cannot do that?I mean use the mount command as in the how to, or add the proper entry to fstab. and you mount whatever partition is your OSX partition, (which I am assuming is /dev/sda2)

Fusion is a VM running in OSX, so it uses OSX to actually access the files using a special driver in the VM. It "mounts" a pseudo-partition in Ubuntu.

---

### Post by lex1 on 2008-02-23
Thanks for your post

I notice i get an error message if i copy large files from OSX to windows not sure about ubuntu
i think i need to reformat with hfs extended journal flie system

in grunb in ubuntu the keys on my keybord do nt work. the first entry in grub is the correct
entry and loads gutsy mem test windows xp are there also. windows i can get from the selection
as mac starts up.

:popcorn:
lex1

---

