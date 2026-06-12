---
title: "[SOLVED] Grub booting Win XP &amp;quot;NTLDR&amp;quot; is missing"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-05-21
Hi, i've installed Ubuntu, played with it for a while (and am impressed) but there's somehting wrong with my Grub

if i tell BIOS to boot from my XP installed SATA drive, it will start up into XP upon boot

if i tell BIOS to boot from my Ubuntu IDE drive the Grub will start, i can get into Ubuntu no problems, but when i opt to boot XP from the Grub i get a screen saying something to the extent of...

> Starting up.....

NTLDR is missing

Press CTRL ALT DEL to continue.

what can i do to get the Grub to work proplerley?

---

### Post by apjone on 2007-05-21
hey dude, can you post the content of  /boot/grub/menu.lst here please. Looks like your windows section may need fixing.

---

### Post by stefaan.dutry on 2007-05-21
I'm only guessing here, remember that.

The problem seems to be that you installed them both as being the primary disk.

The problem being here now is that the grub seems to be installed on your ubuntu installed disk and the Files that are needed to start up Windows are on the windows installed disk.  But I think windows looks for the files to start up on the master drive wich you just said was the other one in bios.

I think it might have worked fine if you had installed ubuntu with windows installed disk still being the master disk.  This way you would have installed the grub on the windows installed disk and therefore that would have been the same drive as the one it checked for the files it needs.

I don't know how to help you, but that's what i think is the problem.

Remember, i'm only guessing.

I hope this clears up a few things for you.

---

### Post by Beatbreaker on 2007-05-27
so i've found out my XP installation is on Disk 4
and Ubuntu is on Disk 0

ok so here's what my Grub looks like:

you guys might not need this one but here it is anyway...

```
Ubuntu .....Ver etc...
Ubuntu Recovery
Ubuntu Memtest 86
other operating systems:
Microsoft XP professional
```

and when i edit the XP professional codes:

```
root (hd4,0)
save default
make active
map (hd0) (hd4)
map (hd4) (hd0)
chain loader +1
```


i don't know anything about this stuff but i'm failing to see the relevance of the reference to hd0 when XP is on hd4

---

### Post by logos34 on 2007-05-27
if you could post the output of 

**sudo fdisk -l**

---

### Post by Beatbreaker on 2007-05-27
> Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      620181   312571192+  42  SFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321   42  SFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       36480   231585007+   f  W95 Ext'd (LBA)
/dev/sdc5            7650       36480   231584976    7  HPFS/NTFS


basically XP on disk 4 is on a SATA
Linux on disk 0 is on an IDE

---

### Post by confused57 on 2007-05-27
You might want to post the output of:
```
gedit /boot/grub/device.map
gedit /boot/grub/menu.lst
```

---

### Post by KIAaze on 2007-05-27
> **Beatbreaker said:**
> 
```
root (hd4,0)
save default
make active
map (hd0) (hd4)
map (hd4) (hd0)
chain loader +1
```

i don't know anything about this stuff but i'm failing to see the relevance of the reference to hd0 when XP is on hd4

I don't know why you get the NTLDR error.
But I can tell you why there is a reference to hd0:
> The problem is that Windows boot must be on the first hard disk/partition in order to boot. You trick it into thinking that by adding those last two lines with the map command in the Grub menu entry.
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")

---

### Post by Beatbreaker on 2007-05-27
Output from "gedit /boot/grub/device.map"

> (hd0)	/dev/hdc
(hd1)	/dev/hdd
(hd2)	/dev/sda
(hd3)	/dev/sdb
(hd4)	/dev/sdc

Output from "gedit /boot/grub/menu.lst"

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=4199c1f2-ef47-4ad6-a108-2d1645ac733e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4199c1f2-ef47-4ad6-a108-2d1645ac733e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4199c1f2-ef47-4ad6-a108-2d1645ac733e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1

---

### Post by confused57 on 2007-05-27
Your Window's entry in grub looks like it should boot OK, based on your device.map output...a forum search for NTLDR missing didn't really turn up anything I could suggest.

