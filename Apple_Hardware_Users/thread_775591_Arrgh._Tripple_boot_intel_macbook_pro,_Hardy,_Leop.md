---
title: "Arrgh. Tripple boot intel macbook pro, Hardy, Leopard."
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by suchawato on 2008-04-30
Well I tried the oficial ubuntu installation guide for getting a triple boot on a second generation macbook pro.

I used bootcamp to do the windows install, and then devided the windows partion up to install ubuntu from the live cd.

Rebooting after install failed to be able to boot ubuntu through rEFIt.
Ended up bein destructive.
Tried reinstalling windows and the dreaded hal dll file missing error.
well, it had worked fine the previous install...
So here's what I currenly have:
My mac partition,
a 6 gig partion,
another 6 gig partion,
and a swap.

Not even a double boot now.
I can't even get OS X's boot camp to delete the changes and restore the areas bac to mac.
It won't let me reinstall wilndows through the mac way either.

I have now one OS and some extra waste partions that even disc utility in OS X can't get rid of.

I would like to do this properly. Help!

-Sara

---

### Post by billbear on 2008-04-30
Hardy has a problem that may wipe your MBR partition table. 
list your GPT table and mbr table here by:
open a terminal in OS X and type
diskutil list
sudo fdisk /dev/rdisk0
and copy the output of the command here.

---

### Post by MTZeon on 2008-04-30
> **suchawato said:**
> Well I tried the oficial ubuntu installation guide for getting a triple boot on a second generation macbook pro.

I used bootcamp to do the windows install, and then devided the windows partion up to install ubuntu from the live cd.

Rebooting after install failed to be able to boot ubuntu through rEFIt.
Ended up bein destructive.
Tried reinstalling windows and the dreaded hal dll file missing error.
well, it had worked fine the previous install...
So here's what I currenly have:
My mac partition,
a 6 gig partion,
another 6 gig partion,
and a swap.

Not even a double boot now.
I can't even get OS X's boot camp to delete the changes and restore the areas bac to mac.
It won't let me reinstall wilndows through the mac way either.

I have now one OS and some extra waste partions that even disc utility in OS X can't get rid of.

I would like to do this properly. Help!

-Sara
Hi,

I have an Intel Macbook and I've successfully managed to get triple boot on it, quite simple too :)

Here how:

1 - Make sure you use Leopard and have it updated (10.5.2).
2 - Start BootCamp and create a partition for Windows XP (15G is enough).
3 - Don't install it through Bootcamp.
4 - Insert Windows CD and reboot holding C when you hear the beeping sound.
5 - Windows instalation should start, follow the usual instalation process of Windows.
6 - If it reboots during instalation, you press ALT during reboot so that you can pick Windows instalation.
7 - After Windows is installed, insert your Leopard DVD and it should install all your Apple drivers and stuff.
8 - Update your Apple Software (there will be an option on the start menu to do so).
9 - Update Windows XP.
10 - Now that Windows is installed, get back to MacOS, we are going to install Linux now.
11 - Start Disk Utility and create a new partition on Machintosh HD, name it Linux
12 - Insert Linux CD and reboot holding C
13 - On Linux instalation, delete the partition you created (Linux) because its HFS, and set it as ext3 and mount /. Don't need to create swap (I know its going to warn you, but ignore it).
14 - At the last step of setup, click advanced because you need to change where GRUB is going to be installed, choose sdaX (which X is your Linux partition).
15 - Let it install Ubuntu.
16 - Get back to MacOS, install rEFIt, reboot and run the partition manager of rEFIt, which should take care of every detail of booting for each OS.
17 - Reboot and that's it.

This is what I did, referenced here: [http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS](http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS)

---

### Post by JCasper on 2008-04-30
I have the latest macbook 2008 (5th gen I think.)

Will this method work with it as well? 

(Edit)* I noticed on that link he mentions which laptop he tested this out on which is the 2008. Cool

Do you guys have any problems that can't be dealt with with ubuntu on a mac?

