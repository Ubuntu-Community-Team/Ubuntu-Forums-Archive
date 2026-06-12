---
title: "Installing Ubuntu on Portable Hard Drive???"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by MackTracker on 2008-12-02
Info:
- I have Mac OS and Windows through Bootcamp. 
- I need to install Ubuntu on my portable hard drive. 
- I have partitioned my HD into 32GB FAT32 for Ubuntu and 220GB NTFS for data storage. 
- I've got rEFIt (in /efi) and grubefi (/efi/grub)
Problems: 
- Where should I install GRUB when installing from Live CD (Advanced section) so that I can boot in Ubuntu from rEFIt
- How can I create a swap partition on my portable HD? I remember that there is an option for creating a swap file. 
I'll post my partition table later. Any help is appreciated thanks in advance.

---

### Post by cyberdork33 on 2008-12-02
> **MackTracker said:**
> - Where should I install GRUB when installing from Live CD (Advanced section) so that I can boot in Ubuntu from rEFIt
I think you should choose not to install it if you are planning to use grubefi.

> **MackTracker said:**
> - How can I create a swap partition on my portable HD? I remember that there is an option for creating a swap file.
just like you would create any other partition. I would suggest gparted on the Ubuntu LiveCD.

---

### Post by Dareajoe on 2008-12-03
hello..
I need a portable external hard drive that works for both Windows and Linux without installing additional drivers. I want it to be plug-n-play. I am using Ubuntu dual-booted with Windows XP at home. Please provide me some brands/models and descriptions.

---

### Post by pxwpxw on 2008-12-03
> **MackTracker said:**
> Info:
- I have Mac OS and Windows through Bootcamp. 
- I need to install Ubuntu on my portable hard drive. 
- I have partitioned my HD into 32GB FAT32 for Ubuntu and 220GB NTFS for data storage. 
- I've got rEFIt (in /efi) and grubefi (/efi/grub)
Problems: 
- Where should I install GRUB when installing from Live CD (Advanced section) so that I can boot in Ubuntu from rEFIt
- How can I create a swap partition on my portable HD? I remember that there is an option for creating a swap file. 
I'll post my partition table later. Any help is appreciated thanks in advance.

You should get grubefi working first, you will need it to boot the external ubuntu kernel, and the old grub-pc will never do that.

From the grubefi menu, you can boot Macosx and the HD MBR (for Windows).

For an external usb drive with GUID partitioning (done by Macosx), grubefi can boot the kernel direct from the Ubuntu boot partition, but some other systems may not work so well. You can easily test that from grubefi before installing ubuntu. 

There is no point in installing GRUB (the grup-pc version ) anywhere if you only want to boot ubuntu on the external drive, it cant do it. That is why you need to have grubefi working from Macosx before installing ubuntu on the external.
 
The current grub.efi works only for the i386 ubuntu installation. Do not use the amd64 install if you want to use gub.efi. 

You can install ubuntu without a swap partition and make the swap file after.

If you create a small (20MB) hfsplus partition on the external drive, grubefi can be installed there also, blessed, and then can be booted by an intel mac from the external drive.

---

### Post by MackTracker on 2008-12-03
- When I boot from rEFIt I get 3 icons: Mac Os, Windows and a Grubefi icon (with a strange guy). So I think Grubefi is working (because i'm using rEFIt so I don't need blessing anymore)
- When installing Ubuntu from the Live CD, I choose the partition on my hard drive which is 32GB FAT32, partition ext3 and root file / However after that I have to specify where to install the Grub. You said that i shouldn't install Grub-pc. How can I not install it?

---

### Post by pxwpxw on 2008-12-03
> **MackTracker said:**
> - When I boot from rEFIt I get 3 icons: Mac Os, Windows and a Grubefi icon (with a strange guy). So I think Grubefi is working (because i'm using rEFIt so I don't need blessing anymore)
- When installing Ubuntu from the Live CD, I choose the partition on my hard drive which is 32GB FAT32, partition ext3 and root file / However after that I have to specify where to install the Grub. You said that i shouldn't install Grub-pc. How can I not install it?

Use the [back] button to get back to the main install menu, then select [continue without bootloader]
if you cant do that, just install grub to the external drive, it wont do any harm there.

---

### Post by MackTracker on 2008-12-03
> **pxwpxw said:**
> Use the [back] button to get back to the main install menu, then select [continue without bootloader]
if you cant do that, just install grub to the external drive, it wont do any harm there.

