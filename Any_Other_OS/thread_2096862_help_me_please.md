---
title: "help me please"
date: 2012-12-21
forum: Any Other OS
---

### Post by gayden on 2012-12-21
hi guys,
i need your help
I was having windows 8 , vista , and Backtrack 5 on my laptop
unfortunately , i've removed windows vista by mistake
and now i can't boot to windows 8
but i can still boot to Backtrack 5

please note that windows 8 is in my enternal hdd
while BT5 is in my external hdd
and when i try to boot windows 8
it says no operating system ... because it checks for windows in the formated partition , not in the partition that includes windows 8

i think that the only way to fix this problem is to change WINDOWS 8 boot options from Backtrack 5 so it will check for operating system in the parition which includes windows 8

is there any way to do that or fix the problem ?!
thanks in advance.

---

### Post by Pjotr123 on 2012-12-21
Install Ubuntu:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by gayden on 2012-12-21
thanks for your fast reply ,
but how would this help ?!

---

### Post by gayden on 2012-12-21
i don't want to format my pc or install a new OS
but i want to boot into windows 8 instead of the empty partition

---

### Post by Pjotr123 on 2012-12-21
It would install a fine OS on your machine. We from Ubuntu advise.... Ubuntu (shock!).
Plus your machine would "automagically" probably be multi-boot again.

For pure Windows help you can go elsewhere.

---

### Post by gayden on 2012-12-21
okay thanks

i'll try it out

---

### Post by howefield on 2012-12-21
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by fdrake on 2012-12-21
no needed to install ubuntu. backtrack is based on ubuntu. Boot into backtrack and open the terminal and run
```


sudo update-grub 
```
reboot and try to boot into windows. I know this worls wit win 7 but i am not sure about win 8

---

### Post by gayden on 2012-12-21
ok i'll try this too
thanks

---

### Post by gayden on 2012-12-21
it didn't work
still saying ... Operating System not found

---

### Post by fdrake on 2012-12-21
post the output of
"sudo parted -l"
if it says error command missing just install it:
```

sudo apt-get install parted

```

---

### Post by haqking on 2012-12-21
> **gayden said:**
> it didn't work
still saying ... Operating System not found

You need to boot to the Windows  CD and repair the boot sector

it is not a Ubuntu or Linux based issue.

You could boot into BT and access the Windows partition that contains the boot.ini and modify the ARC paths depending on your actual partitions.

However a broken windows boot issue is fixed with a windows boot repair.

Peace

---

### Post by fdrake on 2012-12-21
> **haqking said:**
> You need to boot to the Windows  CD and repair the boot sector

it is not a Ubuntu or Linux based issue.

You could boot into BT and access the Windows partition that contains the boot.ini and modify the ARC paths depending on your actual partitions.

However a broken windows boot issue is fixed with a windows boot repair.

Peace
i may be wrong but a boot.ini  error does not show the msg "Operating System not found" yousually it says error boot.ini corrupted or missing or somtjign like that. want to double chekc that they did not delete the partition

---

### Post by haqking on 2012-12-21
> **fdrake said:**
> i may be wrong but a boot.ini  error does not show the msg "Operating System not found" yousually it says error boot.ini corrupted or missing or somtjign like that. want to double chekc that they did not delete the partition

A boot.ini points to where the OS are installed using Arc paths.

Anyways i wasnt telling the OP to do that, I said it was an option, the OP should be using a Windows disc to repair the boot sector as Windows 8 is apparently installed but they have deleted vista.

it is not a Linux or Ubuntu issue.

@OP boot to your windows 8 media, at setup screen choose repair

---

### Post by gayden on 2012-12-21
@fdrake :-
this is what sudo parted -l gave me :-
```
root@bt:~# sudo parted -l
Model: ATA TOSHIBA MK5075GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary
 2      250GB   395GB  145GB  primary  ntfs
 3      395GB   500GB  105GB  primary  ntfs


Model: WD My Passport 0740 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  633GB   633GB   primary                   boot
 2      633GB   686GB   52.4GB  extended
 5      633GB   639GB   6001MB  logical   linux-swap(v1)
 6      639GB   686GB   46.4GB  logical   ext4
 3      895GB   1000GB  105GB   primary   ntfs



```@haqking :-
The problem is that i've lost my windows cd
and i was having a backup for it in my hdd which got formated by mistake
and i want to boot into windows to get back all the data on it
and i'll try what you told me about the boot.ini now

@fdrake :-
no i didn't delete the partition which contains windows 8

@haqking :-
yeah , that's exactly what i'm talking about
actually it's a big story
windows 8 made an update automatically which affected windows vista
and after i fixed it ... i removed windows vista accidentally then windows 8 stopped working
and after that i tried to burn my backup into a usb but then it gave me an error code which is 0x80070241 ... then i tried to burn it into a dvd ... and i've found my hdd parition formatted so i need to recover all the removed files with a program on windows 8 then i'll try to install windows vista again
so now lets fix it step by step
the first step is to get windows 8 booting again
now i searched for boot.ini but didn't find it ... do you know where to find it ?!
i've been trying to fix my laptop for 4 or 5 full days X_X

---

### Post by gayden on 2012-12-21
well, i've found system.ini instead ... would it help ?!

[IMG]http://s9.postimage.org/6wyhza57j/Screenshot_system_ini_105_GB_Filesystem_gedi.png[/IMG]

---

### Post by haqking on 2012-12-21
> **gayden said:**
> well, i've found system.ini instead ... would it help ?!

