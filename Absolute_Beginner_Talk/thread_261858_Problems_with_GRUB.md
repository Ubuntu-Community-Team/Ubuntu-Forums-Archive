---
title: "Problems with GRUB"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2006-09-20
Hi everyone. I'm new to linux and im having some problems with GRUB in particular. I had everything running in a multiboot set up for about 2 weeks when i managed to get a rather nasty virus on my primary windows xp parition and ended up having to reformat it. Now i have 3 hard drives, one with xp one with ubuntu and one used for storage formated with ntfs and fat32. Once i installed xp on the seperate hard drive grub stopped working. So i looked in the forums and found how to start up GRUB again. But it still maintained an old boot table making it impossible to actaully boot my windows partition. How would i go about fixing this problem with out having to reinstall either operating systems? I'm not new to computers but i am rather in the dark when it comes to linux and GRUB. Any help is much appreciated. :(

---

### Post by catlett on 2006-09-20
As long as you are getting to the grub menu, you can enter the boot instruction manually. Which means if you know what partition windows or ubuntu is on, you can enter that instead of what is on the menu. If you knew the windows one it would actually be the easier of the 2. 
If you don't, boot to the ubuntu live cd. Run
```
sudo fdisk -l
```That will tell you the partitions. If you are unsure, post them.
Next you will have to mount ubuntu's partition and edit grub from there.
Again if you need to use the live cd i'll give you the mount commands etc but first post which situation your in. Do you know the partition windows or ubuntu is installed on?

---

### Post by SpiceWeasel on 2006-09-20
My xp partition is sda1, its a SATA hard drive if that matters as far as booting is concerned, which i've experinced it does. When i had everything multibooting before the virus i had to set my bios to boot first from a different hard drive to actaully have GRUB initialize, but thats another problem and i think i solved it. That was when i had both operating systems on the SATA and im not doing that this time round so it shouldnt matter.


*EDIT* I also forgot to mention that due to a disagreement between norton and my SATA hard drive, the only way ive been able to get it to boot now is using GRUB so atm i cant really access my XP drive other than threw linux which is read only if im right.

---

### Post by catlett on 2006-09-20
When you get to the grub menu where it lists the OSs, press ```
c
``` That will get you a command line which is actually the grub shell. It will look like this 
```
grub>
```At that prompt you can enter lines like you have in your menu list. So to boot tp XP (assuming the sda is your master drive) enter these line at the grub command line. I am going to write grub> just so you know it is a new line but don't enter it as a command
Alright, enter ```
c
```
When you get to grub> enter these lines
```
grub>root  (hd0,0)
```
press enter
```
grub>chainloader +1
```
press enter
```
grub>boot
```
If all is right it will boot windows. If it doesn't, post the errors.

If you get into windows, do here and download the ext2 driver [http://www.fs-driver.org/](http://www.fs-driver.org/) Install it, give ubuntu's drive a drive letter through it's interface "IFS Drives" found as an option in windows control panel (it is easiest to find when you switch to classic view)
Once you can access ubuntu's partition, go to the boot folder and then into the grub folder. Find the file menu.lst and open it. That holds the grub menu. You can edit in the correct partitions and save it so the next boot grub will have the correct entries. Post if you need any help wioth the partition labels.

---

### Post by SpiceWeasel on 2006-09-20
I entered the commands and as soon as i entered "root (hd0,0)" it returned the error "unkown file system 0xf"

---

### Post by catlett on 2006-09-20
Is the sda your first/master partition? Try one more thing, you can use rootnoverify instead of root. It keeps grub from trying to mount the partition and tells grub to just send the boot to that point. Try this ans see if it gets the same error.
boot to menu ans enter c
```
grub>rootnoverify (hd0,0)
grub>chainloader +1
grub>boot
```
If that doesn't woprk, we cab try to boot ubuntu. It just takes a little more homework. You need to knwo the kernel and image etc. Not a hard or imposssible thing but is is a bit of a process.

---

### Post by SpiceWeasel on 2006-09-20
sda1 is the only partition on the drive and the drive is set as a master. I tryed what you said and when i entered the boot command the system locked up. :(


*EDIT* the exact output of the sudo fdisk command is

E.g.: fdisk /dev/hda   (for the first IDE disk)
  or: fdisk /dev/sdc   (for the third SCSI disk)
  or: fdisk /dev/eda   (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0   (for RAID devices)

---

### Post by catlett on 2006-09-20
The issue with windows is finding which drive it is on according to grub. Grub lists drives as 0,1,2,3. 0 being the first drive, 1 being the second drive etc.
So are you sure windows' drive sda is the first i.e. 0 to grub.
The other option is to try and boot ubuntu. To do this we need to know the kernel and image. The lines you need to enter are going to look something like this. 
My grub menu.lst for ubuntu
```
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-686 root=/dev/hda5 ro quiet splash
initrd          /initrd.img-2.6.15-26-686
savedefault
boot

```To do it the way you nedd to, it would be entered like this,
boot to the menu and enter c

```
grub>root            (hd0,0)
grub>kernel          /vmlinuz-2.6.15-26-686 root=/dev/hda5 ro quiet splash
grub>initrd          /initrd.img-2.6.15-26-686
grub>boot
```
The issue is, what partition ubuntu is on and what version kernel are you using.
For this you need to boot to the ubuntu live cd. Enter ```
sudo fdisk -l

```To find the linux partition that grub is on. Then you need to mount the partition and browse to the boot folder. Open the menu.lst in the grub folder. That will give you the kernel version etc that you need. You can use the same entry (actually you want to check the boot folder to make sure the kernel is the same version as in the list. you may have updated before or updated this install and the version numbers in grub are not matching the version installed. the kernel will be labeled vmlinuz)
All that info can be found in your boot folder. When you have it written down, reboot and enter it into the grub command line.

P.S. Just in case, to mount you need to know the partition number. I'll use ? for the label bujt of course you need to use the correctr values.
```
sudo mkdir /media/ubuntu
sudo mount /dev/??? -t ext3 /media/ubuntu
```That will mount your ubuntu partition in a folder called ubuntu inside of the media folder

---

### Post by SpiceWeasel on 2006-09-20
Ok, im still not sure how to go about this (no offense to you at all im just not familiar with linux enough to really do this effectively yet), but its been a long day  and the lecture in ccnp 1 today was brutally long so i have one last question since i need this system dual booting with a minimal loss of data. If i was to reinstall Ubuntu on the same partitions its on now what data if any would i lose? specifacally i have a set of folders on the desktop with data i use often and need to keep (was kind of in a hurry when i put them there). Should i relocate them somewhere safe before reinstalling?

Again thanks for the help so far, i plan to look this all over and try to get a better feel for it but i really do need this done tonight or tomorrow morning by the latest. :(

---

### Post by catlett on 2006-09-20
If you reinstall ubuntu, the ubuntu partitions will be formatted and thus erased. The windows drive and the data drive will not be touched.
If the ubuntu drive holds valuable data it will need to be copied out with a live cd. If ubuntu's drive has nothing important on it, reinstall and grub will be installed fresh, with a new (correct) menu.

---

### Post by SpiceWeasel on 2006-09-20
To do that i would have to boot to the cd and map the ubuntu drive then pull the data to the cd correct? Or could i just pop the cd in and copy it into a folder on the live cd?

---

### Post by catlett on 2006-09-20
To copy outr the data, you would have to boot to the live cd. Mount the ubuntu partitionh, mount your data partition and then drag and drop (or use the linux cp command) files from ubuntu's partition to your data partition.
The issue is knowing the correct labels for the ubuntu partition and the data partiton, so they can be mounted.
Usually you can tell which is which from the output of ```
sudo fdisk -l
```

---

### Post by SpiceWeasel on 2006-09-20
Ok thanks, i'll give this a shot and see how it goes. I really wish my linux class was this semester and not next.

---

### Post by catlett on 2006-09-20
It sucks when your under the gun, but just post from within the live cd. Firefox will be on the cd already. Just post anu questions and/or commands you need.

---

### Post by SpiceWeasel on 2006-09-20
Ok according to sudo fdisk my master ATA IDE drive is /dev/hda so to mount that drive id need to go to computer, location then /dev/hda/ubuntu/username/desktop/foldername would be the right syntax for something on that drive thats in a folder on the desktop?

---

### Post by catlett on 2006-09-20
I do not think it will mount by going to Places<Computer. Just copy/paste the output of ```
sudo fdisk -l 
```and I'll give you the commands.

---

### Post by SpiceWeasel on 2006-09-20
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by catlett on 2006-09-20
Is that the output for this command ```
sudo fdisk -l
```Are you entering the dash and small letter L after fdisk. That looks like a return of options for entering fdisk without a parameter.
My ouput is like this
```
catlett@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          58      465853+  83  Linux
/dev/hda2              59        2006    15647310   83  Linux
/dev/hda3            2007        3995    15976642+  83  Linux
/dev/hda4            3996       14593    85128435    f  W95 Ext'd (LBA)
/dev/hda5   *        3996        4652     5277321   83  Linux
/dev/hda6            4653        5109     3670821   83  Linux
/dev/hda7            5110        6456    10819746   83  Linux
/dev/hda8            6457       10297    30852801   83  Linux
/dev/hda9           10298       14129    30780508+  83  Linux
/dev/hda10          14130       14462     2674791   83  Linux
/dev/hda11          14463       14593     1052226   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2656    21334288+   7  HPFS/NTFS
/dev/hdb2            2657        5210    20515005    7  HPFS/NTFS
/dev/hdb3            5211       10765    44620537+   5  Extended
/dev/hdb4           10766       14593    30747937+  a5  FreeBSD
Partition 4 does not end on cylinder boundary.
/dev/hdb5            5211        6086     7036438+  83  Linux
/dev/hdb6            6087        9489    27334566   83  Linux
/dev/hdb7            9490       10765    10249438+  83  Linux
```I am looking for a line like this ion your ouput 
```
/dev/hda5   *        3996        4652     5277321   83  Linux
```That is my ubuntu partition. It's label is /dev/hda5. Try running sudo fdisk again and make sure to add the dash small case L i.e. -l

---

### Post by Najand on 2006-09-20
The command is ```

*sudo fdisk -l*

```
i.e it is a [COLOR="Blue"]small "L"[/COLOR] not [COLOR="Red"]"1"[/COLOR] or [COLOR="Red"]capital "i"[/COLOR].

---

### Post by SpiceWeasel on 2006-09-20
Wow i really am tired hahaha my bad. I can be such a noobert sometimes. :eek:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2550    20474842+   f  W95 Ext'd (LBA)
/dev/hda2            2551       16270   110205900   83  Linux
/dev/hda3           16271       16907     5116702+  82  Linux swap / Solaris
/dev/hda4   *       16908       19457    20482875    7  HPFS/NTFS
/dev/hda5               2        2550    20474811    e  W95 FAT16 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30400   244187968+   7  HPFS/NTFS

---

### Post by SpiceWeasel on 2006-09-20
The 160 is the linux disk the 250 the windows disk and the 80 is my storage disk.

---

### Post by catlett on 2006-09-21
Thanks Najand for the help. SpiceW that is my fault, I should have caught it when you posted the output before.Anyways, to mount your ubuntu partition, enter these commands in a terminal
```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/hda2 -t ext3 /media/ubuntu
```
Then go to the top panel and enter into Places>Computer>Filesystem. Open up the media folder and you will see the ubnuntu folder with the files from your ubuntu partition.
The issue now is, ubuntu cannot write to NTFS (at least not with 100% safety and also not by default. You would have to do some more 'stuff' to get ntfs write support) and you only have the one NTFS partition available for mounting. Do you know why the other drive isn't showing any partitions?
You now have 2 options. If you have a cd player, you can copy the files to cd.
Or you can use an online file storage site to upload and hold your files until you reinstall. I use this one [http://www.gigasize.com/index.php](http://www.gigasize.com/index.php) It allows up to 1gb files. It is free but you may be hit with some pop-ups.

P.S. It looks like grub sees your windows drive as the third drive, that would mean the correct entry would be 
grub>rootnoverify (hd2,0)
grub>chainloader +1
grub>boot

Just in case you want to try before reinstall

---

### Post by SpiceWeasel on 2006-09-21
You guys are total lifesavers. I think my problems up till now have been mostly ID10T errors. :o)  I'm gonna give booting windows one last chance and if that fails i'll probably just burn the data to the cd and reinstal. On the matter of retreiving it, would it be possible to move the data to a usb removable drive thats formatted with fat32 then move it back to windows?

---

### Post by Najand on 2006-09-21
Well can you copy and paste your menu.list located in /boot/grub```

more /boot/grub/menu.lst

```
sometimes it is possible to change the setting of that file and make everything to work without formatting, mounting, etc.

---

### Post by catlett on 2006-09-21
> **SpiceWeasel said:**
> You guys are total lifesavers. I think my problems up till now have been mostly ID10T errors. :o)  I'm gonna give booting windows one last chance and if that fails i'll probably just burn the data to the cd and reinstal. On the matter of retreiving it, would it be possible to move the data to a usb removable drive thats formatted with fat32 then move it back to windows?

Yes. Plug in the usb drive after you boot to the live cd. It will be mounted automatically. It should have an icon on the desktop. Just drag and drop from the folder you mounted. If you get a permission denied error, enter ```
gksudo nautilus
```To launch the file browser as root and then drag and drop.
It appears you are OK. I am off to bed. If you have an issue, post and Najand or another will help- you.

---

### Post by SpiceWeasel on 2006-09-21
Ok this time it took the command rootnoverify (hd0,2) but it gave me "error 13 : not a supported exectuable format. As for my menu its kinda long but this is what it says, keeping in mind that NTLOADER and Windows XP were the only two windows options it has atm and both are linked to prior installs of windows.

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
# kopt=root=/dev/hda2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Najand on 2006-09-21
You have two Windows installed?
Which one is your real windows partition?
4th one of 160 or 1st one of 250?

---

### Post by SpiceWeasel on 2006-09-21
Technically........"TECHNICALLY" i only have one install of windows on the 250gb drive but to put it on there windows felt the need to format a 20gb partition on the 160 that has ubuntu to have its setup files on. I think it had something to do with the fact that its my master ATA drive. The 250 is my master SATA drive and has the actaul windows operating system on it.

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> Technically........"TECHNICALLY" i only have one install of windows on the 250gb drive but to put it on there windows felt the need to format a 20gb partition on the 160 that has ubuntu to have its setup files on. I think it had something to do with the fact that its my master ATA drive. The 250 is my master SATA drive and has the actaul windows operating system on it.
Sorry to jump in on this thread, but have you tried going into bios and booting first to the SATA drive to see if Windows would boot?

---

### Post by SpiceWeasel on 2006-09-21
I think i already said this but if i didnt, norton IS had a little misunderstanding with my hard drive causing it to fail booting windows. Being the creative type i tryed a few things and found that if i set the bios to boot to Linux, then use GRUB to boot to my SATA drive with windows it all works just fine.

---

### Post by Najand on 2006-09-21
Hmm can you try something... 
I am not sure but it may work...
Edit you menu.lst and change the red part to blue part to this:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
[COLOR="Red"]root		(hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1


> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda4
title		Windows NT/2000/XP (loader)
[COLOR="Blue"]root		(hd0,3)[/COLOR]
savedefault
makeactive
chainloader	+1
And see if Windows NT/2000/XP option can boot it or not.

---

### Post by SpiceWeasel on 2006-09-21
I opened up the text editor but its not seeing any files or folders in the root, is there something equivalent to folder options where i can enable seeing hidden folders or is this just another ID10T error on my part?

---

### Post by SpiceWeasel on 2006-09-21
Dont asnwer that i know, BOOT not ROOT, its been a loooooooooooooong day lmao.

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> I think i already said this but if i didnt, norton IS had a little misunderstanding with my hard drive causing it to fail booting windows. Being the creative type i tryed a few things and found that if i set the bios to boot to Linux, then use GRUB to boot to my SATA drive with windows it all works just fine.
Sorry, yes you did...I missed it.
I assume you're able to boot Ubuntu OK from grub, with the entries in your /boot/grub/menu.lst.
The only other thing I could suggest you try to boot Windows is:
```
title Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader +1
```

You may want to check the output of:
```
cat /boot/grub/device.map
```

---

### Post by SpiceWeasel on 2006-09-21
Sorry if i sounded rude there i didnt mean too, its just been a long day and sifting threw my own comments to see if i did actaully mention it was a low priority :(  but im using the text editor and its not letting me save my changes saying i dont have the propper access. Is there something special i have to do when saving such as putting in my admin pass somewhere along the line?

---

### Post by Najand on 2006-09-21
I think you can boot ubuntu from grub; so boot it then edit menu.lst using:
```

sudo gedit /boot/grub/menu.lst

```
it will let you save the file.

---

### Post by confused57 on 2006-09-21
> **Najand said:**
> I think you can boot ubuntu from grub; so boot it then edit menu.lst using:
```

sudo gedit /etc/boot/menu.lst

```
it will let you save the file.

I know we're all getting a little tired(I know you just mistyped it), but I believe it's:
```
sudo gedit /boot/grub/menu.lst
```

copy & paste the above command in a terminal
Edit:  Spiceweasel, I didn't take your response as rude.

---

### Post by Najand on 2006-09-21
> **confused57 said:**
> I know we're all getting a little tired, but I believe it's:
```
sudo gedit /boot/grub/menu.lst
```

You are write... I was talking about fstab with another user... And I just confused... You are right... I edited the mistaken reply, myself too.

---

### Post by SpiceWeasel on 2006-09-21
So just to clarify, when you said

> title Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader +1

Thats hd2 and not hd1 fomr this output

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2550    20474842+   f  W95 Ext'd (LBA)
/dev/hda2            2551       16270   110205900   83  Linux
/dev/hda3           16271       16907     5116702+  82  Linux swap / Solaris/dev/hda4   *       16908       19457    20482875    7  HPFS/NTFS
/dev/hda5               2        2550    20474811    e  W95 FAT16 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30400   244187968+   7  HPFS/NTFS

---

### Post by Najand on 2006-09-21
> /dev/hda is hd0
/dev/hdb is hd1
/dev/sda is hd2... 
It seems...

---

### Post by SpiceWeasel on 2006-09-21
Actaully wouldn't it be this?

> Device Boot Start End Blocks Id System
/dev/sda1 1 30400 244187968+ 7 HPFS/NTFS

Keep in mind im tired and i know very little about how GRUB works so i could just be talking nonesense as far as i know hehehe.


*EDIT* I see thanks for clarifying that for me.

---

### Post by confused57 on 2006-09-21
Since your entry with root (hd1,0) doesn't boot Windows, I thought it might be worth a shot to try booting it as root (hd2,0)...sometimes using rootnoverify works when just root doesn't.
The mapping command is used to fool Windows into thinking it is the first OS, which Ubuntu actually is.

Maybe when you have time to read it, here's an excellent explanation of how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by SpiceWeasel on 2006-09-21
Ok i see. But its still telling me i cant save it because i lack the propper premissions which is weird cause it required me to enter my admin pass to get into gedit in the first place. What should i do?

*EDIT* says its read only in gedit

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> Ok i see. But its still telling me i cant save it because i lack the propper premissions which is weird cause it required me to enter my admin pass to get into gedit in the first place. What should i do?
I'm sorry, but I've never experienced that with gedit...after I make changes, I usually click "File", then "Quit", then "Save Changes".  Hopefully, someone else can help you with permissions.

---

### Post by SpiceWeasel on 2006-09-21
Ok it was another ID10T error hehehe i put in the pass wrong i guess so it opened it in read only. I made the changes now im gonna reboot and pray.

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> Ok it was another ID10T error hehehe i put in the pass wrong i guess so it opened it in read only. I made the changes now im gonna reboot and pray.
It happens to all of us...good luck.

---

### Post by SpiceWeasel on 2006-09-21
Success......of a sort. it trys to switch over to NTLDR but it cant find it. My best guess is it is trying to boot the ntfs parition that doesnt actaully have the windows XP instal on it. I could be wrong, though i was under the impression that GRUB would do the actaul loading instead of switching over to NTLDR. Any ideas?

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> Success......of a sort. it trys to switch over to NTLDR but it cant find it. My best guess is it is trying to boot the ntfs parition that doesnt actaully have the windows XP instal on it. I could be wrong, though i was under the impression that GRUB would do the actaul loading instead of switching over to NTLDR. Any ideas?
The chainloader +1 actually switches loading Windows to the NTLDR.
Did you happen to try the entry I gave you (hd2,0)?

Also, see what the device.map shows:
```
cat /boot/grub/device.map
```

---

### Post by SpiceWeasel on 2006-09-21
Your right it is hd2 and thats what i used. Is there anyway to get past using NTLDR or is that a required part of the boot loading?


*EDIT* would the command "chainloader force" work in this instance?

Thanks for your help so far guys but the hour is late and i need to go pass out if i want to have any hope of getting up for class tomorrow.

---

### Post by SpiceWeasel on 2006-09-21
Ok i just got back from class today and i was wondering what the correct syntax for the force command for chainloader and if that will actaully bypass using NTLDR like i think it will? And is this a dangerous option for loading an XP partition?

---

### Post by confused57 on 2006-09-21
> **SpiceWeasel said:**
> Ok i just got back from class today and i was wondering what the correct syntax for the force command for chainloader and if that will actaully bypass using NTLDR like i think it will? And is this a dangerous option for loading an XP partition?
I'm not familiar with the chainloader --force +1 option, found it by googling...I don't suppose it would hurt anything.

I was looking through an earlier link I gave you concerning grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Toward the bottom half of the page, it mentions pressing 'c' at the grub menu, then entering:
grub>find /boot.ini
grub>find /ntldr

You may want to read through this section & see if grub is able to find your boot.ini & ntldr.

I have no idea how Norton IS is preventing booting Windows, why Windows had to install setup files on your 160 Gb drive.

I'm not experienced enough with different computer setups to be able to give you specific advice, but you may want to try some things like disconnecting all your drives, except the 250 Gb SATA drive and see if Windows will boot.  If you decide to reinstall Windows, you might want to disconnect all the other drives so the Windows installation will install "setup" files to this drive.

I don't know if a repair of the Windows mbr would do anything or not:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
This page is titled "Uninstall Ubuntu", but it basically a guide on how to restore the Windows mbr.

Hopefully, someone else more experienced with your problem will see this thread and can give you some helpful advice...good luck.

---

### Post by SpiceWeasel on 2006-09-21
I tryed the find commands and it came up empty each time, not sure why though. As for Norton, as far as i could tell it was running live update in the backround without telling me and i tryed rebooting not knowning this until windows ended live update. After that i started having boot failures. But im gonna try chainloader --force +1 to see if it resolves the issue if not its back to the drawing board :(

*EDIT* I checked my removable and its running NTFS, is there a quick way to run just the partition program with out actaully using the installer on the live cd so i can resize it and stick fat32 on there for transfering data back to my windows partition if i end up reinstalling everything?

---

### Post by SpiceWeasel on 2006-09-21
Will the version of Linux NTFS that comes with Ubuntu support writing to NTFS volumes?

---