-Last time I made a mistake by not specifying the partition and Grub overwritten MBR. I had to use Windows XP CD to fix MBR.
-Second time, I tried to install Grub on my portable HD but it said cannot install and got back to main menu.
-Where to find the section [continue without bootloader]? Is it under Advanced tab?

---

### Post by cyberdork33 on 2008-12-03
> **MackTracker said:**
> -Last time I made a mistake by not specifying the partition and Grub overwritten MBR. I had to use Windows XP CD to fix MBR.
-Second time, I tried to install Grub on my portable HD but it said cannot install and got back to main menu.
-Where to find the section [continue without bootloader]? Is it under Advanced tab?

Yes, it is in Advanced.

---

### Post by pxwpxw on 2008-12-03
> **MackTracker said:**
> -Last time I made a mistake by not specifying the partition and Grub overwritten MBR. I had to use Windows XP CD to fix MBR.
-Second time, I tried to install Grub on my portable HD but it said cannot install and got back to main menu.
-Where to find the section [continue without bootloader]? Is it under Advanced tab?

and Cyberdork33.

Yes I was thinking of the Alternate install, I don't like the desktop install.
But if it was installed to the internal MBR, and the installation finished, and you did the fixmbr, thats fine. You should have the install all done and ready to try booting with grub.efi.

But please tell me where you got the grub efi, and post the grub.cfg you have.

---

### Post by MackTracker on 2008-12-04
> **pxwpxw said:**
> and Cyberdork33.

Yes I was thinking of the Alternate install, I don't like the desktop install.
But if it was installed to the internal MBR, and the installation finished, and you did the fixmbr, thats fine. You should have the install all done and ready to try booting with grub.efi.

But please tell me where you got the grub efi, and post the grub.cfg you have.
But when GRUB overwrites MBR, I cannot boot into Windows. Do I have to configure anything in my grub-efi so that I could boot into from rEFIt screen.