[IMG]http://s9.postimage.org/6wyhza57j/Screenshot_system_ini_105_GB_Filesystem_gedi.png[/IMG]

no that is nothing to do with it.

I am still a little confused, do you want to repair so the system will boot to Windows 8 or do you just want to access the data from it ?

You can browse to the partitions and access the data using BT.

If you want to repair your existing windows 8 install then you will need media.

Every windows install starts from the boot sector first so that needs repairing, the boot.ini is what comes after that.

---

### Post by gayden on 2012-12-21
sorry for confusion
i need to repair my existing windows 8 for now
and there's no file called boot.ini i've read that it's been replaced with some file called bootmgr
[IMG]http://s7.postimage.org/cxq1s0evf/Screenshot.png[/IMG]
and this is the my whole folder
[IMG]http://s10.postimage.org/kn9zhhpft/Screenshot_D662579462577867_File_Browser.png[/IMG]

---

### Post by haqking on 2012-12-21
> **gayden said:**
> sorry for confusion
i need to repair my existing windows 8 for now
and there's no file called boot.ini i've read that it's been replaced with some file called bootmgr
[IMG]http://s7.postimage.org/cxq1s0evf/Screenshot.png[/IMG]
and this is the my whole folder
[IMG]http://s10.postimage.org/kn9zhhpft/Screenshot_D662579462577867_File_Browser.png[/IMG]

ahh yeah my bad (brain fart, windows 8) well the bootmgr file an be edited.

However it depends if the boot is even seeing that file which might not be the issue.

When you get operating system not found at what stage is it ? is it when you select an entry from the boot menu ? if so which boot menu is it, the one from Windows ? which now points to wrong location when you choose windows 8 ? if so then this can be fixed by editing the bootmgr entries yes ?

---

### Post by gayden on 2012-12-21
there's no boot menu
actually when i need to start BT5 i choose my external hdd to boot first
and when i need windows i start my laptop without my ext hdd
so i get the error after i choose to operate from my internal hdd or when i choose to operate windows 8
i mean that i change the boot order

---

### Post by haqking on 2012-12-21
> **gayden said:**
> there's no boot menu
actually when i need to start BT5 i choose my external hdd to boot first
and when i need windows i start my laptop without my ext hdd
so i get the error after i choose to operate from my internal hdd or when i choose to operate windows 8

OK, so thats because when choosing your internal HDD it looks at the first primary partition which is blank, Windows 8 is on the 3rd primary partition on that drive.

you really would be better using a Windows DVD to repair, borrow one from a friend, or backup your data then do a reinstall.

However you could try the following which may or may not work as I am unfamiliar with Windows 8.

Boot to a Gparted DVD and resize so that Windows 8 (partition 3) now uses the whole drive again.

Then from a Live CD or from Backtrack

```
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update 
sudo apt-get install -y boot-repair 
boot-repair
```Then when options appear use restore mbr.

Before you do anything though, as you have access to the partition from BT, backup your data incase you lose everything

There is a probably a much simpler method to do this, but I am unfamiliar with Windows 8.

Peace

---

### Post by gayden on 2012-12-21
by the way ... windows 8 is the same as windows 7
i didn't find many differences between them

---

### Post by haqking on 2012-12-21
> **gayden said:**
> by the way ... windows 8 is the same as windows 7
i didn't find many differences between them

Are you asking a question ? LOL

There are lots of differences.

Anyways like i said above, resize your Windows 8 partition to be the whole drive by deleting the other partitions (as long as there is nothing in them you want)

Then carry out commands from Live CD or BT as i outlined above

You can use Gparted from the BT or live CD save burning a new CD.

---

### Post by gayden on 2012-12-21
ok i'm trying it out

---

### Post by oldfred on 2012-12-21
Only resize Windows partitions from inside Windows with its MMC. And then reboot immediately so it can run its chkdsk and other fixes to make repairs.

When you deleted Vista, you deleted Windows 8's boot files. Windows only boots from one active partition which we see as the boot flag on the partition on the drive that BIOS uses to boot.

Windows also does not boot from external drives unless you are using eSata or something that looks like an internal drive. Or maybe your booting Vista became a work around. But the license and installer both check for external drives and do not let you install. You probably will not be able to repair if seen as a external drive.

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by haqking on 2012-12-21
> **oldfred said:**
> Only resize Windows partitions from inside Windows with its MMC. And then reboot immediately so it can run its chkdsk and other fixes to make repairs.

When you deleted Vista, you deleted Windows 8's boot files. Windows only boots from one active partition which we see as the boot flag on the partition on the drive that BIOS uses to boot.

Windows also does not boot from external drives unless you are using eSata or something that looks like an internal drive. Or maybe your booting Vista became a work around. But the license and installer both check for external drives and do not let you install. You probably will not be able to repair if seen as a external drive.

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The OP cant resize from within windows, they cant get to Windows.  Windows isnt on an external drive either.  Windows 8 is in the 3rd Primary partition.

If the OP resizes Windows to occupy the whole drive and then repairs the bootloader it "should" work.

---

### Post by oldfred on 2012-12-21
You cannot just fix boot loader in MBR, but then have to fix the PBR or partition boot sector. Windows boots from MBR to PBR. Each NTFS PBR has which boot loader to use, ntldr or bootmgr and the start and size of the NTFS partition that needs to match partition table. If size is changed then you have to run chkdsk to update PBR or else Windows will not boot. And you only can run chkdsk from Windows or a Windows repairCD. 
Is not Windows nice and convoluted?

