---
title: "BOOTMGR is missing after CrunchBang install."
date: 2013-01-01
forum: Any Other OS
---

### Post by Jizztasto on 2013-01-01
Hello everyone, I have a small problem, one that I'm sure can be resolved here as there is a great wealth of knowledge in this community.
So, someone recommended I tried CrunchBang, I also wanted to because I found Mint pretty boring after a while.

Now, to the problem; I was told that it's fine to install GRUB to the MBR since you can always add Windows to the menu afterwards, so I did.
I've added Windows 7 to the GRUB menu and now I receive the following error when I attempt to boot into Windows from GRUB:
[IMG]http://images.wondershare.com/topic/computer-help/bootmgr-is-missing.png[/IMG]

I've tried using my Windows repair disk to fix the boot with bootrec like so:
```

bootrec /fixboot

```It was unable to find the drive so it seems, I received an error stating the device isn't ready.
Does anyone have any ideas? I would be truly grateful. Thank you!

---

### Post by oldfred on 2013-01-01
Bootmgr missing is a Windows error. Did you overwrite the Windows boot partition?

This will not fix Windows, but will show us what may be wrong. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Jizztasto on 2013-01-02
> **oldfred said:**
> Bootmgr missing is a Windows error. Did you overwrite the Windows boot partition?

This will not fix Windows, but will show us what may be wrong. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Am I able to install it in CrunchBang and use it through there or will I have to use Ubuntu?
With CrunchBang I encountered a 404:
```

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/wheezy/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/wheezy/main/binary-amd64/Packages  404  Not Found

```

---