The only thing you might try is changing your Window's entry to something like this:
```
title Microsoft Windows XP Professional
rootnoverify  (hd4,0)
makeactive
map (hd0) (hd4)
map (hd4) (hd0)
chainloader +1
```

You could try booting Windows with the grub CLI:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI)

---

### Post by Beatbreaker on 2007-05-27
i have a feeling that my windows is on an "sd" not on a "hd"

what do you recon?

thankx for your help confussed, im going to try your suggestion out.

---

### Post by Beatbreaker on 2007-05-27
well the rootnoverify didn't work, it still throws the NTLDR - crrl,alt,del

and when i changed the HD's to SD's i got another error completely

--> there's got to be a way of making this work right?, i might have to chankout that Grub page you've suggested to me

---

### Post by Beatbreaker on 2007-05-27
... what if i try to boot without the Grub??

i've noticed there's a few ppls that have tried to boot with one IDE and one SATA and have been highly uncessful with it

---

### Post by ASPCartman on 2007-05-27
Guys you were yousing linux toooo long )))) 

Man, just download ntldr, boot.ini (edit it), ntdetect and put it to your disk win xp AND to your  primary, active partition. (When vista overwrites my xp loader i do this. But i just copy what i want from windows dir. (I backuped))

If you made ext3 -primary, active ..... it is not good.... I have method how to fix that but you will need '**** you bill' It's complect of everything. Available for download in torrent (search here: torrentscan.com ) 

Or just make your xp pertition active again. But i think grub will load again. I used **** you bill to blank boot mbr. Than i rewrited it by my own

---

### Post by Beatbreaker on 2007-05-28
how do i get those files on the drive that has Linux Installed when i can't read that drive from windows?

---

### Post by KIAaze on 2007-05-29
> **Beatbreaker said:**
> how do i get those files on the drive that has Linux Installed when i can't read that drive from windows?

I did not fully understand ASPCartman's explanation and I don't know exactly which files you plan to transfer.
However, I can tell you how to proceed for the file transfer:

_Solution 1:_
> if i tell BIOS to boot from my Ubuntu IDE drive the Grub will start, i can get into Ubuntu no problems,
According to your original post, you can boot into Ubuntu.
You should be able to transfer the files on it that way, either by downloading them from the internet or transfering over a USB key (I don't think the files for solving you problem are very large).

_Solution 2:_
[Mount your windows partition in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

_Solution 3:_
**Warning: This will give Windows full read/write access (including root) to your Ubuntu filesystem!**
Install a driver for Windows, which allows you to read and write from/to your Ubuntu partition from Windows.
Here are some drivers you can use:
Name  	Author  	Access  	Cost  	License  	Source
[ext2ifs]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm") 	John Newbigin 	Read Only 	Free 	GPL 	Available
[Ext2fsd]("http://ext2fsd.sourceforge.net/#ext2fsd") 	Matt Wu 	Read/Write 	Free 	GPL 	Available
[Ext2 ifs]("http://www.fs-driver.org/") 	Stephan Schreiber 	Read/Write 	Free 	Freeware 	Not Available *(only one I have tried personally. It works well and is easy to install. Not GPL though.)*
[ext2 drv]("http://freesourcecodes.tripod.com/ext2.htm") 	Manoj Paul Joseph 	Read/Write 	Free 	LGPL 	Available

==========================
> i have a feeling that my windows is on an "sd" not on a "hd"
what do you recon?

I would say "sd" considering the output of your "sudo fdisk -l":
>  Device Boot Start End Blocks Id System
/dev/sdc1 * 1 7649 61440561 7 HPFS/NTFS
/dev/sdc2 7650 36480 231585007+ f W95 Ext'd (LBA)
/dev/sdc5 7650 36480 231584976 7 HPFS/NTFS

By the way, you seem to have a quite complex system setup.
What's the SFS filesystem for?

> and when i changed the HD's to SD's i got another error completely

Maybe you should post this error message too.

---

### Post by Adntu on 2007-05-29
Man!
I am still new to Ubuntu, I had some problems like this, the solution was just to change the entries in boot.ini, I am not sure of the rule, just change it up and down and try, it worked for me.
sorry for not being very specific, I hope it helps still.

---

### Post by williambrodie on 2007-05-29
I worked in a PC repair shot for a while dealing with windows... XP, Vista and Windows NT ALWAYS HAVE TO BE IN DISK 1, the first partition, ( 'hda1'  /  'C:// ' ).... U must have XP on your first primary partition as NeTworkLoaDeR (NTLDR) (or 'NTLoadr' in Windows NT) is looked for without a reference register in the... The same applies to many verious dll's and exe's used to start up... NTLDR is usually the first to load...

Windows is quite volatile when it comes to booting other OS's on the same System, it also is rarely compatible with Lilo, always use grub.

If your windows is original, use your XP recovery disk, you can then reintall the boot data, u nearly always are left with your original XP data so no problems there... then after that install Ubuntu

---

### Post by bobbob1016 on 2007-06-08
It stands for Windows NT LoaDeR to be specific.  I just had this error, out of my stupidity.  I moved the boot.ini from my XP drive, I was stupid and thought they were from some program, not XP.  If you have another XP install, you could copy them to the main part of the C drive, you might have to modify some of it though, to match your current machine.

Edit:  Windows XP is based off of Windows NT, partly anyways, that is why it uses NT's loader.

---

### Post by GrueTamer on 2007-06-08
> **Beatbreaker said:**
> i have a feeling that my windows is on an "sd" not on a "hd"

what do you recon?

thankx for your help confussed, im going to try your suggestion out.In Feisty, there's some fancy kernel thing that makes drives that are normally hdX turn to sdX, so you technically could have either, but its sdX now, so thats what we need to know.  Try changing your windows xp grub data to
```
rootnoverify (hd4,0)
makeactive
chainloader +1
```

---

### Post by Beatbreaker on 2007-06-23
> **ASPCartman said:**
> Guys you were yousing linux toooo long )))) 