And the real issue is the boot files bootmgr & BCD are probably missing as they were in the Vista partition.

---

### Post by gayden on 2012-12-21
it didn't work ... the problem occurs when i try to resize the windows 8 partition
also i've noticed that there's an exclamation mark near the partition name
[IMG]http://s12.postimage.org/v3jfqrn3x/Screenshot_dev_sda_GParted.png[/IMG]

here's the saved details file :-
```
GParted 0.5.1
 Libparted 2.2
    **Move /dev/sda3 to the right and shrink it from 97.66 GiB to 97.65 GiB**  00:00:03    ( ERROR )             calibrate /dev/sda3  00:00:00    ( SUCCESS )             [I]path: /dev/sda3
start: 771971072
end: 976771071
size: 204800000 (97.66 GiB)[/I]          calculate new size and position of /dev/sda3  00:00:00    ( SUCCESS )             [I]requested start: 771971445
requested end: 976768064
requested size: 204796620 (97.65 GiB)[/I]       [I]new start: 771971445
new end: 976768064
new size: 204796620 (97.65 GiB)[/I]          check file system on /dev/sda3 for errors and (if possible) fix them  00:00:03    ( ERROR )             ***ntfsresize -P -i -f -v /dev/sda3***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda3
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 104857596416 bytes (104858 MB)
Current device size: 104857600000 bytes (104858 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 9064 (0x2368): missing cluster in $Bitmap
Cluster accounting failed at 32543 (0x7f1f): missing cluster in $Bitmap
Cluster accounting failed at 34260 (0x85d4): extra cluster in $Bitmap
Cluster accounting failed at 49698 (0xc222): extra cluster in $Bitmap
Cluster accounting failed at 50632 (0xc5c8): missing cluster in $Bitmap
Cluster accounting failed at 50633 (0xc5c9): missing cluster in $Bitmap
Cluster accounting failed at 52557 (0xcd4d): missing cluster in $Bitmap
Cluster accounting failed at 229315 (0x37fc3): missing cluster in $Bitmap
Cluster accounting failed at 229316 (0x37fc4): missing cluster in $Bitmap
Cluster accounting failed at 229317 (0x37fc5): missing cluster in $Bitmap
Cluster accounting failed at 229318 (0x37fc6): missing cluster in $Bitmap
Cluster accounting failed at 229319 (0x37fc7): missing cluster in $Bitmap
Cluster accounting failed at 325476 (0x4f764): missing cluster in $Bitmap
Cluster accounting failed at 325477 (0x4f765): missing cluster in $Bitmap
Cluster accounting failed at 325478 (0x4f766): missing cluster in $Bitmap
Cluster accounting failed at 325479 (0x4f767): missing cluster in $Bitmap
Filesystem check failed! Totally 16 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
[/I]             ========================================

```

---

### Post by haqking on 2012-12-21
> **gayden said:**
> it didn't work ... the problem occurs when i try to resize the windows 8 partition
also i've noticed that there's an exclamation mark near the partition name
[IMG]http://s12.postimage.org/v3jfqrn3x/Screenshot_dev_sda_GParted.png[/IMG]

here's the saved details file :-
```
GParted 0.5.1
 Libparted 2.2
    **Move /dev/sda3 to the right and shrink it from 97.66 GiB to 97.65 GiB**  00:00:03    ( ERROR )             calibrate /dev/sda3  00:00:00    ( SUCCESS )             [I]path: /dev/sda3
start: 771971072
end: 976771071
size: 204800000 (97.66 GiB)[/I]          calculate new size and position of /dev/sda3  00:00:00    ( SUCCESS )             [I]requested start: 771971445
requested end: 976768064
requested size: 204796620 (97.65 GiB)[/I]       [I]new start: 771971445
new end: 976768064
new size: 204796620 (97.65 GiB)[/I]          check file system on /dev/sda3 for errors and (if possible) fix them  00:00:03    ( ERROR )             ***ntfsresize -P -i -f -v /dev/sda3***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda3
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 104857596416 bytes (104858 MB)
Current device size: 104857600000 bytes (104858 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 9064 (0x2368): missing cluster in $Bitmap
Cluster accounting failed at 32543 (0x7f1f): missing cluster in $Bitmap
Cluster accounting failed at 34260 (0x85d4): extra cluster in $Bitmap
Cluster accounting failed at 49698 (0xc222): extra cluster in $Bitmap
Cluster accounting failed at 50632 (0xc5c8): missing cluster in $Bitmap
Cluster accounting failed at 50633 (0xc5c9): missing cluster in $Bitmap
Cluster accounting failed at 52557 (0xcd4d): missing cluster in $Bitmap
Cluster accounting failed at 229315 (0x37fc3): missing cluster in $Bitmap
Cluster accounting failed at 229316 (0x37fc4): missing cluster in $Bitmap
Cluster accounting failed at 229317 (0x37fc5): missing cluster in $Bitmap
Cluster accounting failed at 229318 (0x37fc6): missing cluster in $Bitmap
Cluster accounting failed at 229319 (0x37fc7): missing cluster in $Bitmap
Cluster accounting failed at 325476 (0x4f764): missing cluster in $Bitmap
Cluster accounting failed at 325477 (0x4f765): missing cluster in $Bitmap
Cluster accounting failed at 325478 (0x4f766): missing cluster in $Bitmap
Cluster accounting failed at 325479 (0x4f767): missing cluster in $Bitmap
Filesystem check failed! Totally 16 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
[/I]             ========================================

```