Thanks, Id love to be triple booting right now!!!!

---

### Post by MTZeon on 2008-04-30
> **JCasper said:**
> I have the latest macbook 2008 (5th gen I think.)

Will this method work with it as well? 

(Edit)* I noticed on that link he mentions which laptop he tested this out on which is the 2008. Cool

Do you guys have any problems that can't be dealt with with ubuntu on a mac?

Thanks, Id love to be triple booting right now!!!!
I have everything working on Ubuntu on my Macbook (Its 2008 gen too). Had to find how to enable the sound, iSight camera, wifi and the two finger right click for the trackpad, but everything is fine now.

Any problems setting the triple boot, post them :)

---

### Post by billbear on 2008-04-30
MTZeon: I don't think you will be able to boot XP again without changing the partition number of XP in the boot.ini after installing ubuntu. And you may have not tried ubuntu 8.04, which is different and may require syncing partition tables after install.

---

### Post by MTZeon on 2008-05-01
I didn't have any problems booting into Windows XP. And I have Ubuntu 8.04 :) After installing Ubuntu, all I had to do was run the rEFIt partition manager and sync the tables.

---

### Post by billbear on 2008-05-01
> **MTZeon said:**
> I didn't have any problems booting into Windows XP. 

I don't understand. Maybe you would not mind posting your MBR/GPT tables and XP file boot.ini?
I think your XP was originally partition 3 and then partition 4.
And also I don't understand your link [http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS](http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS)  where you also created a swap that made XP partition 5. I would believe unless you manually edited MBR table to skip some partitions XP cannot even see himself.

> **MTZeon said:**
> And I have Ubuntu 8.04 :) After installing Ubuntu, all I had to do was run the rEFIt partition manager and sync the tables.

You did not say you had synced the tables so i misunderstood. Sorry i did not read carefully enough. But it is partition tool not partition manager. I really did not understand by 'partition manager' what you meant :)

---

### Post by JCasper on 2008-05-01
Awesome news MTZeon, very promising. I am going to attempt the set up this weekend and will be sure to post my problems :-)

Thanks again!

---

### Post by MTZeon on 2008-05-01
> **billbear said:**
> I don't understand. Maybe you would not mind posting your MBR/GPT tables and XP file boot.ini?
I think your XP was originally partition 3 and then partition 4.
And also I don't understand your link [http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS](http://www.jbkempf.com/blog/post/2008/02/27/MacBook-install:-triple-boot:-linux-windows-Mac-OS)  where you also created a swap that made XP partition 5. I would believe unless you manually edited MBR table to skip some partitions XP cannot even see himself.

I did edit the boot.ini so that it didn't show twice Windows XP...come to think of it, first time I tryed to install Windows XP, it hang and I rebooted and reinstalled it again on the same drive...I kept the entry that was booting, maybe that's why I didn't have any problems booting from it when I ran the partition tool. :-k You want a screenshot of MBR/GPT tables? Or is there another way to show you what I have here? (maybe rEFIt files... I'll check).
That link isn't mine, I just followed what he said, for most part :)

> **billbear said:**
> 
You did not say you had synced the tables so i misunderstood. Sorry i did not read carefully enough. But it is partition tool not partition manager. I really did not understand by 'partition manager' what you meant :)
No problem :)

---

### Post by billbear on 2008-05-01
GPT table: diskutil list
MBR table: sudo fdisk /dev/rdisk0
(Type them in OS X terminal)
Or you can run the rEFIt Partition Inspector, in the rEFIt dmg you downloaded.

---

