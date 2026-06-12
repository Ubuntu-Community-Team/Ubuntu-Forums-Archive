---
title: "triple boot nightmare"
date: 2008-10-07
forum: Apple Hardware Users
---

### Post by niteblind on 2008-10-07
Hi,

I have been trying to triple boot my mac book with ubuntu hardy but I cannot find a devent how to. I tried the one on the help.ubuntu.com page which send you to wikipedia and on the partitoning step if comes back saying the @Linux@ partition type is not valid.

So what should I be using instead. Does anyone have a better how to.

Also I normally like to have 3 l ubuntu partitions, 1 swap, 1 root and 1 home. Is this still possible if I triple boot|

Cheers

---

### Post by cyberdork33 on 2008-10-07
Resize your OS X partition with Bootcamp (or whatever other tool you want), then boot the Ubuntu LiveCD and use gparted to resize the Windows partition and create your other Ubuntu partitions. You will want the EFI, OSX, Ubuntu root, and Windows partitions are the first 4 on the disk (with windows being preferably #4). your other ubuntu partitions can go wherever you like after #4.

1. EFI
2. OS X
3. Ubuntu root - /
4. Windows
5. Ubuntu /home
6. swap

When you start the Ubuntu installer you will need to manually define the partitions to use for / , /home, and swap, and also be sure to indicate that you want to install grub to the Ubuntu root partition (clicking the "advanced" button near the end of the installer setup will allow you to do this).

After the Ubuntu install, use the refit partition tool to sync the partitions again (as Ubuntu messes them up), then you can install windows.

---

### Post by miegiel on 2008-10-07
It should be possible. I don't have a mac though, but I've got a quintuple boot at the moment. The default ubuntu 64 I use, a 32 bit ubuntu in case I break my the ubuntu I use and need to get my system back up on it's feet and don't want to waste time reinstalling, and finally XP (for gaming) vista32 and vista64 (for fun and reassuring myself vista still doesn't fully support my hardware)

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS (XP)
/dev/sda2            6375       12748    51199155    7  HPFS/NTFS (vista32)
/dev/sda3           12749       19122    51199155    7  HPFS/NTFS (vista64)
/dev/sda4           19123       60801   334786567+   5  Extended
/dev/sda5           19123       21672    20482843+  83  Linux (ubuntu32)
/dev/sda6           21673       22194     4192933+  82  Linux swap / Solaris
/dev/sda7           22195       24744    20482843+  83  Linux (ubuntu64)
/dev/sda8           24745       60801   289627821   83  Linux (home)
```

Note that I put all 4 linux related partitions in the extended partition.

I suggest you get the gparted live CD and setup your partitions in advance of installing ubuntu and when installing ubuntu go for the manual option at the partitioning step (thou you probably do that already since you use a separate home partition)

I hope this will give you some inspiration.

---

### Post by cyberdork33 on 2008-10-07
> **miegiel said:**
> put all 4 linux related partitions in the extended partition.

I suggest you get the gparted live CD and setup your partitions in advance of installing ubuntu and when installing ubuntu go for the manual option at the partitioning step (thou you probably do that already since you use a separate home partition)

I hope this will give you some inspiration.Unfortunately, there is no such thing as an extended partition on an GPT partition scheme.

---

### Post by niteblind on 2008-10-08
Hi.

Thanks for the respsonses I had basically been doing what you suggest.

Install OSX 10.5.2
Resize with Bootcamp
Load the Ubuntu live cd and run gparted
Create the following Partition table

1 EFI 200mb
2 OSX 30gb
3 Linux ext3 partition 180gb
4 Bootcamp partition 20gb

The restart and run the XP installer cd, when prompted select the bootcamp partition to install to and reformat it as NTFS (the boot camp instructions say not to use FAT) the files copy acros as notmal the PC restarts and up comes the XP logo. Happy as you would think but no it then totally bombs out with a STOP error.

Is there a particular build number of XP I need to use? It is a SP2 slipstreamed cd so would an SP3 cd be better now that it is out there?

Also in the past (I have been trying since feburary to truple boot this) if I do not partition with Boot camp but instead actually use gparted to create the Fat32 windows partition I get a similar problem, the XP cd boots and copies the files acriis but when it reboots it comes up saying that the Hal32.dll fule is missing now is THIS something that refit could fix by syncing the partition tables as we get a kinda similar thing when Hardy installs sometimes and it cannot find a bootable parition on reboot is this error the winodows equiv, as the hal32 file is not missing and i have even reinstalled through the recovery console.

cheers

---

### Post by cyberdork33 on 2008-10-08
> **niteblind said:**
> 
Install OSX 10.5.2
Resize with Bootcamp
Load the Ubuntu live cd and run gparted
Create the following Partition table

1 EFI 200mb
2 OSX 30gb
3 Linux ext3 partition 180gb
4 Bootcamp partition 20gb

Forget BootCamp and just use DiskUtility.

in Disk Utility, create 2 partitions after your OSX partition. 1 will allocate the space for Linux, then second will be for Windows. Do _not_ alter the windows partition after this. I suggest sticking with FAT32, but if you need to convert it to NTFS, you can try.

Next boot up the Ubuntu LiveCD, delete the 3rd partition (the one between OSX and your windows partition and create a new Linux root partition there.

Next install windows, then install Ubuntu making sure to put grub on partition 3. 

Since this will not allocate space for a swap partition (you can do that with Disk Utlity in the same way you make space for the root partition if you want to) then you will probably want to create a swap file in your Ubuntu install.

---

### Post by miegiel on 2008-10-08
I obviously know little about EFI, yet i still stick with my previous recommendation. Make the partitions you want to install ubuntu and XP in in advance with the gparted live cd. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

As far as I know the live cd supports EFI I'm unsure if the gparted used by the ubuntu installer does.

Maybe you can find how to do it, or inspiration at least, here:
[http://ubuntuforums.org/showthread.php?t=454322](http://ubuntuforums.org/showthread.php?t=454322)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134)

ps. I don't think sp2 or sp3 will make a difference but you could read up on the sp3 release notes. Who knows, there might be someting EFI retated in sp3. Micro soft must have it on their site somewhere.

---

### Post by cyberdork33 on 2008-10-08
> **miegiel said:**
> I obviously know little about EFI, yet i still stick with my previous recommendation. Make the partitions you want to install ubuntu and XP in in advance with the gparted live cd. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

As far as I know the live cd supports EFI I'm unsure if the gparted used by the ubuntu installer does.
I agree 100% with that. In fact, gparted is already on the Ubuntu LiveCD. No need to download another. There are some hurdles in that message though that I don't think you are aware of.

1. Unless your windows partition is created from the mac partitioner (Disk Utility / Boot Camp), you can have troubles mounting it in OSX.
2. Certain partitions have to be in certain places in order for everything to remain bootable.

Because of this, the BEST method, is to use Disk Utility to "layout" the space for your various partitions, then use gparted to delete and replace partitions as needed while not disturbing the Windows partition if at all possible.

---

### Post by niteblind on 2008-10-08
okay, not trying to appear too stupid here but when you say use Disk utiliy to create the space for the linux OS is it better for format that as fat32 or just leave it as blank space or does it not make any difference at all|

---

### Post by cyberdork33 on 2008-10-08
> **niteblind said:**
> okay, not trying to appear too stupid here but when you say use Disk utiliy to create the space for the linux OS is it better for format that as fat32 or just leave it as blank space or does it not make any difference at all|
doesn't matter, but leaving it free space means you don't have to delete a partition before you create your linux partition in its place.

---

### Post by niteblind on 2008-10-08
okay wish me luck as for the umpteenth time I try this lark!

---

### Post by niteblind on 2008-10-09
Hi,

Okay so things have not gone too well. One thing that mistified me was how to get grub to load to the sam partition as the root partition as mentioned above?

cheers

---

### Post by cyberdork33 on 2008-10-09
> **niteblind said:**
> Hi,

Okay so things have not gone too well. One thing that mistified me was how to get grub to load to the sam partition as the root partition as mentioned above?

cheers
in the ubuntu installer, near the end of the dialog boxes (just before it actually starts in installing) there is a button on the bottom right of the window that says "advanced". You click it and select the partition to install grub to.

---

### Post by niteblind on 2008-10-10
Hi,

Sorry to be a pain in the rea, but it still went wrong! I have got to the point of not wanting to triple boot this thing anymore. I realised that for work and home I will need to have at least ubuntu and Windows on there so I made the logical choice of just dual booting those two OSes.

So now to the next problem. That did not work either. I set up the disk using the disk utility as a MS-DOS partition and the rest as a free space partition.

Then I installed Windows and for the first time it installed fine and without errors (woohoo!). I then installed ubuntu setting up the partitions so that they looked like this

1. 200mb fat (was the efi partition and I was not sure if I needed it or not).
2. NTFS 30gb windows parition
3. swap partition 4gb
4. Linux ext3 / partition
4. Linux ext3 /home partition.

I installed (admittedly without changing the grub install point). restarted and KAPOW the mac book won't boot anymore! When I turn on the mac now the white start screen comes up and all that happens is there is a flashing folder icon (atleast that is what it looks like to the blind anyway :D)

So any ideas where i screwed up?

1. Is this likely to be the grub installed to the wrong partition.
2. When installing Hardy before I had to resync the partition table to boot the first time is this likely to be the cause of my issue and if so how on earth do I sync the partitions without refit? Is it just a case of running fixmbr from the winxp cd|
3. Can windows be any more flasky on a macbook?

cheers for any help.

---

### Post by cyberdork33 on 2008-10-10
OK. If you are going to eliminate OSX altogether, then you will want to covert the entire hard drive to a normal MBR disk (no GPT). You can do this with gparted (the option is in the menus somewhere. There will be a big warning and a dropdown with a choice between msdos and GPT. You want msdos).

After you have done that, create your windows partition at the beginning of the disk the size that you want it to be leaving blank space at the end of the disk where you will install Ubuntu. Apply the changes and shutdown. You will now need to boot from the Windows CD and install. It may want to convert the partition to NTFS or whatever. Do what you want there.

After Windows is finished, boot up the Ubuntu CD. Start the installer and choose to install to the "largest free space". (This will install to the space you left when you used gparted before). You can still install grub to the ubuntu partition if you want to, but now I would suggest leaving it default so that you will be able to choose between Windows and Ubuntu on bootup. That's it. If you want to do manual partitioning before installing Ubuntu instead then do that, but you are on your own there.

After all this, you will probably get long delays on bootup... You can fix that by blessing your disk in the Terminal of the OSX DVD. See [http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)
You will probably want to use the device /dev/disk0 instead of the one listed in the link.

---

### Post by niteblind on 2008-10-10
Hi Cyberdork.

Thanks everso much for all your  help I hope I can finally leave you in pice!

cheers
niteblind

---

### Post by niteblind on 2008-10-20
Hi,

Asking a stupid question here but is it possible to upgrade the firmware of the macbook? If so how?

cheers
niteblind

---

### Post by volanin on 2008-10-20
> **niteblind said:**
> Asking a stupid question here but is it possible to upgrade the firmware of the macbook? If so how?

You can only update the macbook firmware with MacOSX, via System Update.

---

### Post by niteblind on 2008-10-20
do you know how I can find out what the current latest version is? I tried searching the apple site but could not find out. Also how do I check the current version on my macbook firmware|

cheers
niteblind

---

### Post by volanin on 2008-10-20
You said you have been trying to triple-boot since February.
Can I try to help you one last time?
Follow me.


There are some conditions that must be observed when installing the
three systems in the macbook, and it seems that no guide online
cites them, so the instalation fails for some people:


1. There must be a 200MB EFI FAT32 partition in the beginning of the disk,
and this partition must be created by the Disk Utility because it sets
some properties apropriately.

2. There must be about 130MB of unpartitioned space after the MacOS partition.
When you format with Disk Utility, it seems that there is no unpartitioned
space left, but Disk Utility indeed leaves this space unpartitioned.
(You can check it out later in GParted).

These two conditions above are essential for MacOSX Jaguar to install,
but NOT for it to work. I don't know if Leopard changed them,
but I will assume that it has not.


3. The Windows partition must be one of the first four partitions in
the system. This is because it does not read the GPT table, just the
MBR table which holds only 4 partitions.

4. The Windows XP partition must be aligned to the cylinder boundary.
This is an OS restriction, Windows Vista does not have this problem.
Disk Utility partitions are not aligned, but GParted ones are.

These conditions are essential for Windows to install AND work.


5. The Linux boot partition must be one of the first four partitions in
the system. This is a limitation of GRUB that can only read the MBR.

6. The Linux boot partition must be EXT3. Although the ubuntu GRUB has
support for GPT, it can only read EXT3 partitions in GPT systems.

The conditions above guarantee maximum compatibility between linux distros.


Based on that, and your requirement that you would like a linux system
with root, home and swap, and a Windows XP instalation, I suggest the
following:


```

sda1: FAT32 - EFI
sda2: FAT32 - STORAGE
sda3: NTFS  - WINDOWS XP
sda4: EXT3  - LINUX ROOT
sda5: EXT3  - LINUX HOME
sda6: SWAP  - LINUX SWAP
sda7: HFS+  - MACOSX

```


Step by step installation:


**1. MacOSX**

1.1. Format the disk with Disk Utility, and create 6 partitions with
your desired size based on the layout above. The EFI partition will
be created automatically. Set all partitions to be UNFORMATTED,
except for the MACOSX partition that should be HFS+ Journaled.

1.2. Install MacOSX normally.

1.3. Install REFIT.


**2. Ubuntu**

2.1. Start the LiveCD and run GParted. Delete both sda2 and sda3, and
recreate them, but be sure to enable ROUND TO CYLINDERS when creating
the new partitions. They must be aligned to cylinder boundary for
Windows XP to work with them. [i](You can skip this if you are
installing Windows Vista in the next step.)[/i]

The final layout will be like this:

```

sda1: FAT32 - EFI

UNALLOCATED SPACE - This is very small, just to allow cylinder boundary alignment.

sda2: FAT32 - STORAGE
sda3: NTFS  - WINDOWS XP

UNALLOCATED SPACE - This is very small, just to allow cylinder boundary alignment.

sda4: EXT3  - LINUX ROOT
sda5: EXT3  - LINUX HOME
sda6: SWAP  - LINUX SWAP
sda7: HFS+  - MACOSX

UNALLOCATED SPACE - About 130MB

```

2.2. Reboot and use the REFIT utility to sync GPT and MBR, just for safety.
*(You can skip this if you are installing Windows Vista in the next step.)*

2.3. Format the sda2, sda4, sda5 and sda6 partitions with the correct
filesystem.

2.4. Install Ubuntu.

2.5. Caution: When installing GRUB, install it to the sda4 partition.
To do this, just click in the ADVANCED button just before the installation
begins and set the GRUB install disk to be **(hd0,3)**


**3. Windows XP**

3.1. Boot the Windows XP CD and format the remaining partition as NTFS.

3.2. Install Windows normally. When the installation reboots, select
Windows in REFIT to continue.


After all this work, everything should be ready to go. You will have
three working systems, with storage space to share files between them.

If there are any problems, describe them here!
Good luck and enjoy!
:)

---

### Post by volanin on 2008-10-20
> **niteblind said:**
> do you know how I can find out what the current latest version is? I tried searching the apple site but could not find out. Also how do I check the current version on my macbook firmware

You don't have to worry.
When there is a new version, it appears in System Update.
And MacOSX installs it automatically for you.
Firmware updates are VERY rare.

But I don't know how to check the version numbers.
:(

---
[i]
P.S.:
The forum page has changed.
Be sure to read my post in the previous page about triple booting![/i]

---

### Post by niteblind on 2008-12-11
[QUOT
1.1. Format the disk with Disk Utility, and create 6 partitions with
your desired size based on the layout above. The EFI partition will
be created automatically. Set all partitions to be UNFORMATTED,
except for the MACOSX partition that should be HFS+ Journaled.
:)[/QUOTE]



I must be the most stupid mac user going BUT....

In Leopard I cannot create a partition with out a format. The only choice the comes close is to leave it as free space and when you do this the partition vanishes into the rest of the free space and you are left eventually with just the Mac OS partition and free space.

Also I tried creating the partitions as ms dos and then deleted and recreated them correctly use Gparted but as soon as I use the partition tool from refit  to rewrite the MBR it write the EFI partition as C\; and then you cannot install XP as it is too small and XP will not install unless to C:

This should be really straight forward but it is not. Can anyone tell me is it easier with Vista maybe?

niteblind

---

### Post by Aktariel on 2008-12-11
I too am looking at triple booting MacOSX 10.5.5, Ubuntu 8.10, and Windows XP SP3.

I am utterly unafraid to wipe and restore anything as necessary - no critical data.

MacBook4,1 2.4Ghz C2D 2GB RAM 160GB HD.

My first attempt:
Install OSX 10.5.4. Update.
Bootcamp -> 40GB Partition
Install Windows. Update.
OSX -> Disk Utility -> Divide OSX partition into a 65 and a 40 GB partition.
Ubuntu LiveCD -> install on (/dev/sda3), with grub in the same place, no swap.
Reboot, OSX ->install rEFIt.
Reboot, use rEFIt to sync partition tables.

Now, Mac and Ubuntu boot fine, but Windows gets about halfway through the loading screen and then BSODs and the computer restarts.

My next thought is to cleanly wipe the HD, restore the OSX image (via CarbonCopyCloner), partition it off with BootCamp into an 80GB partition, install Windows, and then use the Ubuntu windows installer to partition it further automatically.

Either that or completely wipe the HD, and then create three partitions of the size I want via Disk Utility, and install each of them separately, and then use rEFIt to boot them all.
 

Suggestions?

---

### Post by pxwpxw on 2008-12-12
> **Aktariel said:**
> I too am looking at triple booting MacOSX 10.5.5, Ubuntu 8.10, and Windows XP SP3.

I am utterly unafraid to wipe and restore anything as necessary - no critical data.

MacBook4,1 2.4Ghz C2D 2GB RAM 160GB HD.

My first attempt:
Install OSX 10.5.4. Update.
Bootcamp -> 40GB Partition
Install Windows. Update.
OSX -> Disk Utility -> Divide OSX partition into a 65 and a 40 GB partition.
Ubuntu LiveCD -> install on (/dev/sda3), with grub in the same place, no swap.
Reboot, OSX ->install rEFIt.
Reboot, use rEFIt to sync partition tables.

Now, Mac and Ubuntu boot fine, but Windows gets about halfway through the loading screen and then BSODs and the computer restarts.

My next thought is to cleanly wipe the HD, restore the OSX image (via CarbonCopyCloner), partition it off with BootCamp into an 80GB partition, install Windows, and then use the Ubuntu windows installer to partition it further automatically.

Either that or completely wipe the HD, and then create three partitions of the size I want via Disk Utility, and install each of them separately, and then use rEFIt to boot them all.
 

Suggestions?
It probably came undone here - 
OSX -> Disk Utility -> Divide OSX partition into a 65 and a 40 GB partition

You might like to try this procedure - (sequence and order of partitoning and installation is important). Macosx-Windows-Ubuntu.

[COLOR="Red"]EDIT-xxxxxxxxxxxxxxxxxxxxxxx
I SUPECT THIS IS NOT CORRECT FOR WINDOWS, I have not been able to check it xxxxxxxxxxxxxxxxxxxxxxxxxxxx[/COLOR]

 Starting again, repartition as for an initial Macosx install using the Macosx installer DVD. 

Install Macosx and refit, make sure refit works now, before you need it.
That gives 2 partitions, #1 200MB EFI fat (invisible), #2  Macosx = the rest of the disk.

Bootcamp -> shrink Macosx to the final size you want for it, leave the rest for windows as #3 partition, shrink it later

Install windows to the #3 partition, check it works.

[COLOR="Red"][COLOR="Red"]EDIT: This is wrong. Windows partition should not be changed after Windows is installed.[/COLOR][/COLOR]
Ubuntu LiveCD -> Use the desktop Partition Editor to resize the windows #3 partition down to what you need for windows, leaving the rest for all the ubuntu partitions, which will be #4 and up. #4 must be the ubuntu root partiton and the grub root,  but grub calls it (hd0,3). 

If you allow Ubuntu to install to the largest available free space it will auto-partition, you will get root, swap, but I think it offers an option for other configurations  (separate home partition, no swap).
Install grub to the ubuntu root partition.
Reboot and use refit to resync the partition tables.

Final Patitioning -
#1 EFI (hidden in Disk Utility) 200MB
#2 Macosx
#3 Windows
#4 Ubuntu root partition. (grub boot partiton must be in the first 4) 
#5 and above other Ubuntu partitons.

Alternative - (Disk Utility).
If done manually before Macosx install, with Disk Utility, create partitions for Macosx and Windows and remaining space for Ubuntu at their final size, avoid using Bootcamp resizing. Install in the order Macosx, Windows, Ubuntu as above. Note that #1 partition EFI is automatic and hidden from Disk Utility display.
Should work with the cloned Macosx, easy to try it in the first step, but preferable to just reinstall macosx.

This method also makes it possible to put the Macosx partition above #4, this allows a shared widows/macosx/ubuntu partiton in the first 4, where windows can see it. ( See volanin's  method above ).

---

### Post by Aktariel on 2008-12-13
This s**t is bananas!

I followed your instructions to the letter, though I didn't install the drivers on the Windows side.

Mac -> 90GB bootcamp partition -> install windows minus drivers -> install Ubuntu -> partition into 2 45 GB chunks ->install GRUB to /dev/sda4 -> reboot ->sync partition tables -> reboot -> "Windows cannot start: the file hal.dll is missing or corrupted," etc.

Needless to say, my attempts to copy it over or rebuild Boot.ini failed.

Do I have to install drivers on the Windows side, or am I missing something?

Right now I'm starting over fresh, and suggestions are welcome. (I do want OS X to be the primary OS, but the other two don't matter so much.)

---

### Post by pxwpxw on 2008-12-13
**Aktariel**

Sorry, I did not intend you leave anything out for the windows install, and I did say to check  windows was working before proceeding. I assumed you had done windows before, yes you need the windows drivers.
The missing had.dll message can be caused by a windows startup problem rather than hal.dll missing, or the missing drivers,  I can't answer that one, probably the full windows install with drivers will fix it, if not search for windows missing hal.dll.
You seem to have done everything correctly apart from missing the driver install.
I assume you mean the Apple drivers for windows.

[COLOR="Black"]Edit:
Scratch my advice[/COLOR], there seems to be a problem with any change to the Windows partiton after windows is installed. I dont have windows here now to check that out. 

Cyberdork's posts look good to me, seems to cover your situation. 

Also seems to be important to windows that ubuntu gparted partitioning is set to align to cylinder boundary, this is the default setting.

---

### Post by pxwpxw on 2008-12-14
Just trying xp again on sda3 here, got to the missing hal.dll   (googled), edited boot.ini from Macosx, changed it from 
multi(0)disk(0)rdisk(0)partition(3)
to 
multi(0)disk(0)rdisk(0)partition(2)
and moved to the next bug.
In progress.

---

### Post by Aktariel on 2008-12-16
[http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134)

Here's something interesting that I found. It's for an older version of OS X and BootCamp, but it may still work - I haven't tried it yet.

One other interesting thing to consider might be BootPicker, but I don't know how it would work.

---

### Post by pxwpxw on 2008-12-16
> **Aktariel said:**
> [http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134)

Here's something interesting that I found. It's for an older version of OS X and BootCamp, but it may still work - I haven't tried it yet.

One other interesting thing to consider might be BootPicker, but I don't know how it would work.

Got one answer here, after nearly wearing out the macbook hd doing win XP installs, with various partitoning. Possibly same applies to vista, but I cant comment on that, and still don't have all the answers.
 
1. We knew that Windows must be in the first 4 partitions to get booted (the 4 on the MBR table), so does Ubuntu.

2. Windows must be the last of the partitions in the MBR (i.e. 2,3 or 4 where 1 is the EFI 200MB).
Other GPT partitons not seen in the MBR, should be OK, but not confirmed here yet.

3. If windows is installed in sda3, and working, then if ubuntu is installed in sda4, it breaks Windows. Then if you delete sda4, windows works again (with a few minor things to sort out).

4. So I have just got to here
sda1 EFI
sda2 Macosx
sda3 Win XP
Nothing else after XP (tried sda4, breaks windows)

I am about to try 
sda1 EFI
sda2 Macosx
sda3 Ubuntu root
sda4 Win XP.
and see what happens, and what other partitions are allowable for XP.
That will be as recommended in Cyberdork33 post above I think.

if you have Macosx, Windows and Ubuntu in the MBR, then windows must be partition 4.
However, Macosx will also work in any GPT partition (above 4).
There are also side issues, needing to sync the MBR with refit after using gparted, and reinstall grub, but getting windows to install was the main issue.

This has all been done before I think, but is probably so well known that it does not get explained any more.

---

### Post by cyberdork33 on 2008-12-16
> **pxwpxw said:**
>  We knew that Windows must be in the first 4 partitions to get booted (the 4 on the MBR table), so does Ubuntu.
Well to be technical, it just has to be in the MBR partition table (which is limited to 4 partitions). It should be possible to use fdisk to create a partition table that maps the partitiions to the appropriate sectors. You could even create an MBR partition table that doesn't include the EFI partition if you wanted.

> **pxwpxw said:**
> I am about to try 
sda1 EFI
sda2 Macosx
sda3 Ubuntu root
sda4 Win XP.
and see what happens, and what other partitions are allowable for XP.
That will be as recommended in Cyberdork33 post above I think.yep

If we can get a GOOD guide on this written, we can put it in the community docs as the existing how-tos are a bit cumbersome and confusing.

---