Well like  said from the beginning, get hold of some Windows 8 media.  You have access to your data, back it up and reinstall.

And may i suggest cloning your partitions after an install in future, I can flash my system back to one of 100's of different configurations, installs, OS in a matter of minutes.  [www.clonezilla.org](www.clonezilla.org)  

Peace

---

### Post by oldfred on 2012-12-21
Windows 8 normally closes in a hibernated state. Linux will not open Windows if it is hibernated to try to prevent you from damaging it.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by haqking on 2012-12-21
> **oldfred said:**
> Windows 8 normally closes in a hibernated state. Linux will not open Windows if it is hibernated to try to prevent you from damaging it.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

yes but the OP can access his data as he demonstrated above, so they should just back it up and then get hold of some media to reinstall

---

### Post by kiyop on 2012-12-21
I have not read through this whole thread and I do not use Windows 8 nor backtrack5 nor Windows Vista. So I may be wrong. If so, excuse me.

I wonder if the OP can restore Vista's deleted partition by testdisk on backtrack5
```
sudo su -
TYPE ROOT PASSWORD
apt-get update
apt-get install testdisk
testdisk
```And I wonder if boot.ini is not used in Windows 8. AFAIK, boot.ini is used by WIindows XP. Windows Vista, 7 and 8 may use BCD.
[http://windows.microsoft.com/en-GB/windows-vista/What-happened-to-the-boot-ini-file](http://windows.microsoft.com/en-GB/windows-vista/What-happened-to-the-boot-ini-file)

---

### Post by haqking on 2012-12-21
> **kiyop said:**
> I have not read through this whole thread and I do not use Windows 8 nor backtrack5 nor Windows Vista. So I may be wrong. If so, excuse me.

I wonder if the OP can restore Vista's deleted partition by testdisk.

And I wonder if boot.ini is not used in Windows 8. I know that boot.ini is used by WIndows XP and Windows Vista, 7 and 8 use BCD.

Initially possible, after also using Gparted then hope is next to zero ;-) imind you i have recovered allsorts with it before

---

### Post by kiyop on 2012-12-21
I found that you have became aware of bootmgr and BCD.;)
[http://ubuntuforums.org/showthread.php?p=12415518#post12415518](http://ubuntuforums.org/showthread.php?p=12415518#post12415518)
> **haqking said:**
> ahh yeah my bad (brain fart, windows 8) well the bootmgr file an be edited.

However it depends if the boot is even seeing that file which might not be the issue.

When you get operating system not found at what stage is it ? is it when  you select an entry from the boot menu ? if so which boot menu is it,  the one from Windows ? which now points to wrong location when you  choose windows 8 ? if so then this can be fixed by editing the bootmgr  entries yes ?
I will read more in this thread. Thank you.

---

### Post by kiyop on 2012-12-21
I see.
[http://ubuntuforums.org/showpost.php?p=12415560&postcount=21](http://ubuntuforums.org/showpost.php?p=12415560&postcount=21)
> **haqking said:**
> you really would be better using a Windows DVD  to repair, borrow one from a friend, or backup your data then do a  reinstall.

However you could try the following which may or may not work as I am unfamiliar with Windows 8.

Boot to a Gparted DVD and resize so that Windows 8 (partition 3) now uses the whole drive again.

Then from a Live CD or from Backtrack

```
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update 
sudo apt-get install -y boot-repair 
boot-repair
```Then when options appear use restore mbr.

Before you do anything though, as you have access to the partition from BT, backup your data incase you lose everything

There is a probably a much simpler method to do this, but I am unfamiliar with Windows 8.

Peace

I hope that the deleted partition is not so overwritten.

To _[gayden]("http://ubuntuforums.org/member.php?u=1405523")_,

Boot backtrack 5 and execute the following and post the result. You can drug the output and right-click to copy the drugged text and paste it into the posting area.
```
sudo su -
TYPE ROOT PASSWORD
fdisk -lu
grep -A20 menuentry /boot/grub/grub.cfg
grub-install -v
```I wish /boot/BCD formerly in Windows vista partition (or .efi ?... I guess no) file can be recovered.
[http://support.microsoft.com/kb/927392/en](http://support.microsoft.com/kb/927392/en)
for Windows 7 and VISTA not for Windows 8.

And as haqking suggested, boot backtrack 5 (or some live linux) and back up your data in /dev/sda3 to a safe place like a partition in an external HDD or so.

FYI: Executing the following with Windows 7 Recovery environment (Windows 7 install disk and/or Windows 7 system recovery disk)
```
bcdboot.exe c:\windows
```rebuilds /boot/bcd and /bootmgr for Windows 7 on C:.

I found that bcdboot.exe is valid also for Windows 8.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)

There is 
[http://www.prime-expert.com/ebcd/](http://www.prime-expert.com/ebcd/)
I do not know if it is a kind of virus or not, use at your own risk.

---

### Post by gayden on 2012-12-22
@haqking
thanks ... i will use this program in the future

@oldfred
i remember that last time i closed my windows 8 was by restarting not the normal shutdown because i wanted to boot into win vista

@kiyop
this is the result :-
```
root@bt:~# fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2f7083b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3       771971072   976771071   102400000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1236656095   618327024    7  HPFS/NTFS
/dev/sdb2      1236656126  1339056127    51200001    5  Extended
/dev/sdb3      1748658176  1953454079   102397952    7  HPFS/NTFS
/dev/sdb5      1236656128  1248376831     5860352   82  Linux swap / Solaris
/dev/sdb6      1248378880  1339056127    45338624   83  Linux
root@bt:~# grep -A20 menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 3.2.6' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    linux    /boot/vmlinuz-3.2.6 root=UUID=b5824553-9b99-4b83-b7d0-b69e4a2cae1b ro   text splash vga=791
    initrd    /boot/initrd.img-3.2.6
}
menuentry 'Ubuntu, with Linux 3.2.6 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    echo    'Loading Linux 3.2.6 ...'
    linux    /boot/vmlinuz-3.2.6 root=UUID=b5824553-9b99-4b83-b7d0-b69e4a2cae1b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.6
}
menuentry 'Ubuntu, with Linux 2.6.39.4' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=b5824553-9b99-4b83-b7d0-b69e4a2cae1b ro   text splash vga=791
    initrd    /boot/initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.39.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    echo    'Loading Linux 2.6.39.4 ...'
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=b5824553-9b99-4b83-b7d0-b69e4a2cae1b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39.4
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set b5824553-9b99-4b83-b7d0-b69e4a2cae1b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
root@bt:~# grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu13)
```

---

### Post by kiyop on 2012-12-22
Thanks for your report :)

I want to confirm what you have done with the internal HDD, which is recognized with /dev/sda:
> **gayden said:**
> windows 8 made an update automatically which affected windows vista
and after i fixed it ... i removed windows vista accidentally then windows 8 stopped working
and after that i tried to burn my backup into a usb but then it gave me an error code which is 0x80070241 ... then i tried to burn it into a dvd ... and i've found my hdd parition formatted so i need to recover all the removed files with a program on windows 8 then i'll try to install windows vista again
The following is my guess. Are the following and its order correct?
1) Windows 8 made an update automatically, which resulted in a problem with windows vista.
2) You fixed the problem.
3) You removed windows vista accidentally.
4) Windows 8 stopped working.
5) You tried to burn your backup into a usb but it gave an error code 0x80070241.
6) You tried to burn your backup into a dvd.
7) You found your hdd partition formatted.
8) You booted Backtrack5 and executed "sudo update-grub".
9) [You tried resizing /dev/sda3 (windows 8 system partition). But the resizing failed]("http://ubuntuforums.org/showthread.php?p=12416111#post12416111").