Man, just download ntldr, boot.ini (edit it), ntdetect and put it to your disk win xp AND to your  primary, active partition. (When vista overwrites my xp loader i do this. But i just copy what i want from windows dir. (I backuped))

If you made ext3 -primary, active ..... it is not good.... I have method how to fix that but you will need '**** you bill' It's complect of everything. Available for download in torrent (search here: torrentscan.com ) 

Or just make your xp pertition active again. But i think grub will load again. I used **** you bill to blank boot mbr. Than i rewrited it by my own


i've found the boot.ini file on the windows partition - and i copoied NTDLR there too - still dosen't work. This is when i use the Linux as the first boot drive. 

should i edit my boot.ini file? here is is anyway

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

heres a copy of all my drives from the windows admin tools:

[[IMG]http://img151.imageshack.us/img151/6933/disksnt4.th.jpg[/IMG]](http://img151.imageshack.us/my.php?image=disksnt4.jpg)


i really want to get this to work, i almost gave up and i don't want to do that - i know there's something simple i've overlooked.

---

### Post by confused57 on 2007-06-24
About the only thing I can suggest is to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I realize you can boot Windows by changing your bios boot order, but SGD "might" help determine what the problem is?  Be interesting to see if SGD can boot your Window's drive or not...

---

### Post by Beatbreaker on 2007-06-24
> **confused57 said:**
> About the only thing I can suggest is to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I realize you can boot Windows by changing your bios boot order, but SGD "might" help determine what the problem is?  Be interesting to see if SGD can boot your Window's drive or not...

Ah thanks - trying it now i'll let you know

---

### Post by Beatbreaker on 2007-06-24
OMG... i've just realised something....

I have been going through this work sheet: [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

I've now realised that my Widows hard disk is in as SCSI-0, it's not in as ch1, ch2, ch3 or ch4 - in the BIOS

is this why the grub can't find it? is there something else i should be doing to dual boot to a SCSI device in the grub? Windows XP is in partition 1 disk 4, on SCSI-0

i can't believe i didn't notice this earlier!

---

### Post by Herman on 2007-06-24
Hello Beatbreaker :D
Nevermind, you beat me to it, I was just telling you that! :)

Grub is working perfectly, your problem is that your boot,ini file is not agreeing with your BIOS, so Windows can't find itself, it doesn't know where it stands. The error message 'NTLDR is Missing" doesn't come from GRUB, it's a Windows error message. This is probably because you changed your hard disk boot priority in your BIOS. Either change your BIOS back again to the way it was when Windows was last bootable or edit boot.ini in Windows with the new hard disk number. :)

If you can get your hard disk that has Windows in it to be number one or at least number two in your BIOS then that CD you can download from [http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn't_have_a_floppy_drive? ]("http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn%27t_have_a_floppy_drive?")will be able to boot your Windows for you so you can edit your boot.ini file.

But then after you do that your GRUB will probably be all mixed up and you'll need that Super GRUB Disk to boot Ubuntu with until you can get GRUB sorted out. :)

Regards, Herman :)

---

### Post by Beatbreaker on 2007-06-24
> **Herman said:**
> Hello Beatbreaker :D
Nevermind, you beat me to it, I was just telling you that! :)