I got grubefi from this forum. It was in previous post i think.
[http://ubuntuforums.org/showthread.php?p=6267026](http://ubuntuforums.org/showthread.php?p=6267026)

I attached my grub.cfg

---

### Post by pxwpxw on 2008-12-04
> **MackTracker said:**
> But when GRUB overwrites MBR, I cannot boot into Windows. Do I have to configure anything in my grub-efi so that I could boot into from rEFIt screen.

I got grubefi from this forum. It was in previous post i think.
[http://ubuntuforums.org/showthread.php?p=6267026](http://ubuntuforums.org/showthread.php?p=6267026)

I attached my grub.cfg

Good you have my grub package, so I can refer to that.

1. You said: 'Last time I made a mistake by not specifying the partition and Grub overwritten MBR. I had to use Windows XP CD to fix MBR'

That should get Windows back - no need to do anything else.

Try that and if it succeeds, then -

Start grub.efi from rEFIt, you should get the grub text menu produced from grub.cfg.

From there the menu item
 [search MacOSX]
should boot macosx.

The menui item
 [Boot from HD MBR]
should boot windows

[REBOOT]
should work.

Post the result.

If that is all working, then I can get you started booting Ubuntu, that needs a bit more done.

---

### Post by cyberdork33 on 2008-12-04
> **pxwpxw said:**
> You said: 'Last time I made a mistake by not specifying the partition and Grub overwritten MBR. I had to use Windows XP CD to fix MBR'

That should get Windows back - no need to do anything else.

Yes, sorry. I misunderstood which MBR your were talking about. FIXMBR is what you need to repair that. However, in future installs, you do not need to install legacy grub to ANYWHERE if you plan to use grub-efi instead. That will prevent it from overwriting the Windows Bootloader.

---

### Post by MackTracker on 2008-12-04
- Ok i installed Ubuntu to my external HD from Live CD without installing GRUB bootloader (in Advanced section).
- When I come to rEFIt menu, I choose grubefi (with this old guy icon) but it says something like this 
rEFIt - Booting OS
Starting grub.efi
Error: Unsupported while loading grub.efi
*Hit any key to continue*
- By the way I installed my Ubuntu on sdb4. Do I have to change my grub.cfg?

This is my partition table 

```
 #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                                         *74.5 Gi             disk0
   1:                        EFI                                                 200.0 Mi         disk0s1
   2:                  Apple_HFS Macintosh HD                              53.9 Gi         disk0s2
   3:       Microsoft Basic Data WINDOWS HD     20.3 Gi            disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                                           *232.9 Gi      disk1
   1:             Windows_FAT_32                                                         31.2 Gi        disk1s1
   2:               Windows_NTFS Data                                              201.6 Gi        disk1s5
```
31.2GB Windows_FAT32 iss where I need to install Ubuntu

---

### Post by pxwpxw on 2008-12-04
> **MackTracker said:**
> - Ok i installed Ubuntu to my external HD from Live CD without installing GRUB bootloader (in Advanced section).
- When I come to rEFIt menu, I choose grubefi (with this old guy icon) but it says something like this 
rEFIt - Booting OS
Starting grub.efi
Error: Unsupported while loading grub.efi
*Hit any key to continue*
- By the way I installed my Ubuntu on sdb4. Do I have to change my grub.cfg?

This is my partition table 
(not quoted)

31.2GB Windows_FAT32 iss where I need to install Ubuntu

(The old guy is an icon from the grub site, you can change later)

I will have to run that package here to see how to get that refit error, I have only seen it when attempting to run grub.efi x86_64 version in current refit 32. 

Some other things need further explanation, but for now, before doing any more with the ubuntu install, you must get grub.efi going and displaying its menu. This will also have a menu item or command line to check partition layout. 
The grubefi must be fully operational stand alone, it does not matter whether ubuntu is installed or not, grubefi does not care about that.

What is you Mac info from here -
```

Menu bar:Apple:About this mac:More:

Hardware Overview:

  Machine Name:	Power Mac G5
  Machine Model:	PowerMac7,2
  CPU Type:	PowerPC 970  (2.2)
  Number Of CPUs:	1
  CPU Speed:	1.6 GHz
  L2 Cache (per CPU):	512 KB
  Memory:	2.25 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	5.1.5f2
  Serial Number:	YM413PDGPGA

```

Refit may have a problem with the location you have the /EFI/grub folder, refit can sometimes find grub.efi and then still be unable to run it.

This should be in the root of the Macosx partition and upper case 'EFI' is safest, not 'efi'

You should have only one /EFI  directory and then -
```
   
   /EFI/grub/ with grub.efi and modules 
   
   /EFI/refit/ with refits stuff
 
```

I will post some more when I have looked at it on the MacBook, I am on the wrong computer here (G5).

---

### Post by pxwpxw on 2008-12-05
Rechecked it here, there are 2 essentials  -
(I will amend the grub thread to clarify this.)

1. the folder containing  grub and refit MUST be named EFI (upper case)not lower case 'efi'. There is a conflict between refit and grub about case handling.

2. the final location and layout in the Macosx root  /EFI directory 
and its contents as seen from a terminal command line in macosx, should be like this -
```

The /EFI directory -  
mb:~ pxw$ ls /
Applications    System          etc             sbin
Desktop DB      Users           grubstuff       tmp
Desktop DF      Volumes         mach            untitled folder
Developer       automount       mach.sym        usr
EFI             bin             mach_kernel     var
Library         cores           mds-crash-state
Network         dev             private
mb:~ pxw$ 

The /EFI contents -
mb:~ pxw$ ls -l /EFI
total 0
drwxr-xr--   82 pxw  pxw    2788 Nov 28 16:36 grub
drwxrwxrwx   10 pxw  admin   340 Dec  5 15:13 refit
drwxrwxrwx   23 pxw  admin   782 Oct 20 16:56 tools

```

I checked this with refit as the default boot manager, as well as for grub as the default.

Please check that.

---

### Post by MackTracker on 2008-12-05
I just change the directory from /efi to /EFI but to no avail...
When I select grubefi, I'll still get the error message. What's the problem? Maybe it is my rEFIt problem?
I'm currently using rEFIt 0.11 should i upgrade to 0.12?

My mac info

Model Name:	MacBook
  Model Identifier:	MacBook3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MB31.008E.B02
  SMC Version:	1.24f2

---

### Post by pxwpxw on 2008-12-05
> **MackTracker said:**
> I just change the directory from /efi to /EFI but to no avail...
When I select grubefi, I'll still get the error message. What's the problem? Maybe it is my rEFIt problem?
I'm currently using rEFIt 0.11 should i upgrade to 0.12?

My mac info

Model Name:	MacBook
  Model Identifier:	MacBook3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MB31.008E.B02
  SMC Version:	1.24f2

Something is wrong somehwere.

Please list the EFI files using Macosx terminal
```

$ ls /
$ ls /EFI/*

```
and post the result, I can see from that if everything is in the right place..

I am using refit 0.12. and you have a later model macbook 3,1 - SantaRosa? mine is 2,1. 
So yes, please get the later refit 0.12 version, let us eliminate that suspect.

---

### Post by MackTracker on 2008-12-05
```
 MacBuntu-2:~ ngo$ ls /EFI/*
/EFI/rEFIt License.rtf	/EFI/rEFIt ReadMe.rtf

/EFI/grub:
_chain.mod	cpio.mod	grub.cfg	loadenv.mod	reboot.mod
_linux.mod	cpuid.mod	grub.efi	loopback.mod	reiserfs.mod
acorn.mod	crc.mod		grub.icns	ls.mod		scsi.mod
affs.mod	date.mod	grubtux.icns	lspci.mod	search.mod
afs.mod		datehook.mod	gzio.mod	lvm.mod		sfs.mod
amiga.mod	datetime.mod	halt.mod	mdraid.mod	sleep.mod
apple.mod	dm_nv.mod	hello.mod	minix.mod	sun.mod
appleldr.mod	doc		help.mod	normal.mod	terminal.mod
at_keyboard.mod	echo.mod	hexdump.mod	ntfs.mod	terminfo.mod
blocklist.mod	elf.mod		hfs.mod		ntfscomp.mod	test.mod
boot.mod	ext2.mod	hfsplus.mod	pc.mod		udf.mod
bufio.mod	fat.mod		iso9660.mod	pci.mod		ufs.mod
cat.mod		font.mod	jfs.mod		raid.mod	vga_text.mod
chain.mod	fs_uuid.mod	kernel.mod	raid5rec.mod	xfs.mod
cmp.mod		fshelp.mod	labels		raid6rec.mod
configfile.mod	gpt.mod		linux.mod	read.mod

/EFI/refit:
enable-always.sh	icons			refit.efi
enable.sh		refit.conf		refit.vollabel

/EFI/tools:
DrawBox.efi	dhclient.efi	edit.efi	hostname.efi	pppd.efi
Shell.efi	dumpfv.efi	ftp.efi		ifconfig.efi	route.efi
TextMode.efi	dumpprot.efi	gptsync.efi	loadarg.efi	tcpipv4.efi
dbounce.efi	ed.efi		hexdump.efi	ping.efi	which.efi
```

---

### Post by pxwpxw on 2008-12-05
That looks correct, provided it shows as EFI in ls.
You can check that -
```

mb:~ pxw$ ls /
Applications    EFI             Users           cores           mach            private         usr
Desktop DB      Library         Volumes         dev             mach.sym        sbin            var
Desktop DF      Network         automount       etc             mach_kernel     tmp
Developer       System          bin             grubstuff       mds-crash-state untitled folder
mb:~ pxw$ 

```

I would like to eliminate refit by booting direct to grub efi, as the problem seems to be between refit and grub. I assume refit is booting Macosx (boot.efi), so dont see why it shoud fail to boot grub.efi.

To boot directly, grub.efi needs to be blessed. This will bring up the grub menu at startup, refit will then be unblesed and will not show.
When the grub menu comes up, you can boot back into macosx and reset the startup disk if you wish.
If not, you can reset the startup by holding down the Apple(command) Option P R keys at startup, or using the Macosx install DVD to reset the startup to Macosx.
To restore to refit as startup, you then run the refit enable.sh.

My EFI configuration is the same as yours and this is how to bless grub.efi
```

mb:~ pxw$ sudo bless --folder / --file /EFI/grub/grub.efi 

```

---

### Post by pxwpxw on 2008-12-05
On second thoughts, that /EFI/rEFIt folder may be the bug. Try removing it.

 MacBuntu-2:~ ngo$ ls /EFI/*
/EFI/rEFIt License.rtf	/EFI/rEFIt ReadMe.rtf

---

### Post by MackTracker on 2008-12-05
I just blessed grub.efi. Now it only boots straight to Windows. When I hold alt(option) at the startup, there are 2 options EFI boot and Windows. Both selections boot Windows. Command+R+P does not work. I'm going to get my installation disc to fix this. See what'll happen

---

### Post by pxwpxw on 2008-12-06
That dhould be commnd option R P

---

### Post by grazed on 2008-12-06
unless the drive has a fan built into it, running an OS off of it isn't the brightest idea. you'll have way too much heat build up inside of the enclosure. externals aren't built to be constantly read/written to.

i would estimate a week before it craps out on ya.

EDIT: also, due to the limitations of a 5400RPM drive + USB, you're looking at speeds slower than running the live CD.

---

### Post by MackTracker on 2008-12-06
Ok I got rEFIt back...The problem now is how to make grub.efi load from rEFIt menu. Grubefi menu still doesn't show.

---

### Post by pxwpxw on 2008-12-06
Ok, but it will not help to use refit, only complicate things more. There is something wrong there, it is normally quite impossible for grubefi to default to windows. Now you can recover, please give the blessing of grub.efi another try, and do several restarts to make sure what is happening. You can just abort by holding the power-off button in, but let it complete whatever it is doing to see where it finishes up. Try it a few times to make sure it is constistent and you can describe what happens. Also try the Windows icon to see what that does.

Before you do that, try booting Windows with refit to see what that does.
And what were those extra files in /EFI/rEFIt ?? 
You were showing 2 directories -
/EFI/rEFIt
and /EFI/refit
and Macosx wont let you have 2 same names in one folder.

Edit-
Just reinstalled refit0.12 here and see that
/efi/rEFIt License.rtf  /efi/rEFIt ReadMe.rtf
are in fact 2 file names with a space in the middle, so not any problem to Macosx. My mistake.

---

### Post by pxwpxw on 2008-12-06
> **MackTracker said:**
> Ok I got rEFIt back...The problem now is how to make grub.efi load from rEFIt menu. Grubefi menu still doesn't show.
I reproduced all the errors you reported by running a corrupt grub.efi.

refit said:
```

Starting
Unsupported while loading grub.efi

```

When the bad grub.efi was blessed,  the option - apple boot screen (with a Windows and a Grub icon) booted straight to the MBR (windows in your case).

And the default boot went straight to the MBR.

You can check your grub.efi for both size and for errors using the md5 utility, 
You do this in terminal. You should get these results -
```

mb:~ pxw$ md5 /EFI/grub/grub.efi 
MD5 (/EFI/grub/grub.efi) = 0895ed5aae62ec4f692f83484d6e0ff2

mb:~ pxw$ ls -l /EFI/grub/grub.efi 
-rwxr--r--   1 pxw  pxw  235008 Nov 19 21:41 /EFI/grub/grub.efi

```

If there is an error that is the cause of all the problems, and a new down load and reinstall should fix it. 

You can use the md5 check to confirm the replacement  is ok.

It may have been a problem with the utility used to unpack it.

Also found the the Command Option P R did not work (as you reported - sorry about that), I used the refit CD to rescue me.

---

### Post by MackTracker on 2008-12-06
```
MacBuntu-2:~ ngo$ md5 /EFI/grub/grub.efi 
MD5 (/EFI/grub/grub.efi) = 0895ed5aae62ec4f692f83484d6e0ff2
MacBuntu-2:~ ngo$ ls -l /EFI/grub/grub.efi
-rwxr--r--@ 1 ngo  staff  235008 Nov 19 18:41 /EFI/grub/grub.efi
```
  

It seems like the file is not corrupted

---

### Post by pxwpxw on 2008-12-06
> **MackTracker said:**
> ```
MacBuntu-2:~ ngo$ md5 /EFI/grub/grub.efi 
MD5 (/EFI/grub/grub.efi) = 0895ed5aae62ec4f692f83484d6e0ff2
MacBuntu-2:~ ngo$ ls -l /EFI/grub/grub.efi
-rwxr--r--@ 1 ngo  staff  235008 Nov 19 18:41 /EFI/grub/grub.efi
```
  

It seems like the file is not corrupted

Right.

Ok, sorry about all the false leads, I tried everything here to reproduce the bug, but I can't on the MacBook2,1

Seems that there must be significant firmware differences between your MacBook3,1 and my 2,1., causing the Mac to refuse to load grub.efi.
The fact that it fails when attempting to run directly (without using refit) indicates a mismatch between the grub.efi and the mac firmware, that has been the case in the past, but there has been development since last reports.

I hope to get some other Mac versions to test where it is ok.

I will leave it there unless you have any other ideas. 

Thanks for giving it a try, much appreciated.

---