What does "stopped working" in 4) mean?
Did Windows 8 freeze? Or Windows 8 did not boot after reboot?
 After 4), did you reboot the computer? 
If you rebooted, on what OS did you execute 5) and 6)?
At 5), what is "a usb"? External HDD containing backtrack5? Or another USB media?
At 7), what is "your hdd partition"? /dev/sda1 and /dev/sda2 (Vista partitions)?
After 7), [you did not install ubuntu]("http://ubuntuforums.org/showthread.php?p=12415362#post12415362"), did you?

At [16th post]("http://ubuntuforums.org/showthread.php?p=12415507#post12415507"), there is [an image]("http://s10.postimage.org/kn9zhhpft/Screenshot_D662579462577867_File_Browser.png") showing that there is bootmgr in a 105GB partition. The 105GB partition is Windows 8 system partition = /dev/sda3, isn't it?
And in the image, there is 145GB partition. Is it /dev/sda2? When was the image taken? Before you deleted /dev/sda1 and /dev/sda2?

After 7), you did not change the partition, did you?

> **gayden said:**
> ```
root@bt:~# fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2f7083b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3       771971072   976771071   102400000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1236656095   618327024    7  HPFS/NTFS
/dev/sdb2      1236656126  1339056127    51200001    5  Extended
/dev/sdb3      1748658176  1953454079   102397952    7  HPFS/NTFS
/dev/sdb5      1236656128  1248376831     5860352   82  Linux swap / Solaris
/dev/sdb6      1248378880  1339056127    45338624   83  Linux

```
What are /dev/sdb1 and /dev/sdb3?
/dev/sda3 does not have "boot flag". If you add boot flag to /dev/sda3 by gparted on Backtrack5, BIOS will try loading /dev/sda3 boot sector. The situations may change, but I guess Windows 8 will not boot because there is not /boot/BCD in /dev/sda3. 

> **gayden said:**
> this is what sudo parted -l gave me :-
```
root@bt:~# sudo parted -l
Model: ATA TOSHIBA MK5075GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary
 2      250GB   395GB  145GB  primary  ntfs
 3      395GB   500GB  105GB  primary  ntfs


Model: WD My Passport 0740 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  633GB   633GB   primary                   boot
 2      633GB   686GB   52.4GB  extended
 5      633GB   639GB   6001MB  logical   linux-swap(v1)
 6      639GB   686GB   46.4GB  logical   ext4
 3      895GB   1000GB  105GB   primary   ntfs

```
When the above "sudo parted -l" was executed, there is a trace of information on the deleted /dev/sda1 (250GB) and /dev/sda2 (145GB), which seems strange for me.

I suggest you using testdisk on Backtrack5 in order to recover the deleted /dev/sda1 and /dev/sda2.
How to use testdisk is written at;
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You can start testdisk by executing on Backtrack5;
```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```Furthermore, you can check if the backup boot sector of the deleted partition is still at the expected last sector of the deleted partition by executing
```
sudo dd if=/dev/sda bs=512 count=1 skip=771971071 2>/dev/null|hd
```> **gayden said:**
> ```

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###
```
Did you execute "sudo update-grub" at 8)?
It did not detect Windows 8 installed on /dev/sda3, which seems natural because /dev/sda3 does not contain /boot/BCD. /boot/BCD might have been in the deleted /dev/sda1 or /dev/sda2.