### Post by kiyop on 2013-01-02
> **Jizztasto said:**
> Am I able to install it in CrunchBang and use it through there or will I have to use Ubuntu?
With CrunchBang I encountered a 404:
```

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/wheezy/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/wheezy/main/binary-amd64/Packages  404  Not Found

```
You can easily find that [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists) does not contain wheezy but ubuntu release names such as hardy, ... , quantal and raring.
And I think you should not mix debian repository and ubuntu repository. Some guys dared to mix them, and some of them got terrible troubles.
I think that you should use Ubuntu instead of crunchbang, which is based on debian and using wheezy repository, as is written at [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
> **Step 1 - Boot on a liveCD or liveUSB**

 Boot your computer either on: 
- a Ubuntu live-CD or live-USB, then choose "Try Ubuntu", then go to **Step 2 below**. 
- or a [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") liveCD or liveUSB (which will lead you automatically to **Step 3 below**) 
- or a [Boot-Repair-Disk]("https://sourceforge.net/projects/boot-repair-cd/files/") (this is the most convenient as it will lead you automatically to **Step 4 below**) 
Remark: if your boot is not broken, you can also boot into your installed Ubuntu, then go to **Step 2 below**. 

---

### Post by Jizztasto on 2013-01-04
> **kiyop said:**
> You can easily find that [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists) does not contain wheezy but ubuntu release names such as hardy, ... , quantal and raring.
And I think you should not mix debian repository and ubuntu repository. Some guys dared to mix them, and some of them got terrible troubles.
I think that you should use Ubuntu instead of crunchbang, which is based on debian and using wheezy repository, as is written at [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I tried writing the image to the USB, it doesn't seem to be bootable though.
```

dd if=downloads/boot-repair-disk.iso of=/dev/sdh oflag=direct

694616+0 records in
694616+0 records out
355643392 bytes (356 MB) copied, 1435.69 s, 248 kB/s

```

Any help would be appreciated.

---

### Post by kiyop on 2013-01-04
Did you download [http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download) ?
Are you sure that /dev/sdh is an USB media which you want to change to Boot-repair-disk?
Are you sure that your PC can boot from USB?

---

### Post by Jizztasto on 2013-01-04
> **kiyop said:**
> Did you download [http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download) ?
Are you sure that /dev/sdh is an USB media which you want to change to Boot-repair-disk?
Are you sure that your PC can boot from USB?

Yes to all three.
[img]http://i.imgur.com/PXzAP.png[/img]

I installed CrunchBang via the same USB, so I know it can boot from USB.

---

### Post by kiyop on 2013-01-04
I guess that the current boot-repair-disk.iso has a problem on boot loader (kernel loader). 

I found
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
> IMPORTANT: Boot-Repair-Disk is NOT ok for recent computers, LVM, RAID, EFI. You may want to use the alternative repair disk below: RECOMMENDED REPAIR DISK FOR RECENT COMPUTERS / LVM / RAID /EFI : [https://sourceforge.net/p/ubuntu-secured](https://sourceforge.net/p/ubuntu-secured) (750MB, multi-languages, ok for Wifi, LVM and RAID, 32 or 64bit, based on Ubuntu 12.10, Boot-Repair shortcut in the desktop, the 64bit version is UEFI-compatible)How about using Ubuntu-secure-remix [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
[https://sourceforge.net/p/ubuntu-secured](https://sourceforge.net/p/ubuntu-secured)

Below is why I guess that the current boot-repair-disk.iso has a problem on boot loader (kernel loader). 

I downloaded boot-repair-disk.iso at [http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download)[]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download") and confirmed its sha1sum value is correct.
(Did you check the sha1sum value of the downloaded iso file; 
aaa9462d4f61ce5bcc8078da2830fb59f1ec03a8 ?)
The iso file successfullly boots with guest OS played on virtualbox-ose.

I dd'ed the iso file with
```
dd if=./boot-repair-disk.iso of=/dev/sdc oflag=direct
sync
```with root privilege at debian squeeze. Of course, /dev/sdc is an USB flash.
I tried to boot with the dd'ed USB flash but it did not boot.

I tried without "oflag=direct" option in dd'ing, but it did not boot.
I wonder if the latest boot-repair-disk.iso is not bootable, when it is written to an USB flash.
I could boot the very USB flash by using my-tool (kiyoshi's help) [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html) successfully.

---

### Post by Jizztasto on 2013-01-04
> **kiyop said:**
> I guess that the current boot-repair-disk.iso has a problem on boot loader (kernel loader). 

I found
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
How about using Ubuntu-secure-remix [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
[https://sourceforge.net/p/ubuntu-secured](https://sourceforge.net/p/ubuntu-secured)

Below is why I guess that the current boot-repair-disk.iso has a problem on boot loader (kernel loader). 

I downloaded boot-repair-disk.iso at [http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download)[]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download") and confirmed its sha1sum value is correct.
(Did you check the sha1sum value of the downloaded iso file; 
aaa9462d4f61ce5bcc8078da2830fb59f1ec03a8 ?)
The iso file successfullly boots with guest OS played on virtualbox-ose.

I dd'ed the iso file with
```
dd if=./boot-repair-disk.iso of=/dev/sdc oflag=direct
sync
```with root privilege at debian squeeze. Of course, /dev/sdc is an USB flash.
I tried to boot with the dd'ed USB flash but it did not boot.

I tried without "oflag=direct" option in dd'ing, but it did not boot.
I wonder if the latest boot-repair-disk.iso is not bootable, when it is written to an USB flash.
I could boot the very USB flash by using my-tool (kiyoshi's help) [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html) successfully.

Thank you for the help so far.
Strangely, I still can't boot into the USB after installing Ubuntu Secure. All the files appear to be there.
[img]http://i.imgur.com/Q5Q2N.png[/img]

You were able to boot Boot-Repair via USB after using my-tool? If so, I'll take a look at it when I can, it's getting late here so I have to head off soon.

---

### Post by kiyop on 2013-01-04
> **Jizztasto said:**
> You were able to boot Boot-Repair via USB after using my-tool?
Yes, the written USB flash booted successfully if I use my tool: kiyoshi's help [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html).

> **Jizztasto said:**
> If so, I'll take a look at it when I can
You must make my tool by yourself to include suitable modules into my tool.
To make my tool, you must boot some debian first.
I could make my tool on crunchbang, and the made kiyoshi's help could find the boot repair USB flash as /dev/sdc. I selected /dev/sdc, and selected "Search Grub, ...". isolinux settings file was found and I selected "select menuentry" and selected "/mnt/isolinux/live.cfg:label_live" and pressed enter key again and again. Then, Boot repair booted in GUI mode successfully.

If you can tell me the necessary modules, I may be able to make my tool for your case and upload it somewhere to give you, .... BUT...
I may be bashed if I do such a thing.

...

How about using boot info script to know the cause of the problem (instead of boot-repair)?
You can download boot info script at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please post the contents of the generated RESULTS.txt between "[ code]" and "[ /code]". Omit the space just after the "[".

...

Are you sure that your PC is 64bit?

---

### Post by #1udancqSHv% on 2013-01-04
> **kiyop said:**
> How about using Ubuntu-secure-remix [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
[https://sourceforge.net/p/ubuntu-secured](https://sourceforge.net/p/ubuntu-secured)

Unless you're using something that doesn't have a CD/DVD drive, I'd highly recommend writing yourself an Ubuntu Secure Remix bootable DVD - it's saved me a number of times and has more than justified the use of a black DVD. It should sort this issue out for you too...

---

### Post by Jizztasto on 2013-01-08
> **kiyop said:**
> Yes, the written USB flash booted successfully if I use my tool: kiyoshi's help [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html).


You must make my tool by yourself to include suitable modules into my tool.
To make my tool, you must boot some debian first.
I could make my tool on crunchbang, and the made kiyoshi's help could find the boot repair USB flash as /dev/sdc. I selected /dev/sdc, and selected "Search Grub, ...". isolinux settings file was found and I selected "select menuentry" and selected "/mnt/isolinux/live.cfg:label_live" and pressed enter key again and again. Then, Boot repair booted in GUI mode successfully.

If you can tell me the necessary modules, I may be able to make my tool for your case and upload it somewhere to give you, .... BUT...
I may be bashed if I do such a thing.

...

How about using boot info script to know the cause of the problem (instead of boot-repair)?
You can download boot info script at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please post the contents of the generated RESULTS.txt between "[ code]" and "[ /code]". Omit the space just after the "[".

...

Are you sure that your PC is 64bit?


My apologies for the delay.

RESULTS.txt
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda5 already mounted or sda5 busy

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         81,920    32,940,031    32,858,112   7 NTFS / exFAT / HPFS
/dev/sda3          32,940,032 2,004,158,463 1,971,218,432   7 NTFS / exFAT / HPFS
/dev/sda4       2,004,160,510 3,907,028,991 1,902,868,482   5 Extended
/dev/sda5       2,004,160,512 3,873,626,111 1,869,465,600  83 Linux
/dev/sda6       3,873,628,160 3,907,028,991    33,400,832  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        9422144322142CAC                       ntfs       RECOVERY
/dev/sda3        EC88174D881715A4                       ntfs       OS
/dev/sda5        b651edf2-e5ad-488a-9e74-721a25a07c4b   ext4       
/dev/sda6        b0710767-b65d-4674-9139-e8be8a0e2482   swap       
/dev/sdb                                                isw_raid_member 
/dev/sdc                                                iso9660    Boot-Repair-Disk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/disk/by-uuid/b651edf2-e5ad-488a-9e74-721a25a07c4b /                        ext4       (rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered)
/dev/sdc         /media/Boot-Repair-Disk  iso9660    (ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

Yes, I am positive my PC is 64-bit. :)

---

### Post by kiyop on 2013-01-09
Thanks for your posting the contents of the generated RESULTS.txt. :smile:

According to the contents you posted,
/dev/sda has MS-DOS partition table.
/dev/sda2 has /bootmgr.
/dev/sda3 seems to be a windows system partition.
The label of /dev/sda2 is "RECOVERY".
The label of /dev/sda3 is "OS".
But I cannot understand why there is no information on /boot/grub/grub.cfg or /boot/grub/menu.lst. Maybe due to fault on mounting /dev/sda5, but I do not know why.
Did you remove many lines from the contents of the generated RESULTS.txt ?
I want to know the contents of /boot/grub/grub.cfg in /dev/sda5.

If I were you, I would boot crunchbang and download [grub4dos]("http://sourceforge.net/projects/grub4dos/") and unzip the downloaded file, and move the grub.exe in the unzipped directory into / (root) directory of the booting crunchbang, and reboot, and at the grub2 menu, press c key to enter into command line and execute 
```
set root=(hd0,msdos5)
linux /grub.exe
boot
```and then at grub4dos-0.4.4 screen,
```
find --set-root /bootmgr
```or
```
root (hd0,1)
```and then
```
chainloader /bootmgr
boot
```But I am afraid because the label of /dev/sda2 is "RECOVERY".
I hope chainloading to /bootmgr on /dev/sda2 does not start recovery of windows.

Furthermore, I do not know if grub4dos-0.4.4 can run on 64bit CPU.

[Burg4dos]("http://en.sourceforge.jp/projects/sfnet_burg4dos/") may be better, although I have never used it.

---

### Post by oldfred on 2013-01-09
Boot flag is on sda2, but it only has bootmgr. Windows also has to have /boot/BCD.

You probably need to run Windows repairs from a Windows repairCD. But if you run the auto repair 3 times, you then will have to reinstall grub as Windows will install its boot loader. That may not be a bad idea as then you can prove Windows directly boots before using grub to chain load to Windows.

---

### Post by Jizztasto on 2013-01-09
> **kiyop said:**
> Thanks for your posting the contents of the generated RESULTS.txt. :smile:

According to the contents you posted,
/dev/sda has MS-DOS partition table.
/dev/sda2 has /bootmgr.
/dev/sda3 seems to be a windows system partition.
The label of /dev/sda2 is "RECOVERY".
The label of /dev/sda3 is "OS".
But I cannot understand why there is no information on /boot/grub/grub.cfg or /boot/grub/menu.lst. Maybe due to fault on mounting /dev/sda5, but I do not know why.
Did you remove many lines from the contents of the generated RESULTS.txt ?
I want to know the contents of /boot/grub/grub.cfg in /dev/sda5.

If I were you, I would boot crunchbang and download [grub4dos]("http://sourceforge.net/projects/grub4dos/") and unzip the downloaded file, and move the grub.exe in the unzipped directory into / (root) directory of the booting crunchbang, and reboot, and at the grub2 menu, press c key to enter into command line and execute 
```
set root=(hd0,msdos5)
linux /grub.exe
boot
```and then at grub4dos-0.4.4 screen,
```
find --set-root /bootmgr
```or
```
root (hd0,1)
```and then
```
chainloader /bootmgr
boot
```But I am afraid because the label of /dev/sda2 is "RECOVERY".
I hope chainloading to /bootmgr on /dev/sda2 does not start recovery of windows.

Furthermore, I do not know if grub4dos-0.4.4 can run on 64bit CPU.

[Burg4dos]("http://en.sourceforge.jp/projects/sfnet_burg4dos/") may be better, although I have never used it.

Thank you for the informative reply! :)

No, no, I didn't remove any lines from the RESULTS.txt at all.
I can provide the code for that file if you like?
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
insmod png
if background_image /usr/share/images/desktop-base/grub-splash-crunchbang.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'CrunchBang GNU/Linux, with Linux 3.2.0-4-amd64' --class crunchbang --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
	echo	'Loading Linux 3.2.0-4-amd64 ...'
	linux	/boot/vmlinuz-3.2.0-4-amd64 root=UUID=b651edf2-e5ad-488a-9e74-721a25a07c4b ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-4-amd64
}
menuentry 'CrunchBang GNU/Linux, with Linux 3.2.0-4-amd64 (recovery mode)' --class crunchbang --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
	echo	'Loading Linux 3.2.0-4-amd64 ...'
	linux	/boot/vmlinuz-3.2.0-4-amd64 root=UUID=b651edf2-e5ad-488a-9e74-721a25a07c4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-4-amd64
}
menuentry 'CrunchBang GNU/Linux, with Linux 3.2.0-3-amd64' --class crunchbang --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
	echo	'Loading Linux 3.2.0-3-amd64 ...'
	linux	/boot/vmlinuz-3.2.0-3-amd64 root=UUID=b651edf2-e5ad-488a-9e74-721a25a07c4b ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-3-amd64
}
menuentry 'CrunchBang GNU/Linux, with Linux 3.2.0-3-amd64 (recovery mode)' --class crunchbang --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b651edf2-e5ad-488a-9e74-721a25a07c4b
	echo	'Loading Linux 3.2.0-3-amd64 ...'
	linux	/boot/vmlinuz-3.2.0-3-amd64 root=UUID=b651edf2-e5ad-488a-9e74-721a25a07c4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-3-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

I tried everything you said and received the following error when booting:
[http://i.imgur.com/crHAo.jpg](http://i.imgur.com/crHAo.jpg)

Thanks a lot for the help so far! :p


> **oldfred said:**
> Boot flag is on sda2, but it only has bootmgr. Windows also has to have /boot/BCD.

You probably need to run Windows repairs from a Windows repairCD. But if you run the auto repair 3 times, you then will have to reinstall grub as Windows will install its boot loader. That may not be a bad idea as then you can prove Windows directly boots before using grub to chain load to Windows.

I tried the Windows disk, it doesn't even detect that Windows is installed on the drive.

---

### Post by kazuya on 2013-01-09
I am asuming that you have one of those new laptops with secure boot and windows 8?
(1) First step is to ensure that you go to your BIOs and make sure that you enabled Windows Boot Manager under Boot Order Priority. 
You may have to tap ESC, F2, F10, F9 repeatedley upon boot depening on what laptop.
(2) If Windows Boot manager is disabled in Boot Order TAB , be sure to enable it > Then SAVE changes
(3) Reboot Machine and Hit the ESC or whatever Key gets to Boot Order Selection (Not BIOS)
(4) Select the Windows Boot Manager boot option and hit ENTER
 
Windows 8 install should hopefully start.
Good luck.

---

### Post by Jizztasto on 2013-01-12
Does anyone have any suggestions as of my last post?

---

### Post by oldfred on 2013-01-13
Windows needs both Bootmgr & /boot/BCD in a NTFS partition with the boot flag to start to boot. BCD has to then have info on where your install(s) are.

If Windows 7 repairCD does not want to fix sda2, try moving boot flag to sda3 and rerun repairs. I have seen one user literally just copy the bootmgr from his repairCD to his install, copy and then manually edit BCD (to be the install not the repair) and got his system working. But generally better to run Windows repairs. It also may need chkdsk on either or both sda2 or sda3.

---

### Post by kiyop on 2013-01-14
Thanks oldfred for the following post:
> **oldfred said:**
> Windows needs both Bootmgr & /boot/BCD in a NTFS partition with the boot flag to start to boot. BCD has to then have info on where your install(s) are.

---

### Post by Jizztasto on 2013-01-17
> **oldfred said:**
> Windows needs both Bootmgr & /boot/BCD in a NTFS partition with the boot flag to start to boot. BCD has to then have info on where your install(s) are.

If Windows 7 repairCD does not want to fix sda2, try moving boot flag to sda3 and rerun repairs. I have seen one user literally just copy the bootmgr from his repairCD to his install, copy and then manually edit BCD (to be the install not the repair) and got his system working. But generally better to run Windows repairs. It also may need chkdsk on either or both sda2 or sda3.

Thanks for the reply.
I set the boot flag using fdisk, am I actually meant to somehow "move" it or is that what you mean?
Output of **fdisk -l**:
```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9083934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131    6  FAT16
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    32940031    16429056    7  HPFS/NTFS/exFAT
/dev/sda3   *    32940032  2004158463   985609216    7  HPFS/NTFS/exFAT
/dev/sda4      2004160510  3907028991   951434241    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      2004160512  3873626111   934732800   83  Linux
/dev/sda6      3873628160  3907028991    16700416   82  Linux swap / Solaris

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba000000

Disk /dev/sdb doesn't contain a valid partition table

```

I didn't remove the flag from sda2 because it has bootmgr, not sure if I was suppose to remove that or not.
Alas, Windows repair disk still couldn't locate the Windows installation.

---

### Post by kiyop on 2013-01-17
I think that two or more partitions in a HDD should not have boot flags.
It may cause a confusion.
So I suggest you removing the boot flag from /dev/sda2.

I hope the following helps you.
[http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm](http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm)

---

### Post by oldfred on 2013-01-17
+1 on kiyop's suggestion on only one boot flag. 
You can use gparted, Disk Utility or command line to set boot flag. In Windows it is setting the active partition.
       set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
parted /dev/sdb set 2 boot on

    
Was SSD one of the Intel SRT systems. We often see issues with the RAID as SRT uses RAID somehow as the cache for Windows on the SSD.
> /dev/sdb                      isw_raid_member 

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