Grub is working perfectly, it is your boot,ini file that is not agreeing with your BIOS because you changed your hard disk boot priority in your BIOS. Either change your BIOS back again or edit boot.ini in Windows with the cnew hard disk number. :)

If you can get your hard disk that has Windows in it to be number one or at least number two in your BIOS then that CD you can download from [http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn't_have_a_floppy_drive? ]("http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn%27t_have_a_floppy_drive?")will be able to boot your Windows for you so you can edit your boot.ini file.



i'm in windows now, i've done that entire web page. I did the CD option, my selection "2" works - it will boot ok if i put the SCSI drive windows is in as the first HDD in BIOS to boot (as was before) but i'm still getting NTLDR from grub if i choose the UBUNTU drive to boot first. 

I don't get a Grub when booting first on the windows HDD it just goes straught to windows. How can i install a grub on the windows disk when booting from windows first? - is it easier to do it that way?



 i don't quite understand what to change it to to get it to work from booting first with the ubuntu hard drive. 

now my boot.ini file is this... I'll clean it up later but 2ND TRY THIS works fine to get into windows, if i'm booting from windows first - should i change anything for it to work? if my windows disk is a SCSI do i have to change the value of rdisk or something?

```

[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINXP

[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Winxp="1ST TRY THIS seleccione esto primero" /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\Winxp="2ND TRY THIS essayez ceci en deuzieme" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\Winxp="3RD TRY THIS wahlen Sie diesen Third" /fastdetect
multi(0)disk(0)rdisk(1)partition(2)\Winxp="4TH TRY THIS selezioni questo fourth" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\Winxp="5TH TRY THIS selecione este fifth" /fastdetect
multi(0)disk(0)rdisk(1)partition(3)\Winxp="6TH TRY THIS seleccione este sexto" /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\Winxp="7TH TRY THIS essayez ceci en septieme" /fastdetect
multi(0)disk(0)rdisk(1)partition(4)\Winxp="8TH TRY THIS wahlen Sie dieses achte" /fastdetect
C:\="9TH TRY THIS selezioni questo nono"
D:\="10TH TRY THIS selecione este decimo"

```

---

### Post by Herman on 2007-06-24
You should read confused57's thread on how to  [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902")   :)
Then for example if you decide to make your Windows hard drive your second hard drive you will be able to boot Windows with GRUB if you edit the rdisk in boot.ini to (1). You would probably want to install GRUB to whatever hard disk you are going to use as your first, (number 0), hard disk in your BIOS.

---

### Post by Beatbreaker on 2007-06-24
its funny, now i've tried this one from the command prompt grub menu:

> 

grub>rootnoverify (hd1,0)
grub>savedefault
grub>makeactive
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
grub>chainloader +1
grub>boot


when i did that all manually from the grub control panel i got this - the boot.ini file worked no problems (i knew this because i got that menu coming up that i've now set up

but i got this: 

windows could not start because the following system file is missing or corrupt:

<windows root>\system32\hal.dll

i think i'm getting pretty close - i'm in linux now and i've edited the menu.lst with the above code as in confused57 has explained (but with rootnoverify) and i'm gunna try it grom the grub menu - if i get the boot.ini file to atleast give me something from the grub menu i'll be half way there i recon.

---

### Post by Beatbreaker on 2007-06-24
damn still not working - i think i know what the problem might be - in my boot.ini i have to change it to refer to windows being on a SCSI drive - but i can't find how to code it - it's like where rdisk is or something there

oh so close!

---

### Post by Herman on 2007-06-24
[                                        hal.dll is missing or corrup]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt")t. There's what that error message probably means.

Keep trying, you'll get it soon! :)

---

### Post by Beatbreaker on 2007-06-24
YES i got it!!! Many thanks Herman who's been helping me today and everyone over the past few weeks!

ok i don't know HOW it happened but my bloody boot.ini file as i posted above changed between when it was working and it wasn't - i didn't check it when i posed it before but there were errors in it..

this one was wrong

> [Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINXP

[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Winxp="1ST TRY THIS seleccione esto primero" /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\Winxp="2ND TRY THIS essayez ceci en deuzieme" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\Winxp="3RD TRY THIS wahlen Sie diesen Third" /fastdetect
multi(0)disk(0)rdisk(1)partition(2)\Winxp="4TH TRY THIS selezioni questo fourth" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\Winxp="5TH TRY THIS selecione este fifth" /fastdetect
multi(0)disk(0)rdisk(1)partition(3)\Winxp="6TH TRY THIS seleccione este sexto" /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\Winxp="7TH TRY THIS essayez ceci en septieme" /fastdetect
multi(0)disk(0)rdisk(1)partition(4)\Winxp="8TH TRY THIS wahlen Sie dieses achte" /fastdetect
C:\="9TH TRY THIS selezioni questo nono"
D:\="10TH TRY THIS selecione este decimo"

...i don't know what altered the file automatically to do that.. it should have been referencing to \windows NOT \Winxp 

and i recently found that the new windows recovery console is nothing like DOS used to be - they've taken EDIT away, and to make it hard for all the old users we can't use cd\ it's gotta be cd \ otherwise it'll throw an error. Good one Microsoft.

Anyway i'd like to thank eveyone who's helped me with this one - for future reference i'll post what i had to edit my menu.lst with 

> title              Windows XP
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

My working boot.ini

> [Boot Loader]

timeout=0

Default=multi(0)disk(0)rdisk(0)partition(1)\Windows



[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS seleccione esto primero" /fastdetect


Now i've got this one done i'm onto bigger and better things!

---

### Post by confused57 on 2007-06-24
I've seen other posters report the same sort of problem, they could boot a Windows or Ubuntu drive from bios, but couldn't boot the Window's drive from grub without the ntldr missing error...I've bookmarked the last 2 pages of this thread, so I can at least refer the solution, after  you & Herman determined what the problem was.  I've been a Window's user for years, however my computer setups have been quite basic and have never had to edit boot.ini...the more I use Linux & Ubuntu, the more I realize how much easier it is to configure & work with grub.
Impressive job getting your system working...Herman's the best person  I'm aware of on the forum  to assist with boot problems or any other problem for that matter...

Hi Herman...seems I learn something new every day in the forum...As I mentioned, I've seen this issue before with other posters and had no idea what to suggest...especially when they were able to boot their Window's drive from bios.  At least "armed" with the boot.ini & bios boot order problem, I can direct posters in the right direction...the OP would probably know more editing their boot.ini than I would.

---

### Post by Herman on 2007-06-24
Hello Beatbreaker,
Hey, I'm happy to see you've got it booting! Good work and congratulations! :p
It looks like you copied the boot.ini file from Miles Comer's NTLDR CD into your Windows eh? Well that's okay, as long as you got it working. I just meant to use that CD to boot with, then edit your boot.ini by hand, but I guess the way you did it could be another way to do things that I didn't think of. The main thing is, it works! :D

Hello confused57,
Thanks for all your help around here too, I don't know how many booting threads would go unanswered or unsolved if you weren't around, and your excellent thread [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902") really helps a lot of people to probably avoid getting into any difficulties in the first place, so you deserve a lot of credit yourself there!  :D

 I have been meaning to get around to doing more experiments with booting with multiple hard disks and this thread has reminded me to get busy and do so. The whole subject seems very interesting and a few experiments might show how we can help people better in the future. 
There are several ways by which we can switch our hard disk drives around and have them numbered in a different order. 
One way is physically, by the way we plug them in to our IDE cables and use cable select or jumper setting to determine which is master and which is slave, and different ports on the motherboard for which is the primary cable and which is the secondary cable.
Then when we add SCSI (SATA) disks we have ports to plug them in to the motherboard, and SCSI disks seem to most often register in the BIOS as first hard disks, bumping our IDE disks to second or third position, normally.
The BIOS will normally automatically detect our hard disks and list them in the expected order if we don't force it to do something different.
After that we have many modern computers with BIOSes that are able to switch the hard disk order around in the BIOS.
We also have GRUB's device.map, which I would like to learn a lot more about too.
And then of course, we have editable files in the bootloaders, both GRUB and NTLDR.
With all these different variables, no wonder it soon becomes  a complicated mess so quickly when people go ahead and change more than one of these at a time. 
 On the other hand though, it should be possible for us to be able to help people better to solve any boot loader/BIOS problem if we can come up with some better procedures and practices.
This thread has also brought another problem to my attention. One of the things I will be looking at now too, is the way I have the [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")'s [                                        Common Booting Errors and Some Possible Cures]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible") menu laid out. I presumed that people would know the difference between an error message coming from their BIOS, from GRUB, or from Windows.  Have you got any ideas how I can improve that, confused57, or anyone? Should I just make an alpha-numeriical listing of all boot errors maybe, and then tell people where the error message comes from rather than requiring them to know that before selecting a menu? I guess I really should re organize it all that way, it might be better.
Well bye for now,
Regards, Herman :D

---

### Post by confused57 on 2007-06-24
Thanks Herman,
    There's definitely more & more  people on the forum who are quite capable of helping others with booting problems...there's several that if I see them assisting, I know the new user is in "good hands"...your website is an invaluable resource to link anyone to with boot problems or just to learn about Linux & Ubuntu...between you, aysiu, & others, the resources are there that will encourage & enable people to make their Ubuntu experience an easier & more pleasant experience.
   My opinion is that your Super Grub section on boot errors is organized quite well...I've noticed that you update it frequently as you discover new & different methods to solve common boot problems, I attempt to keep up with the updates, keeps me quite busy doing so.   
Thanks again,

Jim

---

### Post by redcharlie on 2007-06-25
I agree with ASPCartman...seems that NTLDR was indeed missing in my case:
  1)Vista Basic preinstall on a toshiba A135-s2386
  2)Shrank Vista partition using Vista storage management tools (gparted complained that the ntfs indices were hosed, but Vista shrank itself nicely)
  3) Booted Fiesty CD, used gparted to create a second NTFS part and an ext3 part in the newly freed-up space
  4) installed XP on the new NTFS part
   5)used Vista recovery CD to restore MBR that XP installer hosed  (just to see if Vista still booted fine)
   6) intalled Fiesty from CD, wrote grub to MBR
   7) added entry to /boot/grub/menu.lst for XP partition (grub automagically got the Vista cadence right)
   8) HERE's where ASPCartman helped me:  Xubuntu and VIsta would boot, but not XP, I'd get the "NTLDR missing" message.  Well, indeed.  XP installed itself to disk "E", as Vista was on "C", but it still copied ntldr, boot.ini, and ntdetect to the root dir of drive "C", not "E".  So, I had to boot up into Vista, copy the three to the root dir of E (didn't edit anything).  Now it triple boots fine.

---

### Post by Herman on 2007-06-26
Hello redcharlie,
> I agree with ASPCartman...seems that NTLDR was indeed missing in my case:
  1)Vista Basic preinstall on a toshiba A135-s2386