> **gayden said:**
> ```

grub-install (GNU GRUB 1.98-1ubuntu13)
```
I am more familiar with this version of Grub2; 1.98. Do not upgrade grub2 to version 1.99 or higher.

As my note:
> **gayden said:**
> 
The problem is that i've lost my windows cd
and i was having a backup for it in my hdd which got formated by mistake

(snip by kiyop)

no i didn't delete the partition which contains windows 8

---

### Post by gayden on 2012-12-24
> **kiyop said:**
> Thanks for your report :)

I want to confirm what you have done with the internal HDD, which is recognized with /dev/sda:

The following is my guess. Are the following and its order correct?
1) Windows 8 made an update automatically, which resulted in a problem with windows vista.
2) You fixed the problem.
3) You removed windows vista accidentally.
4) Windows 8 stopped working.
5) You tried to burn your backup into a usb but it gave an error code 0x80070241.
6) You tried to burn your backup into a dvd.
7) You found your hdd partition formatted.
8) You booted Backtrack5 and executed "sudo update-grub".
9) [You tried resizing /dev/sda3 (windows 8 system partition). But the resizing failed]("http://ubuntuforums.org/showthread.php?p=12416111#post12416111").
yeah that's the right order
> **kiyop said:**
> What does "stopped working" in 4) mean?
Did Windows 8 freeze? Or Windows 8 did not boot after reboot?
no it means that it didn't boot at all as it gave me that error which i mentioned before
at the beginning it was telling me bootmgr is not found
but after i deleted the partition which includes win vista it told me operating system not found
i mean that when win vista's partition was still there with no data it gave me the first error and when i deleted the partition it gave me the second
and also if i created the deleted partition again it would give me the second error i guess
and if so , would copying files from win 8's partition to that partition work ?! "imma give it a try"
 > **kiyop said:**
> After 4), did you reboot the computer? 
If you rebooted, on what OS did you execute 5) and 6)?
it told me "bootmgr is not found press Alt+Ctrl+Del to restart" so i did so and i rebooted to BT5 and done 5 and 6 from them
and after that i tried to execute it from the bios but the ext hdd which includes BT5 wasn't plugged in so i guess that it was executed by win 8 , even though i still don't know as i don't exactly get it xD i dunno if u are talking about either the burning process or the starting process
> **kiyop said:**
> At 5), what is "a usb"? External HDD containing backtrack5? Or another USB media?
no i meant a 4GB usb stick which shown in the following pic
[IMG]http://di1-4.shoppingshadow.com/images/pi/64/e5/d8/107658659-260x260-0-0_sandisk+sandisk+cruzer+micro+4gb+usb+2+0+flash+dri.jpg[/IMG]
> **kiyop said:**
> At 7), what is "your hdd partition"? /dev/sda1 and /dev/sda2 (Vista partitions)?
no i meant my ext hdd partition which includes all my backups
which is /dev/sdb1
> **kiyop said:**
> After 7), [you did not install ubuntu]("http://ubuntuforums.org/showthread.php?p=12415362#post12415362"), did you?
no i didn't as we were trying other solutions
> **kiyop said:**
> At [16th post]("http://ubuntuforums.org/showthread.php?p=12415507#post12415507"), there is [an image]("http://s10.postimage.org/kn9zhhpft/Screenshot_D662579462577867_File_Browser.png") showing that there is bootmgr in a 105GB partition. The 105GB partition is Windows 8 system partition = /dev/sda3, isn't it?
yeah it is
> **kiyop said:**
> And in the image, there is 145GB partition. Is it /dev/sda2? When was the image taken? Before you deleted /dev/sda1 and /dev/sda2?
the 145GB partition is the DATA partition in windows
it includes my normal data which i have a backup for
i mean by normal data the documents , music and such things
it's also called D drive in windows
the image was taken before i deleted the partition on sda2
by the way ... the partition on sda1 was already deleted
> **kiyop said:**
> After 7), you did not change the partition, did you?
i didn't change anything in my ext hdd after 7

> **kiyop said:**
> What are /dev/sdb1 and /dev/sdb3?
/dev/sda3 does not have "boot flag". If you add boot flag to /dev/sda3 by gparted on Backtrack5, BIOS will try loading /dev/sda3 boot sector. The situations may change, but I guess Windows 8 will not boot because there is not /boot/BCD in /dev/sda3. 
sdb is my ext hdd which includes BT5 but there are many partitions :S 1 is for my backed up data and it has been formatted and 3 is for my installed programs and the others are for BT5
actually i've noticed that very early and checked "Bootable" in disk utility as it gave me this error but i forgot to mention that here <=-P sorry for that
[IMG]http://s14.postimage.org/3oiawebe9/Screenshot_Untitled_Window.png[/IMG]
```
Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=395249188864, new_start=395249188864, new_size=104857600000, type=0x07
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 395249188864, size 104857600000, type 0x07)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
got partition
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
new_size=104857600000 but resulting size, 104855869440, smaller than requested
Error: Can't have a partition outside the disk!
changed partition to start=32256 size=500105217024
committed to disk
ugh, offset or size changed
offset:     395249188864
size:       104857600000
new_offset: 32256
new_size:   500105217024

```but imma try it now with gparted and give you the result
i dunno what exactly BCD is <=-P but i think that because bootmgr is there it must boot when "bootable" is checked in disk utility

