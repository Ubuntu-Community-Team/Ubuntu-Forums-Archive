---
title: "internal hd not loading"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-17
I tweaked my fstab file, but as far as I can recollect, it's back the same way it was before I tweaked it (used a reloaded backup copy)

But now my internal windows hd (dev/hda1) won't mount at all sudo mount, etc.

here's the fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
UUID=9858328CE07FB76E /media/i80 ntfs    defaults,nls=utf8,umask=007,gid=46        0       1
#  /dev/sda3  swap
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
# cdroms
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
# /dev/sdc1 --VFAT External Travel Drive 2bb
#UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1


#UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1
```

any ideas?  Fornutanately,  I can still boot (with external hd), but can't access that internal hd at all for now.

When I try to mount it I get this

mount: special device /dev/disk/by-uuid/9858328CE07FB76E does not exist

---

### Post by mikeyphi on 2007-08-17
Is the NTFS configuration tool, under Applications/System Tools, activated?

SORRY!! - Ignore the above, that tool is in the 'Gutsy' version!!

You'll find good advice about the correct fstab entry here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by johntkucz on 2007-08-17
> **mikeyphi said:**
> Is the NTFS configuration tool, under Applications/System Tools, activated?

SORRY!! - Ignore the above, that tool is in the 'Gutsy' version!!

You'll find good advice about the correct fstab entry here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


thanks for the reference mikey, i make the psychocat changes and when try to mount -a

get

```
 wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by johntkucz on 2007-08-17
this didn't look to pleasing

```
kooz@kooz-laptop:~$ dmesg | tail
[ 8206.020000] Buffer I/O error on device sdd1, logical block 238472
[ 8206.020000] lost page write due to I/O error on sdd1
[ 9160.912000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 9160.912000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 9160.912000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 9160.912000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[ 9308.124000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 9308.124000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 9308.124000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 9308.124000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
kooz@kooz-laptop:~$ 


```

---

### Post by Inxsible on 2007-08-17
can you post the output of the following command

```
sudo fdisk -l
```-l is lowercase L. Also, do you have ntfs-3g installed?

NTFS-3g needs to be installed to be able to write to NTFS drives. Read capability is built in.

---

### Post by mikeyphi on 2007-08-17
Does that message mean that you have damaged/altered the MBR file on your windows drive??
If so you should be able to get back into windows with a recovery disc and the "fix mbr" command.
Bear in mind that if you do that you will have to reinstall Grub.

---

### Post by Inxsible on 2007-08-17
try a chkdsk before you fix MBR. Maybe a chkdsk from Windows might rectify the errors.

---

### Post by johntkucz on 2007-08-18
> **Inxsible said:**
> can you post the output of the following command

```
sudo fdisk -l
```-l is lowercase L. Also, do you have ntfs-3g installed?

NTFS-3g needs to be installed to be able to write to NTFS drives. Read capability is built in.

Sure, if I # comment out two lines in fstab the external flash loads .

sudo fdisk 
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7944    63810148+  83  Linux
/dev/sdb2            7945        9768    14651280   83  Linux
/dev/sdb3            9769       10011     1951897+  82  Linux swap / Solaris

Disk /dev/sdd: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         232     1863508+   b  W95 FAT32
/dev/sdc2             233         250      144585    5  Extended
/dev/sdc5             233         250      144553+  82  Linux swap / Solaris
kooz@kooz-laptop:~$ 


```


fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
#/dev/hda1 /media/i80  ntfs    nls=utf8,umask=0222 0       1
# /dev/sda3
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

#/dev/sdc1 /media/e2 vfat iocharset=utf8,umask=000 0 0
```


The main problem is 
#/dev/hda1 /media/i80  ntfs    nls=utf8,umask=0222 0       1

Also, unless

#/dev/sdc1 /media/e2 vfat iocharset=utf8,umask=000 0 0[/CODE] 

is the way it is -- commented out, it says "You are not privileged to mount this volume" whenever I insert the flash.  Again, with the above commented out, the flash works, though.

---

### Post by johntkucz on 2007-08-18
You know I love ubuntu because you can "CHANGE ANYTHING".  However, from my experience, whenever I try to change "Anything" EVERYTHING gets ****** up! 

Blast!

You can' t customize how your external drives load in windows, but you can in ubuntu, but I can't make that "work" in ubuntu -- along with the hundreds of other cool fixits I've done.

---

### Post by johntkucz on 2007-08-18
> **mikeyphi said:**
> Does that message mean that you have damaged/altered the MBR file on your windows drive??
If so you should be able to get back into windows with a recovery disc and the "fix mbr" command.
Bear in mind that if you do that you will have to reinstall Grub.

I don't know what MBR is.  How do you reinstall grub? My grub boot already is zany.  I have to hae the external boot drive loaded only (all other drives loaded will result in an error 21) then I can plug in my other external drives after the menu.lst boot menu.