2)Shrank Vista partition using Vista storage management tools (gparted complained that the ntfs indices were hosed, but Vista shrank itself nicely)
  3) Booted Fiesty CD, used gparted to create a second NTFS part and an ext3 part in the newly freed-up space
  4) installed XP on the new NTFS part
   5)used Vista recovery CD to restore MBR that XP installer hosed  (just to see if Vista still booted fine) I see, so what you did was allow Windows to set up your dual boot the 'Microsoft way'.  When you dual boot the 'Microsoft way', for some weird reason they move all the boot loader files to the 'C' drive. I always thought they installed them to the oldest microsoft system, but now I realize it's the 'C' drive. Thanks for pointing that out. They call it the 'boot partition'. You should read the following link, that will explain what happened to you in more detail, [    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm"). You could have installed Xubuntu after Vista and then you could have used GRUB as your 'third party boot manager'. You could have used GRUB's 'hide' commands to hide your Vista partition until you installed XP. Then they would have both been okay. You could have used GRUB's  'hide' and 'unhide' commands for booting them too. GRUB is a much better boot  loader/manager for booting  more than one Windows than Windows own boot loader.   ;)
>     6) intalled Fiesty from CD, wrote grub to MBR
   7) added entry to /boot/grub/menu.lst for XP partition (grub automagically got the Vista cadence right)
   :cool: HERE's where ASPCartman helped me: Xubuntu and VIsta would boot, but not XP, I'd get the "NTLDR missing" message. Well, indeed. XP installed itself to disk "E", as Vista was on "C", but it still copied ntldr, boot.ini, and ntdetect to the root dir of drive "C", not "E". So, I had to boot up into Vista, copy the three to the root dir of E (didn't edit anything). Now it triple boots fine.I'm glad you got it fixed, not very many users would have been aware of what was wrong in that situation or know how to fix it. Well done! And thanks for contributing your info. It reminded me to take that situation into account as a possibility when I see this error message again. I'll update the Super GRUB Disk Page error messages section to mention this possibility too. :D
Thanks again,
Regards, Herman :D

---

### Post by Beatbreaker on 2007-06-28
> **confused57 said:**
> I've seen other posters report the same sort of problem, they could boot a Windows or Ubuntu drive from bios, but couldn't boot the Window's drive from grub without the ntldr missing error...

i might be wrong but i felt that part of the problem continued because i kept changing the BIOS HDD boot prioirories, i decided that the system would have to configure it's boot.ini and NTLDR file whilst i was booting from the drive that was giving me the faulty grub menu and not the other way around. So i kept it fixed in bois to boot into grub every time - when i had the boot CD in there i did it all from that order of boot proririty. 



[QUOTE=Herman] 	Hello Beatbreaker,
Hey, I'm happy to see you've got it booting! Good work and congratulations!
It looks like you copied the boot.ini file from Miles Comer's NTLDR CD into your Windows eh? Well that's okay, as long as you got it working. I just meant to use that CD to boot with, then edit your boot.ini by hand, but I guess the way you did it could be another way to do things that I didn't think of. The main thing is, it works! [/QUOTE]

many thanks, yeah i copied the boot.ini file over because i thought that however it was letting me boot in was the correct way the boot.ini file should be setup.The boot.ini file is a little messy and cheap with the italian still in there but it works, and I was pretty certain that it would work in the next few tried at that stage. 

i just realised that i can put this thread into a [solved] format. Done and done.

---

### Post by redcharlie on 2007-07-15
Herman,
     Thanx for the feedback, and I'm glad to be able to contribute after all the fixes that I've found here.  Yes, I installed xubuntu last (after 0)Vista pre-install, 1) XP install, 2) Vista recovery disk to restore MBR) just because I anticipated that installing XP would wipe grub from my MBR and I didn't want to deal with that hassle.  So I just did xubuntu last.  I haven't looked at the link you provided, but it's not surprising that "dual-booting the windows way" is not as straightforward as I had hoped. 
     Hiding the partition is a great idea, I wish I had thought of that before, as there is no telling how confused my XP install is now (i.e. parts of it on "C", and parts of it on "E").   Instead of using grub, however, my instinct would be to boot up with the live cd and hide the Vista part with gparted (rather than grub), install XP, boot up with the live cd and unhide Vista, then finally install (x)ubuntu.  But that's mostly because I'm not that comfortable with grub (it's something I have to fiddle with when things *don't* work, so I have sort of a Pavlovian aversion to using it by choice ;-)

---

### Post by Herman on 2007-07-16
Hello redcharlie,
Sure, you can use Gnome Partition Editor, (GParted) for that if you like. It should work as well as GRUB. :)

Regards, Herman :)

---