> **kiyop said:**
>  When the above "sudo parted -l" was executed, there is a trace of information on the deleted /dev/sda1 (250GB) and /dev/sda2 (145GB), which seems strange for me.
actually this is what sudo parted -l gave to me now :-
```
root@bt:~# sudo parted -l
Model: ATA TOSHIBA MK5075GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 3      32.3kB  500GB  500GB  primary  ext2         boot


Model: WD My Passport 0740 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  633GB   633GB   primary                   boot
 2      633GB   686GB   52.4GB  extended
 5      633GB   639GB   6001MB  logical   linux-swap(v1)
 6      639GB   686GB   46.4GB  logical   ext4
 3      895GB   1000GB  105GB   primary   ntfs


Error: /dev/sr0: unrecognised disk label          
```> **kiyop said:**
> I suggest you using testdisk on Backtrack5 in order to recover the deleted /dev/sda1 and /dev/sda2.
How to use testdisk is written at;
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You can start testdisk by executing on Backtrack5;
```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```
ok i'll give it a try
> **kiyop said:**
> Furthermore, you can check if the backup boot sector of the deleted partition is still at the expected last sector of the deleted partition by executing
```
sudo dd if=/dev/sda bs=512 count=1 skip=771971071 2>/dev/null|hd
```
well here's the result :-
```
root@bt:~# sudo dd if=/dev/sda bs=512 count=1 skip=771971071 2>/dev/null|hd
00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

```> **kiyop said:**
> Did you execute "sudo update-grub" at 8)?
It did not detect Windows 8 installed on /dev/sda3, which seems natural because /dev/sda3 does not contain /boot/BCD. /boot/BCD might have been in the deleted /dev/sda1 or /dev/sda2.
yes ... as fdrake told me
anyways i've found many interesting things
i've searched for BCD in win 8's partition as i've found those files in this pictures


[IMG]http://s8.postimage.org/edo1kbqr9/Screenshot_Search_for_BCD_File_Browser.png[/IMG]


but the more interesting are those highlighted files


[IMG]http://s9.postimage.org/e83pa2h0v/Screenshot_Search_for_BCD_File_Browser_1.png[/IMG]


and the most interesting thing is exactly this file "bcdinfo.txt" which includes all the boot information and i think that editing it would help anyways i won't edit anything except if you told me to
```
 
Windows Boot Manager 
-------------------- 
identifier              {bootmgr} 
device                  partition=C: 
description             Windows Boot Manager 
locale                  en-US 
inherit                 {globalsettings} 
integrityservices       Enable 
default                 {default} 
resumeobject            {4a986386-d17a-11e1-909c-d41a34e8d60d} 
displayorder            {default} 
                        {33fcdb64-6be7-11e1-8e6d-9d952d699748} 
toolsdisplayorder       {memdiag} 
timeout                 30 
 
Windows Boot Loader 
------------------- 
identifier              {33fcdb64-6be7-11e1-8e6d-9d952d699748} 
device                  partition=C: 
path                    \Windows\system32\winload.exe 
description             Microsoft Windows Vista 
locale                  en-US 
inherit                 {bootloadersettings} 
osdevice                partition=C: 
systemroot              \Windows 
resumeobject            {33fcdb65-6be7-11e1-8e6d-9d952d699748} 
nx                      OptIn 
 
Windows Boot Loader 
------------------- 
identifier              {default} 
device                  partition=E: 
path                    \Windows\system32\winload.exe 
description             Windows 8 
locale                  en-US 
inherit                 {bootloadersettings} 
recoverysequence        {current} 
integrityservices       Enable 
recoveryenabled         Yes 
allowedinmemorysettings 0x15000075 
osdevice                partition=E: 
systemroot              \Windows 
resumeobject            {4a986386-d17a-11e1-909c-d41a34e8d60d} 
nx                      OptIn 
bootmenupolicy          Standard 
 
Windows Boot Loader 
------------------- 
identifier              {current} 
device                  ramdisk=[C:]\Recovery\4a986388-d17a-11e1-909c-d41a34e8d60d\Winre.wim,{4a986389-d17a-11e1-909c-d41a34e8d60d} 
path                    \windows\system32\winload.exe 
description             Windows Recovery Environment 
locale                  en-US 
inherit                 {bootloadersettings} 
displaymessage          Recovery 
osdevice                ramdisk=[C:]\Recovery\4a986388-d17a-11e1-909c-d41a34e8d60d\Winre.wim,{4a986389-d17a-11e1-909c-d41a34e8d60d} 
systemroot              \windows 
nx                      OptIn 
bootmenupolicy          Standard 
winpe                   Yes 
 
Resume from Hibernate 
--------------------- 
identifier              {33fcdb65-6be7-11e1-8e6d-9d952d699748} 
device                  partition=C: 
path                    \Windows\system32\winresume.exe 
description             Windows Resume Application 
locale                  en-US 
inherit                 {resumeloadersettings} 
filedevice              partition=C: 
filepath                \hiberfil.sys 
pae                     Yes 
debugoptionenabled      No 
 
Resume from Hibernate 
--------------------- 
identifier              {4a986386-d17a-11e1-909c-d41a34e8d60d} 
device                  partition=E: 
path                    \Windows\system32\winresume.exe 
description             Windows Resume Application 
locale                  en-US 
inherit                 {resumeloadersettings} 
recoverysequence        {current} 
recoveryenabled         Yes 
allowedinmemorysettings 0x15000075 
filedevice              partition=E: 
filepath                \hiberfil.sys 
bootmenupolicy          Standard 
pae                     Yes 
debugoptionenabled      No 
 
Windows Memory Tester 
--------------------- 
identifier              {memdiag} 
device                  partition=C: 
path                    \boot\memtest.exe 
description             Windows Memory Diagnostic 
locale                  en-US 
inherit                 {globalsettings} 
badmemoryaccess         Yes 
 
Windows Legacy OS Loader 
------------------------ 
identifier              {ntldr} 
device                  partition=C: 
path                    \ntldr 
description             Earlier Version of Windows 
 
EMS Settings 
------------ 
identifier              {emssettings} 
bootems                 No 
 
Debugger Settings 
----------------- 
identifier              {dbgsettings} 
debugtype               Serial 
debugport               1 
baudrate                115200 
 
RAM Defects 
----------- 
identifier              {badmemory} 
 
Global Settings 
--------------- 
identifier              {globalsettings} 
inherit                 {dbgsettings} 
                        {emssettings} 
                        {badmemory} 
 
Boot Loader Settings 
-------------------- 
identifier              {bootloadersettings} 
inherit                 {globalsettings} 
                        {hypervisorsettings} 
 
Hypervisor Settings 
------------------- 
identifier              {hypervisorsettings} 
hypervisordebugtype     Serial 
hypervisordebugport     1 
hypervisorbaudrate      115200 
 
Resume Loader Settings 
---------------------- 
identifier              {resumeloadersettings} 
inherit                 {globalsettings} 
 
Device options 
-------------- 
identifier              {4a986389-d17a-11e1-909c-d41a34e8d60d} 
description             Windows Recovery 
ramdisksdidevice        partition=C: 
ramdisksdipath          \Recovery\4a986388-d17a-11e1-909c-d41a34e8d60d\boot.sdi
```> **kiyop said:**
> I am more familiar with this version of Grub2; 1.98. Do not upgrade grub2 to version 1.99 or higher.