---

### Post by johntkucz on 2007-08-18
In short, my system feels very "teetering"  a fresh grub reinstall might improve things, or it might royall f things up.  Don't want to risk it.

---

### Post by johntkucz on 2007-08-18
The problem originates with permissions!! WTF! This is my laptop - how the hell can I run into being "locked" out so frequently with my own, god damn computer!  Arg!:mad:.  ANY drive I manually mount (like

sudo mount -t vfat /dev/sdd /media/e1

is read-only.  I've tweaked a ton of the various options, too...

    nls=utf8,umask=0222 0       1

etc.  Whenever I have entered specifics about hwo the drive should, load, I'm met with idiotic permission exclussions.  WheneverI manually plug in the external drive and let the machien handle it, permissions work (are rw).

---

### Post by johntkucz on 2007-08-18
> **Inxsible said:**
> try a chkdsk before you fix MBR. Maybe a chkdsk from Windows might rectify the errors.


Whenever I try to boot from the internal I get Error 13: invalid or unsupported format (that's after the menu.lst screen.

---

### Post by johntkucz on 2007-08-18
> **Inxsible said:**
> try a chkdsk before you fix MBR. Maybe a chkdsk from Windows might rectify the errors.

umm... no idea what chkdsk is -- doesn't have a man page.

---

### Post by johntkucz on 2007-08-18
hello!!! Anyone have any ideas?

---

### Post by johntkucz on 2007-08-18
> **Inxsible said:**
> can you post the output of the following command

```
sudo fdisk -l
```-l is lowercase L. Also, do you have ntfs-3g installed?

NTFS-3g needs to be installed to be able to write to NTFS drives. Read capability is built in.

um thanks inxs... however I dont care about writing to the drive now, I just want to read it at least. i've never been able to write to the internal ntfs.

---

### Post by johntkucz on 2007-08-18
strangley

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/hda /media/e2

```

doesn't produce any errors, but doesn't mount the drive either.

---

### Post by johntkucz on 2007-08-18
> **johntkucz said:**
> umm... no idea what chkdsk is -- doesn't have a man page.


oh, I cna't even boot to windows.

---

### Post by johntkucz on 2007-08-18
STrangely,

Whenever I pull the command 
sudo gedit /etc/fstab

the command terminal spews this:

```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
kooz@kooz-laptop:~$ 


```

---

### Post by logos34 on 2007-08-18
You need the **XP install CD** to boot into recovery console so you can run **chkdsk /r**.   Then  you can do **fixmbr** to restore the windows bootloader, and after that reinstall Grub to the usb hard drive.  (where it should be so you can boot the internal when it's not connected)

---

### Post by johntkucz on 2007-08-19
> **logos34 said:**
> You need the **XP install CD** to boot into recovery console so you can run **chkdsk /r**.   Then  you can do **fixmbr** to restore the windows bootloader, and after that reinstall Grub to the usb hard drive.  (where it should be so you can boot the internal when it's not connected)

hhmm....okay, sounds nifty, but a bit complicated.  Thanks for clarifying all that.  If I can do all those steps, I might be in theclear.

However...My windows xp cd is some gateway recovery disk that doesnt' have any chkdsk options.  

also, how do I just install grub from the ubuntu livecid (how do you "just' restore the windows botoloader, too.  I don't want to erase data trying to reinstall the bootloader and/or grub. Thanks a ton fro clarifying all that, though.

---

### Post by johntkucz on 2007-08-19
hey logos thanks again for those lucid directions (you really seem to know my situations), I am still researching fixmbr and chkdsk and whatnot, but how do I reinstall grub targetting only the external usb drive?  I mean, that's where I installed ubuntu, but grub somehow still got installed on the internal.

---

### Post by johntkucz on 2007-08-19
> **logos34 said:**
> You need the **XP install CD** to boot into recovery console so you can run **chkdsk /r**.   Then  you can do **fixmbr** to restore the windows bootloader, and after that reinstall Grub to the usb hard drive.  (where it should be so you can boot the internal when it's not connected)

would i want to run a chkdsk /f, too?  i see that /r implies /p (the exhaustive check, which is good).

---

### Post by johntkucz on 2007-08-19
okay, logos,

my Windows XP gateway recovery disk (that came with the laptop), when I boot off of it, it behaves, shall we say, a bit loony.

I press R to boot into recovery mode and then you have to wait (literally) for 10 minutes before it shows the boot recovery green and whit screen interface, whereby it has alreay jumped over the "Select Recovery Option" and displays a dialog saying that this action will delete the partition and all user data files with only a select OK option, so I rebooted.  In other words, I can't seem to access a recovery console or recovery options from the boot disk.  How can I do that?  Thanks.

---

### Post by johntkucz on 2007-08-19
okay, logos,

my Windows XP gateway recovery disk (that came with the laptop), when I boot off of it, it behaves, shall we say, a bit loony.

I press R to boot into recovery mode and then you have to wait (literally) for 10 minutes before it shows the boot recovery green and whit screen interface, whereby it has alreay jumped over the "Select Recovery Option" and displays a dialog saying that this action will delete the partition and all user data files with only a select OK option, so I rebooted.  In other words, I can't seem to access a recovery console or recovery options from the boot disk.  How can I do that?  Thanks.

---

### Post by logos34 on 2007-08-19
> **johntkucz said:**
> okay, logos,

my Windows XP gateway recovery disk (that came with the laptop), when I boot off of it, it behaves, shall we say, a bit loony.

I press R to boot into recovery mode and then you have to wait (literally) for 10 minutes before it shows the boot recovery green and whit screen interface, whereby it has alreay jumped over the "Select Recovery Option" and displays a dialog saying that this action will delete the partition and all user data files with only a select OK option, so I rebooted.  In other words, I can't seem to access a recovery console or recovery options from the boot disk.  How can I do that?  Thanks.

never used a gateway recovery disk...The two most common ways to run chkdsk /r (/r implies /f) is to use the Xp install disk or something that will allow you to get to the console like an MS-DOS Boot disk (there's a little checkbox in the A: floppy drive in Windows for making one but hardly anyone ever does these days).  

You should be able to easily reinstall Grub to the mbr of the external drive using the live cd...lemme read back over this thread real quick...be back

---

### Post by yogo on 2007-08-20
Just trying to simplify and clarify things. Below is a copy of my MBR. Assuming John fixes his MBR, really this is only removing the line addressing the dual boot part, and reinstalling GRUB is only adding a line of text back to the MBR  that boots the Kernel first.

Correct me if I am wrong...?
 For example, mine below, if the text in bold is removed, then the Grub bootloader would not be loaded?


;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="OS for testing new boot screen" /FASTDETECT /NOEXECUTE=OPTIN** /KERNEL=NewBoot.exe**

---

### Post by logos34 on 2007-08-20
So correct me if I'm wrong:  grub is on the internal drive, you can boot to the grub menu screen and into ubuntu on the external usb hard disk (sdb1) but not into windows ([error 13]("http://users.bigpond.net.au/hermanzone/p15.htm#13")), nor can you mount windows/hda1 in linux.  

If you can't run chkdsk I'd suggest you either get TestDisk (see error 13 link above) to try and fix it OR go ahead an reinstall the windows bootloader to the drive in the hope that you will at least be able to boot into windows directly, if not mount it in linux.  But I'd first try installing Grub to the external usb hard disk because restoring the windows bootloader will overwrite grub and lock you out of linux, forcing you to use the live cd. 

So do you want to try installing grub to the mbr of the external drive and see if you boot to it directly (change the bios boot order) and into ubuntu?

---

### Post by johntkucz on 2007-08-20
> **yogo said:**
> Just trying to simplify and clarify things. Below is a copy of my MBR. Assuming John fixes his MBR, really this is only removing the line addressing the dual boot part, and reinstalling GRUB is only adding a line of text back to the MBR  that boots the Kernel first.

Correct me if I am wrong...?
 For example, mine below, if the text in bold is removed, then the Grub bootloader would not be loaded?


;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="OS for testing new boot screen" /FASTDETECT /NOEXECUTE=OPTIN** /KERNEL=NewBoot.exe**]]
hey yogo, thanks for the input but I really don't know how to do things you speak of.

great, so I have to do some bootstrapping..:) hehe.

1.  Is the MBR a file like /etc/fstab that I can edit from ubuntu?
      a.  if so, how, and where is it?
2. How do I access "recovery mode" from the gateway partition? It seems to not offer any options other than erasing (formatting) the internal internal hd.
3.  I though all of this reinstallation stuff of grub and mbr was automatic, how do I reinstall those files -- do I simply edit a text file?

---

### Post by logos34 on 2007-08-20
john,

I'm not sure what yogo is referring to...I mena it could be something to do with the boot.ini file or it could be something else,

Do this: download the Super Grub disk right now ([here]("http://forjamari.linex.org/frs/?group_id=61")--sgd_0.9598.iso.bz2), extract it and burn it to CD.  It's a small download.  You can use it to try to boot windows and to restore the windows bootloader.

---

### Post by yogo on 2007-08-20
[quote=logos34;3219702]john,

I'm not sure what yogo is referring to...I mena it could be something to do with the boot.ini file or it could be something else,
/quote]


Yes I was referring to the boot.ini.

John, as for editing the boot.ini, it is easy if you can load Windows, then you would just right click on my computer, choose properties, click advanced, and under the start up, choose settings and the click edit to edit in notepad, however if you can not boot into windows, then you would need to use a recovery CD as logos said.


Use  the steps to edit the boot.ini above AFTER you download what Logos said for loading Windows.


HTMS

---