### Post by billbear on 2008-05-01
As you may need to change the boot.ini, why do you have to partition twice? I remember when i changed boot.ini, XP did become bootable again but the system became unstable. I would use disk utility to make space for xp and linux at the beginning and avoid this. No need to run boot camp. Just remember XP must be the last partition. Also to avoid syncing tables (some people still have problem booting hardy after a syncing), I would recommend this process:
1.Use Disk Utility to add 2 partitions at the end of the disk.(Assuming your disk is originally one big partition) Set the last partition to FAT. Install rEFIt.
2. Reboot and install XP@FAT partition. (You must format C: to either NTFS or FAT with the XP installer or XP won't boot)
3. Reboot with Ubuntu Gusty to format your linux partition.
4. Reboot with Ubuntu Hardy to install, don't create/delete/format partitions. (If you want a swap, the installer will format it anyway thus you need to sync tables) Install grub to (hd0,2)
That's it. You can add a swap file now, or just use the xp swap file pagefile.sys to save space. (Config in XP to make pagefile.sys static length first)

---

### Post by billbear on 2008-05-01
> **MTZeon said:**
> I did edit the boot.ini so that it didn't show twice Windows XP...come to think of it, first time I tryed to install Windows XP, it hang and I rebooted and reinstalled it again on the same drive...I kept the entry that was booting, maybe that's why I didn't have any problems booting from it when I ran the partition tool. :-k 

I think the story is, After installing Ubuntu, XP hang, reinstalled XP without formatting XP partition so it kept the dead entry, showed 2 XP. Then you deleted the dead entry in boot.ini.

---

### Post by JCasper on 2008-05-01
Ugh, sounds like a full weekend of work ahead of me with this one...lol...That should go nicely with my final exam studying and GTA4 playing...

---

### Post by suchawato on 2008-05-01
> **billbear said:**
> Hardy has a problem that may wipe your MBR partition table. 
list your GPT table and mbr table here by:
open a terminal in OS X and type
diskutil list
sudo fdisk /dev/rdisk0
and copy the output of the command here.
here you go:
```
s-h-murrays-macbook-pro:~ Sara$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *111.8 Gi   disk0

DiskManagement setuid-tool failure
s-h-murrays-macbook-pro:~ Sara$ sudo fdisk /dev/rdisk0

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
Sorry, try again.
Password:
Disk: /dev/rdisk0	geometry: 14593/255/63 [234441648 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -     409639] <Unknown ID>
 2: AF 1023 254  63 - 1023 254  63 [    409640 -  207355904] HFS+        
 3: C0 1023 254  63 - 1023 254  63 [ 208027688 -   13207032] CTOS        
*4: 83 1023 254  63 - 1023 254  63 [ 221234720 -   11251954] Linux files*
s-h-murrays-macbook-pro:~ Sara$ 

```
Thanks for all the help people, stil reading the responses,
Thanks,-Sara

---

### Post by billbear on 2008-05-01
diskutil list failed to list GPT table. DiskManagement setuid-tool failure: I've never seen this, I think this is a serious GPT table error. Can you see partitions in the graphical disk utility? And run rEFIt Partition Inspector and give me its report.
Your MBR table is messed up too, your windows partition is listed "CTOS". BTW windows partition must be the last one in MBR table or there will be a missing hal.dll error. (Who knows why)
How did you split the windows partition? In windows with an MBR-only partition tool? Play with partitions only in OS X, it takes care of both GPT and MBR table.
To repair this I am afraid you are going to backup your data and wipe the whole disk. Sorry.

---

### Post by suchawato on 2008-05-01
> **billbear said:**
> diskutil list failed to list GPT table. DiskManagement setuid-tool failure: I've never seen this, I think this is a serious GPT table error. Can you see partitions in the graphical disk utility? And run rEFIt Partition Inspector and give me its report.
Your MBR table is messed up too, your windows partition is listed "CTOS". BTW windows partition must be the last one in MBR table or there will be a missing hal.dll error. (Who knows why)
How did you split the windows partition? In windows with an MBR-only partition tool? Play with partitions only in OS X, it takes care of both GPT and MBR table.
To repair this I am afraid you are going to backup your data and wipe the whole disk. Sorry.
Naa,
I will reinstall ubuntu on the available partitions.
I installed windows in a virtual machine (vmware fusion) which does all the things I need it too.
I didn't really want a windows boot anyway.
I will install ubuntu, and then have that as a dual boot.
I will delete or reformat the partions for ubuntu, or back into hfs+. either way it will be fine.
I can always use them for storage.
Osx boots just fine so no worries,

What should I do to instal ubuntu?
By the way, I figured out if i wanted to install windows, I could just reinstal to hda 4 so it's last on the boot menu.
No worries.

Yarr.
-Sara
Help with the ubuntu install would be nice!Thanks 
Sara

---

### Post by billbear on 2008-05-02
Can you see partitions in disk utility? What is the report of rEFIt Partition Inspector? Did you split windows partition with a windows program?
I think you must repair  the tables first before another attempt of install. And i recommend backup your data now.

---

### Post by cyberdork33 on 2008-05-02
> **billbear said:**
> I think you must repair  the tables first before another attempt of install. And i recommend backup your data now.
Agreed.

---

### Post by JCasper on 2008-05-02
Obviously I run into a problem with every step. I am trying to install windows now in this process and I keep getting

"disc error, press any key to reboot"

This happens when it trys to boot off of the windows install after installing from the CD.

I'm going to try and do a slow format instead of quick this time around

How do I repair my tables? I guess I should do that?

Any thoughts?

**I know for a fact the CD is fine, I have installed from this CD before FWIW.

---

### Post by billbear on 2008-05-02
Can you offer some details? The steps you took, the GPT/MBR tables info?

---

### Post by JCasper on 2008-05-02
Sure, thanks for the help man. I took your advice and set up the partitions pre-install. I then installed refit, and rebooted to install win xp. I reformated to ntfs and installed. Now the partition does not have my "Windows" label and it wont install. It is known as Partition 4 now. Here is the info refit gives me, if you need more please just ask. Also, I set up the partitions as MS-DOS FAT32 for both windows and linux because leopard does not allow me to format it as linux. I planned on fixing the linux partition in the linux set up.

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    165822503  Mac OS X HFS+
 3      166084648    208027687  Basic Data
 4      208027688    312581767  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    165822503  af  Mac OS X HFS+
 3 *    166084648    208027687  0b  FAT32 (CHS)
 4      208027688    312581767  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 166084648:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0b  FAT32 (CHS), active

Partition at LBA 208027688:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

***diskutil results***

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            78.9 Gi    disk0s2
   3:       Microsoft Basic Data LINUX                   20.0 Gi    disk0s3
   4:       Microsoft Basic Data                         49.9 Gi    disk0s4
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:        CD_partition_scheme                        *798.4 Mi   disk1
   1:              CD_ROM_Mode_1 VRMPVOL_EN              695.2 Mi   disk1s0
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *16.0 Mi    disk2
   1:        Apple_partition_map                         31.5 Ki    disk2s1
   2:                  Apple_HFS rEFIt                   16.0 Mi    disk2s2

---

### Post by billbear on 2008-05-02
> **JCasper said:**
> Also, I set up the partitions as MS-DOS FAT32 for both windows and linux because leopard does not allow me to format it as linux. I planned on fixing the linux partition in the linux set up.


Just leave the linux partition 'Mac OS Extended(Journaled)'. 2 FAT partitions during XP setup cause problems. It calls the linux partition c: and xp partition d: then install boot code to c: and other things to d:. Check in OS X if it put some boot files on the partition that will become linux. Everything of XP should be on the last partition. Now you can format the linux partition in OS X as Mac OS Extended(Journaled) and install xp once more.

> **JCasper said:**
> 
I'm going to try and do a slow format instead of quick this time around

Quick is fine.

> **JCasper said:**
> 
How do I repair my tables? I guess I should do that?

Your tables are fine.

---

### Post by JCasper on 2008-05-03
OK Bill, You got me past the windows portion, now I installed linux, and I can't get it to boot. refit just sits there with the peguin and freezes.

I did make a swap and format the linux to ext3, I am now trying to install with no swap. I synced my tables using refit's partition tool as well.

Windows is good, but no go for linux :( If you need any information at all to help me more, please let me know.

Thanks so much.

---

### Post by billbear on 2008-05-03
If you want a swap you should make a partition for it earlier as partition 5.
Swap file is as good as swap partition.
What are the tables now?

---

### Post by mattgaunt on 2008-05-03
Hey I am so happy to find this thread lol, thought I was never going to get ubuntu on my MacBook.

You said that you need to change the GRUB to install somewhere else for the 2008 (5th Gen) MacBooks, does this mean It wont use Boot Camp anymore, instead use GRUB?

I dont want to triple boot, jus want ubuntu

---

### Post by MTZeon on 2008-05-03
Btw, this is my output:
GPT table:
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS MacOSX                  122.3 Gi   disk0s2
   3:       Microsoft Basic Data                         15.7 Gi    disk0s3 -> this is Ubuntu
   4:       Microsoft Basic Data                         10.9 Gi    disk0s4 -> this is WIndows XP

MBR table:
Disk: /dev/rdisk0	geometry: 19457/255/63 [312581808 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE    0   0   2 -   25 127  14 [         1 -     409639] <Unknown ID>
 2: AF   25 127  15 - 1023  45  36 [    409640 -  256520776] HFS+        
 3: 83 1023  45  37 - 1023  40  62 [ 256930416 -   32884766] Linux files*
*4: 07 1023  63  48 - 1023  80  23 [ 289816616 -   22765152] HPFS/QNX/AUX

I have triple booting working fine... I don't use the swap for Ubuntu, maybe that's why there's so many problems.

1 - Install MacOSX
2 - Create partition for Windows XP on BootCamp
3 - Start installation for Windows XP, install it, install the bootcamp drivers from your Leopard DVD, UPDATE THEM since the ones on the DVD are outdated, reboot, update Windows. (hold one of ALT/C/CMD keys during boot so that it goes for the CD)
4 - Go back to MacOSX, create a partition for Ubuntu using Disk Utility, insert Ubuntu CD, reboot, hold C, install Ubuntu by formating the HFS partition you created on MacOS to ext3 and set its mounting point to /, don't create swap. On the last step of installation, hit "Advanced" and change where the GRUB gets installed to the partition of Ubuntu (15G partition - this is the size DiskUtility creates). Let it install and then reboot.
5 - Go back to MacOSX, install rEFIt, reboot, you shall see the 3 OS's you have, but they won't boot right away, there you have on the bottom the Partition Tool, run it, it will take care of the details for booting, reboot again - there's an option for it - and voilá, you can now boot Windows or Ubuntu.

This is what I did...

---

### Post by cyberdork33 on 2008-05-03
yes you need to reinstall the grub bootloader. no it does not replace refit.
See this thread for discussion about the issue:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by JCasper on 2008-05-03
Success!! The swap file was the trouble maker. I reinstalled last night without the swap, partition tooled my tables and volia.

Now just to get all these drivers going, I assume with a 2008 macbook the ubuntu community macbook page is sufficient?

After getting the drivers situated my next project is to figure out how to use windows pagefile as swap, that is an awesome idea.

This thread has been a lifesaver for me and you guys are all getting thanked, if I could do more I would. A bunch of people will find this info useful!!!!

BTW, refit looks so awesome when it boots up!!

---

### Post by xfile087 on 2008-10-11
I got a new MacBook Pro a couple of days ago and I have Windows XP on it too and both Mac OS X and Windows are running fine.

I installed Ubuntu as well. Worked perfectly and I can boot all three operating systems, Mac OS X and Ubuntu work wonderfully however now when I boot Windows it shows the logo and then reboots. I delete the Linux partitions and I'm back to OSX/Windows and now Windows boots perfectly fine with zero problems? Very odd indeed!

No matter, I'll just stick to VBox for now. :)

---

### Post by EnGorDiaz on 2008-11-23
guys check the link in my sig:)

---