As my note:
ok i won't update anything

---

### Post by kiyop on 2012-12-24
Thanks for the above reply of yours.

But.... UNFORTUNATELY, you resized /dev/sda3 to the empty place where the former /dev/sda1 and /dev/sda2 occupied before resizing.
What a silly thing you did!!! Why did haqking suggest such a silly thing!!!??? :( :cry:
<<EDIT after the next post of haqking was posted>>

Maybe you lost a very good chance to recover.

You mentioned that you do not have Windows 8 installer DVD.

> **gayden said:**
> actually this is what sudo parted -l gave to me now :-
```
root@bt:~# sudo parted -l
Model: ATA TOSHIBA MK5075GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 3      32.3kB  500GB  500GB  primary  ext2         boot

```
But there are many possible ways to make Windows 8 bootable.

First, the information "parted -l" gave may be wrong.

---

### Post by haqking on 2012-12-24
> **kiyop said:**
> Thanks for the above reply of yours.

But.... UNFORTUNATELY, you resized /dev/sda3 to the empty place where the former /dev/sda1 and /dev/sda2 occupied before resizing.
What a silly thing you did!!! Why did fdrake suggest such a silly thing!!!???
Maybe you lost a very good way to recover.

I suggested it, however i said "you could try" and i told them to back up the data first as the OP had access to that partition with the data on.

In the time this thread has been going the OP could of reinstalled Vista or got a Windows 8 disc to repair.

Moral of the story, have clones/images and backups of data.

---

### Post by kiyop on 2012-12-24
Thanks haqking to the above post of yours.
I made a mistake about "fdrake". Excuse me, especially fdrake.:oops:

Now... it is difficult to support him.

I am not sure if [http://www.prime-expert.com/ebcd/](http://www.prime-expert.com/ebcd/) does not include malware.

---

### Post by gayden on 2012-12-24
i backed up the data before i erased the partitions

---

### Post by gayden on 2012-12-24
check out this it may help
[http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx)

---

### Post by haqking on 2012-12-24
> **gayden said:**
> i backed up the data before i erased the partitions

so all you need then is to reinstall Windows 8 or Vista.

Get hold of some media and do so, as far as i can tell none of this has been a Linux related issue of any type or involves Linux as BT is on an external drive

---

### Post by gayden on 2012-12-24
the only way to get hold of some media is to be able to run win 8 again
because i will then recover all the data on my ext hdd including the backups

---

### Post by kiyop on 2012-12-24
> **gayden said:**
> i backed up the data before i erased the partitions
What did you back up?
/boot/BCD may be in small boot partition.

In the extended Windows 8 system partition (500GB), there are 3 BCD files. Where are the 3 BCD files?
And also, there are BCDboot.exe and BCDedit.ext. If you can run it on Windows 8 circumstance, it will rebuild /boot/BCD. Wine may be able to run the two files, but it is not on Windows 8 circumstance.

If only you had not resize /dev/sda3, testdisk might have helped you. It was a pity that you resized /dev/sda3.

Excuse me, gayden. I am not familiar with Windows 8. :(
I do not want to read through and understand whole of [http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx") just in order to help you. I do not have such free spare time now.

You may get better answer in windows 8 forum. 
 
Good luck.

---

### Post by oldfred on 2012-12-24
Lets just run the BootInfo report to see what is installed where. This finds all boot files from all installed systems.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by gayden on 2012-12-25
would this help ?!
windows 7 32-bit repair disk

---

