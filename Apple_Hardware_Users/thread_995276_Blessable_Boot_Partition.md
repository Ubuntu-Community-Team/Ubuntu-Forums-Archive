---
title: "Blessable Boot Partition"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by user12021 on 2008-11-27
Hello.
I currently have all my Linux files on one ext3 partition.
I would like to move all of my boot files to a separate partition (with a filesystem that I can mount (r/w) in Mac OS X)
It would have to be HFS, HFS+ (preferable), MSDOS (FAT12, 16 or 32), or UFS.
That way I can, mount it in OSX, run the bless command, add my own volume icon and labelfile, and use my firmware's built in boot menu instead of that awful rEFIt.
If that's impossible, I can move the boot files to an ext2 volume, which the firmware can boot from, but I can't bless them if I do that.
I was able to do something like this when I was using Fedora. Is there a way I can do this in Ubuntu?

---

### Post by pxwpxw on 2008-11-27
> **user12021 said:**
> Hello.
I currently have all my Linux files on one ext3 partition.
I would like to move all of my boot files to a separate partition (with a filesystem that I can mount (r/w) in Mac OS X)
It would have to be HFS, HFS+ (preferable), MSDOS (FAT12, 16 or 32), or UFS.
That way I can, mount it in OSX, run the bless command, add my own volume icon and labelfile, and use my firmware's built in boot menu instead of that awful rEFIt.
If that's impossible, I can move the boot files to an ext2 volume, which the firmware can boot from, but I can't bless them if I do that.
I was able to do something like this when I was using Fedora. Is there a way I can do this in Ubuntu?

By boot files, do you mean the boot loader or the whole /boot directory (vmlinuz intird.img ...)?  Why would you need to use a separate /boot?

You can put an efi bootloader (which I am using) in Macosx or any hfsplus partition and use macosx to bless it and maintain it.  

Refit can show custom icons. 

On the Apple boot screen (without refit) I can show small graphical labels using bless --labelfile, have not so far managed to change the big Apple icons.

The grub.efi bootloader works well, the current development requires disabling accelerated graphics (agpgart *_agp ). 

Refit is a very useful tool, keep it, even if you dont boot with it.

---

### Post by user12021 on 2008-11-27
> By boot files, do you mean the boot loader or the whole /boot directory (vmlinuz intird.img ...)?  Why would you need to use a separate /boot?
That's what i had when using Fedora, but I don't really need it. It can just be the bootloader.

> You can put an efi bootloader (which I am using) in Macosx or any hfsplus partition and use macosx to bless it and maintain it.  
That's what i'm trying to do.

> On the Apple boot screen (without refit) I can show small graphical labels using bless --labelfile, have not so far managed to change the big Apple icons.
you can also use bless --label name
i believe creating a file called .volumeicon.icns in the root level of the partition will do this.

> The grub.efi bootloader works well, the current development requires disabling accelerated graphics (agpgart *_agp ). 
it's compiling as i type
Is that all I need to use?

---

### Post by pxwpxw on 2008-11-27
What version have you got? (svn1913 here)

edit /.volumeicons.icns
works

---

### Post by user12021 on 2008-11-27
I got it from subversion today, so it's probably the newest.

I can't get it to work. If I try to choose grub from apple's boot menu, it just goes straight to rEFIt.
If I try to choose grub from rEFIt, it says "unsupported while loading grub.efi"
What am I doing wrong?

Also, what should my grub.cfg file look like?
my disk is formatted like this:
OSX on 2nd partition
Grub on 3rd
Linux on 4th

---

### Post by pxwpxw on 2008-11-28
> **user12021 said:**
> I got it from subversion today, so it's probably the newest.

I can't get it to work. If I try to choose grub from apple's boot menu, it just goes straight to rEFIt.
If I try to choose grub from rEFIt, it says "unsupported while loading grub.efi"
What am I doing wrong?

Also, what should my grub.cfg file look like?
my disk is formatted like this:
OSX on 2nd partition
Grub on 3rd
Linux on 4th
Probably missing some modules, but you got a start.
grub.efi should be around 250KB with the preloaded modules.

I am just putting together a grub efi tarball here with working grub.efi grub.cfg and modules, should help you, should be about an hour. Would be glad to get your reactions.

For that I will open a new thread with a more grubby title.

Here is some of it -
----------------------
These are the preloaded modules in my grub.efi -

apple appleldr boot cat chain configfile cpio date ext2 echo fat gpt help hexdump hfs hfsplus iso9660 linux ls normal pc reboot reiserfs scsi search sleep xfs

These are all the modules in the grub directory alongside grub.efi
```

pxw@wdc:~/src/grub2/build$ ls *.mod
acorn.mod        _chain.mod      echo.mod     help.mod      ls.mod        raid6rec.mod  terminfo.mod
affs.mod         chain.mod       elf.mod      hexdump.mod   lspci.mod     raid.mod      test.mod
afs.mod          cmp.mod         ext2.mod     hfs.mod       lvm.mod       read.mod      udf.mod
amiga.mod        configfile.mod  fat.mod      hfsplus.mod   mdraid.mod    reboot.mod    ufs.mod
appleldr.mod     cpio.mod        font.mod     iso9660.mod   minix.mod     reiserfs.mod  vga_text.mod
apple.mod        cpuid.mod       fshelp.mod   jfs.mod       normal.mod    scsi.mod      xfs.mod
at_keyboard.mod  crc.mod         fs_uuid.mod  kernel.mod    ntfscomp.mod  search.mod
blocklist.mod    datehook.mod    gpt.mod      _linux.mod    ntfs.mod      sfs.mod
boot.mod         date.mod        gzio.mod     linux.mod     pci.mod       sleep.mod
bufio.mod        datetime.mod    halt.mod     loadenv.mod   pc.mod        sun.mod
cat.mod          dm_nv.mod       hello.mod    loopback.mod  raid5rec.mod  terminal.mod

```
--------------------
grub.cfg
```

## grub svn v1913 configure --with-platform=efi
## 20081128 pxw
## example
## comments apply to MacBook2,1 with 1 internal HD and CD, used with various external drives.
## linux root=/dev/sdxx and grub loads kernel from root=(hdx,x). Will need check/edit. 
##
timeout=20 
## first menuentry is 0 
default=0
fallback=1
## for booting from 'e' edited menuentry control x does not work.
set F1=ctrl-x
set F2=ctrl-c
#
# boot the first macosx found
menuentry "search MacOSX" {
	search --set /usr/standalone/i386/boot.efi
	chainloader /usr/standalone/i386/boot.efi
}
#
# search for vmlinuz starts from (hd0,1)
# with only one drive (no cd or usb) it will be grub (hd0) and linux /dev/sda
# boot first /vmlinuz found and use linux root=/dev/sda4 
menuentry "search-vmlinuz root=sda4" {
	search --set  /vmlinuz
 linux  /vmlinuz root=/dev/sda4  agp=off video=efifb
 initrd  /initrd.img
}
#
# with a usb drive present usb is (hd0) but /dev/sdb, internl hd is (hd1) but sda
# usb will be found first
menuentry "search-vmlinuz root=sdb3" {
	search --set  /vmlinuz
 linux  /vmlinuz root=/dev/sdb3  agp=off video=efifb
 initrd  /initrd.img
}
#
# boot ubuntu on HD (hd1) at /dev/sda4.
# 
# boot (hd1,4)/vmlinuz and use root=/dev/sda4 
menuentry "set hd1,4 vmlinuz" {
  root=(hd1,4)
  linux /vmlinuz root=/dev/sda4 ro video=efifb
  initrd /initrd.img
}
# appleloader boots from internals only - cd or hd. 
menuentry "Boot from ISO CD" {
   appleloader CD
}
menuentry "Boot from HD MBR" {
   appleloader HD
}
## optional extras
menuentry "Partition List" {
	ls -l
	sleep 5
}
menuentry "Where am I" {
set
ls
date
echo "sda2?? edit this"
sleep 10
}
menuentry "REBOOT" {
	reboot
}
menuentry "set pager=1" {
	set pager=1
}
##

```

---

### Post by pxwpxw on 2008-11-28
More on new thread
grub2 EFI boot loader internal/external booting

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by user12021 on 2008-11-28
It almost works:
when I choose Linux in GRUB, It prints a bunch of text for about 3 seconds, then every five seconds it prints this:
```
ata5.00: status: { DRDY }
ata5: soft resetting link
ata5.00: configured for PIO0
ata5: EH complete
ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata5.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
         cdb 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00
         res 40/00:00:00:00:00/00:00:00:00:00/ Emask 0x4 (timeout)
```

At 30 seconds, it says this, then continues to print the first one over and over
```
Done.
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - check root= (did the system wait for the right device?)
- Missig modules (cat /proc/modules;ls /dev)
ALERT! /dev/sda4 does not exist. Dropping to a shell!
```

I know it must be a problem with my grub.cfg file.
I used the one that you uploaded, but I know that probably won't work.
What should I change to get it to work on my system?

---

### Post by pxwpxw on 2008-11-28
We can fix those. You have got grub loading the kernel vmlinuz and initrd.img, so it has done its job, there are just a few more things to do.

1. The ata5 timeout (probably the cd drive) just needs adding a kernel arg in the grub.cfg linux line, I have had to use it, but I will have to go find what it is.
It may depend on the Mac model - what is it?.

2. < ALERT /dev/sda4 does not exist>

just needs you to change the linux root device partition number from 4 
  in   **linux    /vmlinuz root=/dev/sda4**

In my grub.cfg you have -
```

menuentry "search-vmlinuz root=sda4" {
	search --set  /vmlinuz
 linux  /vmlinuz **root=/dev/sda4 ** agp=off video=efifb
 initrd  /initrd.img
}

```

It might be /dev/sda3, if you just have Macosx and Linux.
(There is an empty 200MB EFI partition at /dev/sda1).

To find the partition number, use the grub menuentry Partition List or the grub commandline 'c'
```

grub> ls -l
grub> search /vmlinuz

```

You can  use the grub menu editor 'e' and edit the menuentry, F1 will boot from there, then fix it from macosx editor.

3. After fixing that, the next stop will be at the end of the startup messages, when the agpgart and any  *_agp modules are loaded, the screen goes to black, just beforee it gets to a text console.

These need to be blacklisted by editing /etc/modprobe.d/blacklist or by adding another blacklist file. I will post this in the other thread, I forgot it there also. 

 Since you can't write to the ubuntu ext3 file system from macosx,
it will be easiest to use your ubuntu install cd if it is a live cd.
At the same time, if you have installed a desktop, you can edit /etc/X11/xorg.conf to use Driver "fbdev", or you can do that from a root console.

I will add info on that also, its a small one.

Edit:
agp blacklist and desktop xorg.conf for fbdev now on grub efi thread
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by user12021 on 2008-11-29
the model of my mac is macbook 2,1 (aka santa rosa)

i tried many combinations of /dev/sda# but none of them worked
the comm and "search /vmlinuz" says vmlinuz is on hd0,4
setting root to hd0,4 does not work
setting root to the partition's uuid did not work
copying /dev from my linux partition to my grub partition did not work

i haven't done the blacklist thing yet, or the xorg.conf thing yet

while in grub's terminal, i tried search /dev/, search /dev/sda4, and other things, but it never found any devices

what else can i do?

---

### Post by pxwpxw on 2008-11-29
Can we just get some information together here, you are just trying to do some things the wrong way.

Firstly, have you had the ubuntu installation running at all?

Also -
Search will only find files, not directories.
If you want to see what is in a directory
```

grub> ls /

```

Correct me if I have this wrong -

grub> search /vmlinuz
found /vmlinuz on (hd0,4)
 
(hd0,4) is grub talk
 - it is the same partition that linux calls /dev/sda4.
grub is finding /vmlinuz using search and loading vmlinuz from there.
So that looks ok.

Now if you have your ubuntu root installation on /dev/sda4 with /vmiinuz,  the grub.cfg with linux root=/dev/sda4 shoudl be working. and my grub.cfg should work for you. 

But you may have a different configuration (2 separate partitions for linux) 

So you need to recheck the partitions first.

Please go into Macosx.

In a terminal run these commands

```

sudo diskutil list
sudo gpt -r show /dev/disk0

```
If you have the rEFIt Partitiion Inspector, run that.

Then post the results.

Also have you installed Intrepid and do you have the Desktop CD or the Alternate install?

---

### Post by user12021 on 2008-11-29
> Firstly, have you had the ubuntu installation running at all?
Yes, I'm using it right now. I still have the old bootloaders on here, but they're on an ext3 partition that can't be accessed from OSX.

> Search will only find files, not directories.
I thought /dev/sda4 would count as a file

I got some interesting results when using the ls command in grub
```
grub>root=(hd0,4)
grub>ls /dev
```
this printed ~40-50 things, but nothing like sda# or hda#, or really anything that looks like it could be a partition
While booted into linux, ls -A /dev returns no less than 720 results.

I am using Intrepid, with the alternate installer, but I still have several fedora live CD's and a live CD of Gutsy Gibbon. I also have a Gparted live cd.

EDIT: I booted into OSX and  ran the commands
```
sudo diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *186.3 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS HD                      169.9 Gi   disk0s2
   3:                  Apple_HFS HD_2                    896.0 Mi   disk0s3
   4:       Microsoft Basic Data                         13.4 Gi    disk0s4
   5:                 Linux Swap                         1.8 Gi     disk0s5

sudo gpt -r show /dev/disk0
gpt show: /dev/disk0: Suspicious MBR at sector 0
      start       size  index  contents
          0          1         MBR
          1          1         Pri GPT header
          2         32         Pri GPT table
         34          6         
         40     409600      1  GPT part - C12A7328-F81F-11D2-BA4B-00A0C93EC93B
     409640  356253696      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  356663336     262144         
  356925480    1835008      3  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  358760488   28125001      4  GPT part - EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
  386885489    3836446      5  GPT part - 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F
  390721935         32         Sec GPT table
  390721967          1         Sec GPT header

rEFIt partition inspector.
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    356663335  Mac OS X HFS+
 3      356925480    358760487  Mac OS X HFS+
 4      358760488    386885488  Basic Data
 5      386885489    390721934  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    356663335  af  Mac OS X HFS+
 3      356925480    358760487  af  Mac OS X HFS+
 4 *    358760488    386885488  83  Linux

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

Partition at LBA 356925480:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 358760488:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 386885489:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```

I updated the MBR in rEFIt, and now rEFIt will no longer boot ubuntu.

---

### Post by pxwpxw on 2008-11-29
The partitioning looks good, 
If that is ubuntu linux root partition at 4, thats /dev/sda4
grubefi sees it as (hd0,4)

your grub-pc uses the MBR, but grub.efi does not, so can you still run grub.efi?

If you can, please get to the grub.efi command line using 'c'
then just 
```

grub> ls -l

```
This should show you a list of all the partitions.
Just do that, you are getting confused by using difficult commands for grub.efi
It is not like grup-pc the old versiion, do not confuse the 2.

Then please post the grub.cfg menu you are using.

---

### Post by user12021 on 2008-11-29
i can still run grub.efi, but I'm still having the same problem as before

ls -l returns this
```
Device hd0: Partition table
       Partition hd0,1: Filesystem type fat, UUID 3c1a-1iaf6
       Partition hd0,2: Filesystem type hfsplus
       Partition hd0,3: Filesystem type hfsplus
       Partition hd0,4: Filesystem type ext2, UUID 472edca7-2a7b-4219-b1dc-d1424e4a0d38
       Partition hd0,5: Unknown Filesystem
Device cd0: unknown filesystem
```

and here's my grub.cfg file:
```
## grub svn v1913 configure --with-platform=efi
## 20081128 pxw
## example
## comments apply to MacBook2,1 with 1 internal HD and CD, used with various external drives.
## linux root=/dev/sdxx and grub loads kernel from root=(hdx,x). Will need check/edit. 
##
timeout=20 
## first menuentry is 0 
default=0
fallback=1
## for booting from 'e' edited menuentry control x does not work.
set F1=ctrl-x
set F2=ctrl-c
#
# boot the first macosx found (works)
menuentry "search MacOSX" {
	search --set /usr/standalone/i386/boot.efi
	chainloader /usr/standalone/i386/boot.efi
}
#
# returns error
# /dev/disk/by-uuid/472edca7-2a7b-4219-b1dc-d1424e4a0d38 does not exist
menuentry "uuid" {
 set root=(hd0,4)
 linux  /vmlinuz root=UUID=472edca7-2a7b-4219-b1dc-d1424e4a0d38  agp=off video=efifb
 initrd  /initrd.img
}
# search for vmlinuz starts from (hd0,1)
# with only one drive (no cd or usb) it will be grub (hd0) and linux /dev/sda
# boot first /vmlinuz found and use linux root=/dev/sda4 
menuentry "search-vmlinuz root=sda4" {
	search --set  /vmlinuz
 linux  /vmlinuz root=/dev/sda4  agp=off video=efifb
 initrd  /initrd.img
}
#
# returns error
# /dev/sda4 does not exist
menuentry "setroothd04" {
	set root=(hd0,4)
 linux  /vmlinuz root=/dev/sda4  agp=off video=efifb
 initrd  /initrd.img
}
# with a usb drive present usb is (hd0) but /dev/sdb, internl hd is (hd1) but sda
# usb will be found first
menuentry "search-vmlinuz root=sdb3" {
	search --set  /vmlinuz
 linux  /vmlinuz root=/dev/sdb3  agp=off video=efifb
 initrd  /initrd.img
}
#
# boot ubuntu on HD (hd1) at /dev/sda4.
# 
# boot (hd1,4)/vmlinuz and use root=/dev/sda4 
menuentry "set hd1,4 vmlinuz" {
  root=(hd1,4)
  linux /vmlinuz root=/dev/sda4 ro video=efifb
  initrd /initrd.img
}
# appleloader boots from internals only - cd or hd. 
menuentry "Boot from ISO CD" {
   appleloader CD
}
menuentry "Boot from HD MBR" {
   appleloader HD
}
## optional extras
menuentry "Partition List" {
	ls -l
	sleep 5
}
menuentry "Where am I" {
set
ls
date
echo "sda2?? edit this"
sleep 5
}
menuentry "REBOOT" {
	reboot
}
menuentry "set pager=1" {
	set pager=1
}
##
```

---

### Post by pxwpxw on 2008-11-29
Just reading that, there are a few bugs in the grub.cfg, while I am looking at that, could you confirm that you have all the modules *.mod, about 70 of them, in beside grub.efi.

---

### Post by user12021 on 2008-11-29
I have 72 modules.

---

### Post by pxwpxw on 2008-11-29
Ok 72 sounds right.

The grub.cfg has got some bugs in it now, need to make a clean entry to try, there may be a problem with the search --set entry. and I dont lknow if uuid option is available.

but also 

You dont use set root=  in the menuentry
 just root=

This should work -
```

menuentry " hd0,4 vmlinuz sda4" {
  root=(hd0,4)
  linux /vmlinuz root=/dev/sda4  video=efifb agp=off
  initrd /initrd.img
}

```

I will stand by here for your result.

---

### Post by user12021 on 2008-11-29
unfortunately, that returns the same error.

---

### Post by pxwpxw on 2008-11-29
I assume you mean the ALERT....

One other possibility - it is not so far confirmed that the root is in fact /dev/sda4 as seen in linux.

You can check that from after the ALERT
```

(initramfs) cat /proc/partitions
(initramfs) ls /dev/sd*

```
just   exit or reboot from there.

Its all I can think of just now, given that all was booting  from the old grub.

If that fails, it is just possible there is some bug in that svn release, you might try my package which is proved OK at least on a MacBook2.1.
It also has some notes in grub/doc might be of use.

I will wait to see what you say (its just about daybreak here).

---

### Post by pxwpxw on 2008-11-29
X

---

### Post by user12021 on 2008-11-29
when do i type this?
```
(initramfs) cat /proc/partitions
(initramfs) ls /dev/sd*
```

in the first 3 seconds, when there's a bunch of text, i spotted a few errors.
i had to write these quickly, so they might not be word for word.
```
can't find irq for pci int a: please try using pci=biosirq
found hc with no irq
init (something) failed -19
ohci1394 failed to allocate interupt 0
Probe of (something) Failed with error -12
Driver sd needs updating. Please use bus_type methods
```

i've been using the package you uploaded. I re-downloaded it just in case, but it still didn't work

---

### Post by pxwpxw on 2008-11-29
Were you able to check the partition names?

Ah sorry, do that after you get the alert, hit a key, it should
go to 
(initramfs)

Those errors might be a clue but probably not fatal, IDK.

It all looks correct as far as loading the kernel, there is something stopping the root partition from being mounted by linux, and I cant see how the booloader can cause that, it is loading the kernel from the same partition, but grub is using its own modules to do that.
And the linux side seems to be ok when old grub1 is the bootloader.

I will have to leave it there for now, will check back after a sleep.

---

### Post by user12021 on 2008-11-29
what key should I use? I think i hit every key on my keyboard, and not one of them made it so I could type.

/proc/partitions does not exist
/proc is completely empty except for . and ..

---

### Post by pxwpxw on 2008-11-29
ok, leave it, it has a problem there. I will get back tomorrow.

---

### Post by pxwpxw on 2008-11-29
Had another  look here, I think try adding the kernel arg 
 pci=biosirq
maybe for the macbook santa rosa.
It does no harm here for macbook2,1

It is established that (hd0,4) and /dev/sda4 are correct.

PM me if that might make it easier.

re-reading - you said it is a MacBook 2,1 but SantaRosa is 3,1-4,1 according to the wiki?
(Mine is a 2,1 with 80GB hd).
[https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa)

---

### Post by pxwpxw on 2008-11-30
On macbook2,1 I can reproduce the bug you described by setting acpi=off in the kernel boot options. It is an acpi issue.

That causes both the < ALERT... cant find /dev/sda4 ... dropping to shell>
AND the continuous looping of the ata5 timeout, with keyboard dead,
so you cant do anything except power off.

So to allow acpi to work, try acpi=force in the meuentry 

```

linux /vmlinuz root=/dev/sda4 video=efifb agp=off acpi=force

```

I can't test that here because I have to use acpi=off to reproduce the bug.
pci=noirq had no effect.

For a list of the boot options and other acpi settings -

BootOptions
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

---

### Post by user12021 on 2008-11-30
I'm sorry, I had been told it was a Santa Rosa. My mistake.
I looked it up, and the T7400 processor is not a Santa Rosa one.

acpi=force made no difference. neither did pci=noirq.
acpi=noirq or pci=acpi did not work either.

---

### Post by cyberdork33 on 2008-11-30
> **user12021 said:**
> I'm sorry, I had been told it was a Santa Rosa. My mistake
Use the information in the "Before you post" link to properly identify your Mac.

---

### Post by pxwpxw on 2008-12-01
> **user12021 said:**
> I'm sorry, I had been told it was a Santa Rosa. My mistake.
I looked it up, and the T7400 processor is not a Santa Rosa one.

acpi=force made no difference. neither did pci=noirq.
acpi=noirq or pci=acpi did not work either.

Try this menuentry
It should get to  (initramfs) but no keyboard.
```

menuentry "search-vmlinuz root=sda4" {
	search --set  /vmlinuz
 linux  /vmlinuz root=/dev/sda4  agp=off video=efifb  break
 initrd  /initrd.img
}

```

I want to get this fixed, here is some info I nead .
 
1. The macbook model:
from macosx -
```

Apple--About this mac--More Info:

Hardware Overview:

  Machine Name:	Mac
  Machine Model:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.13f3
  Serial Number:	W8717FYXWGL
  Sudden Motion Sensor:
  State:	Enabled

```

2. About the ubuntu installation on sda4.

How was this installed, and what kernel versions are on it, and can you still boot it with grub1 - we should  fix that first. 

You can list the boot files fronm the efi grub command line 
```

search --set /vmlinuz
ls -l /boot

```
It must be intrepid 810 kernel version 2.6.27 to work with EFI, and i386 not amd64 for that build of grub.efi. An intrepid server or alternate install CD ia best.

3. It seems that nothing is affecting the result.
When you tried acpi=off and others, booting from the grub editor must be done using the fn and F1 keys (on my macbook), without escaping to the menu, else it will cancel the edit. It is safest to edit a menuentry in macosx. Can we eliminate that suspect.

---

### Post by user12021 on 2008-12-01
Last night, I had been thinking about it, and realized it might be because I'm using the 64-bit version of Linux.

I just recompiled grub because of this, and now I have the exact same problem I did in post 5 of this thread.
I can no longer use grub2 at all, so I can't test that new menuentry.
Is this the correct way to compile/install it?
```
./configure --with-platform=efi --target=x86_64
./grub-mkimage -d . -o grub.efi gpt hfsplus fat ext2 normal chain boot configfile
cp grub.efi *.mod fs.lst command.lst /media/HD_2/efi/grub
```

1.  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.16 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.17f0
  Sudden Motion Sensor:
  State:	Enabled

2.kernel is 2.6.27-9-generic, but 2.6.27-7-generic did not work either
It is Ubuntu 8.10 AMD64 with the alternate text-based install
grub1 still works.

3. I had been using F1, and editing the files in OSX, so that is not a problem

---

### Post by pxwpxw on 2008-12-01
Just quickly, 
the 64 bit may well be the problem, i am i386=32bit, compiled on that.
your macbook seems to be the model following mine, also T7200 here.
Your grub-mkimage looks a bit short of preloaded modules.
In my package grub/doc there should be a log of my build and list of modules.
Youy should look at 
$ dmesg | grep ACPI

Is that from latest svn trunk/grub2?

---

### Post by pxwpxw on 2008-12-01
To run grub.efi from refit, it needs to be in /EFI/ for refit to find it, unless it is in same directory as refit. 
My grub.cfg needs some of the extra modules.
You can load modules from grub commandline using insmod, see help or tab.

---

### Post by user12021 on 2008-12-01
I have the same number of modules as the package you provided.
Let me move grub into /EFI instead of /EFI/grub to see if that makes a difference
Then I'll boot into linux, and run dmesg.
yes, it's the latest revision of trunk/grub2

Moving grub into /EFI instead of /EFI/grub then re-blessing it made it so refit couldn't find grub at all.
It could find it before, it just didn't work.

the results of dmesg | grep ACPI
```
[    0.000000]  BIOS-e820: 000000007e0f8000 - 000000007e2f9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e2f9000 - 000000007eebe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eebe000 - 000000007eeef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eeef000 - 000000007ef00000 (ACPI data)
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 APPLE )
[    0.000000] ACPI: XSDT 7EEFD1C0, 0074 (r1 APPLE   Apple00       A5       1000013)
[    0.000000] ACPI: FACP 7EEFB000, 00F4 (r3 APPLE   Apple00       A5 Loki       5F)
[    0.000000] ACPI: DSDT 7EEF0000, 41E4 (r1 APPLE   MacBook    20001 INTL 20050309)
[    0.000000] ACPI: FACS 7EEC0000, 0040
[    0.000000] ACPI: HPET 7EEFA000, 0038 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: APIC 7EEF9000, 0068 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: MCFG 7EEF8000, 003C (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: ASF! 7EEF7000, 00A0 (r32 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: SBST 7EEF6000, 0030 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: ECDT 7EEF5000, 0053 (r1 APPLE   Apple00        1 Loki       5F)
[    0.000000] ACPI: SSDT 7EEEF000, 04DC (r1 APPLE     CpuPm     3000 INTL 20050309)
[    0.000000] ACPI: SSDT 7EEBD000, 064F (r1 SataRe  SataPri     1000 INTL 20050309)
[    0.000000] ACPI: SSDT 7EEBC000, 069C (r1 SataRe  SataSec     1000 INTL 20050309)
[    0.000000] ACPI: DMI detected: Apple
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.004019] ACPI: Core revision 20080609
[    0.005701] ACPI: Checking initramfs for custom DSDT
[    0.584375] ACPI: bus type pci registered
[    0.588795] ACPI: EC: EC description table is found, configuring boot EC
[    0.588897] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.608187] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.608735] ACPI: Interpreter enabled
[    0.608737] ACPI: (supports S0 S3 S4 S5)
[    0.608753] ACPI: Using IOAPIC for interrupt routing
[    0.624218] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.624218] ACPI: EC: driver started in interrupt mode
[    0.624218] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.625058] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.628759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.629149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.629300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.629466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.636460] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.636460] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.636460] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.636517] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.636638] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.636760] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.636882] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.637004] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[    0.637074] pnp: PnP ACPI init
[    0.637074] ACPI: bus type pnp registered
[    0.644202] pnp: PnP ACPI: found 9 devices
[    0.644205] ACPI: ACPI bus type pnp unregistered
[    0.644229] PCI: Using ACPI for IRQ routing
[    0.670689] ACPI: RTC can wake from S4
[    0.689517] pci 0000:00:1e.0: power state changed by ACPI to D0
[    1.843334] ACPI: SSDT 7EEB8C10, 02AE (r1 APPLE   Cpu0Ist     3000 INTL 20050309)
[    1.843732] ACPI: SSDT 7EEB8910, 02A0 (r1 APPLE   Cpu0Cst     3001 INTL 20050309)
[    1.844357] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.844437] processor ACPI0007:00: registered as cooling_device0
[    1.844441] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.844844] ACPI: SSDT 7EEB8F10, 0087 (r1 APPLE   Cpu1Ist     3000 INTL 20050309)
[    1.845172] ACPI: SSDT 7EEB7F10, 0085 (r1 APPLE   Cpu1Cst     3000 INTL 20050309)
[    1.845774] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.845825] processor ACPI0007:01: registered as cooling_device1
[    1.845829] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.228668] pata_acpi 0000:00:1f.1: power state changed by ACPI to D0
[    3.294389] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[   16.322442] ACPI: Battery Slot [BAT0] (battery present)
[   16.322570] ACPI: AC Adapter [ADP1] (off-line)
[   16.353027] ACPI: Power Button (FF) [PWRF]
[   16.353197] ACPI: Lid Switch [LID0]
[   16.385023] ACPI: Power Button (CM) [PWRB]
[   16.413033] ACPI: Sleep Button (CM) [SLPB]
[   16.473048] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   20.139082] ACPI: WMI: Mapper loaded
```

---

### Post by pxwpxw on 2008-12-01
Yes, it just needs grub.efi in the right place I'm sure.
But you can bless --folder xxxx   --file xxxx/grub.efi and it should show up in the Apple boot screen.

---

### Post by user12021 on 2008-12-01
It shows up in the apple boot menu every time, I never had any problems with that.
It only shows up in rEFIt when grub in in /efi/grub/

---

### Post by pxwpxw on 2008-12-01
If external it should be in /EFI/grub/grub.efi.
I think maybe a problem with target
see
grub2/configure

line 1951
if test "x$with_platform" = x; then
  case "$target_cpu"-"$target_vendor" in
    i386-apple) platform=efi ;;
    i386-*) platform=pc ;;
    x86_64-apple) platform=efi ;;
    x86_64-*) platform=pc ;;
    powerpc-*) platform=ieee1275 ;;
    powerpc64-*) platform=ieee1275 ;;
    sparc64-*) platform=ieee1275 ;;


 may need x86_64-apple
not sure.

---

### Post by user12021 on 2008-12-01
What do I type after [FONT="Courier New"]./configure[/FONT] to get [FONT="Courier New"]x86_64-apple[/FONT]?
Is it [FONT="Courier New"]--target=x86_64-apple[/FONT]?
I don't really know much about compiling besides configure and make.

---

### Post by pxwpxw on 2008-12-01
first you need to clean out the previous stuff
```

make distclean

./configure --with-platform=efi --target=x86_64-apple

 make

 ./grub-mkimage .........

```

Doubt if that is it, but give it a try.

IDK much about compiling either.

---

### Post by user12021 on 2008-12-01
I'm about to try again. this time I'm using this, which is what you had in your documents.
```
./grub-mkimage -d . -o grub.efi apple appleldr boot cat chain configfile cpio date ext2 echo fat gpt help hexdump hfs hfsplus iso9660 linux ls normal pc reboot reiserfs scsi search sleep xfs
```

EDIT:
No luck.

---

### Post by pxwpxw on 2008-12-01
Suggest - 

I will try getting a 64 bit version going here, cross compile or install an adm64 system.

You might consider a small i386 system on a usb stick to get something working as model for 64bit. I have done that here.

Use macosx (not ubuntu) to partition a usb flash drive (4GB or so) - a bit slow, external usb HD faster. 

use macosx diskutilty - parttion option GUID,

partition 1 hfsplus macosxextended no journal 20 MB 
partition 2 free or FAT32

Install small system using intrepid i386 server CD (no gui initially) 

 using p2 as /
 no swap.

Put the i386 /EFI/grub/... in p1, refit will see it.

Edit:
You can of course just install /EFI/grub/ on the usb stick first to see that it boots, but must use the macosx GUID partition option.

---

### Post by user12021 on 2008-12-01
I think the only flash drive I have is a 2 gigabyte one.
I'll try out your suggestion once I have the necessary equipment.

---

### Post by pxwpxw on 2008-12-01
2 gb is plenty for a server CLI install - uses less than 1 gb.

If you do that, use manual partitioning and check "do not use" for all the internal HD partitions.

---

### Post by user12021 on 2008-12-01
I can't seem to find my flash drive anywhere. The only thing I have with a USB interface is my old ipod.

Back to my other options:
Can I install GRUB legacy on the partition instead, bless that, and boot using that?

---

### Post by pxwpxw on 2008-12-01
No.

I'll try amd64 here, maybe make a 64 bit grub to try,

---

### Post by user12021 on 2008-12-01
Allright.
I was looking at the thing it kept repeating when it was trying to load linux with the 32 bit grub2
```
ata5.00: status: { DRDY }
ata5: soft resetting link
ata5.00: configured for PIO0
ata5: EH complete
ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata5.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
         cdb 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00
         res 40/00:00:00:00:00/00:00:00:00:00/ Emask 0x4 (timeout)
```
and i found this:
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

thanks for all you're doing to help.

---

### Post by pxwpxw on 2008-12-01
Thanks, good ref.
downloading amd64 now.
will get back when its installed and have tried grubefi.
cu

---

### Post by pxwpxw on 2008-12-01
Installed macbook2,1 intrepid amd64 on external, 
boot with i386 grub.efi loads kernel 
and then reproduces the ata5 timeout / root system timeout as above, so thats the problem.

Now will compile for grub.efi 64 bit.

---

### Post by pxwpxw on 2008-12-02
**user12021**

I built the x86_64 grub efi and tried it, but no good, same results  you reported.
refit reports x86_64 not supporteds, refit shell is IA32. 
Apple boot screen just ignores it (defaults to the current boot when selected).

Now that I have an amd64 ubuntu system, I will go back to try some other kernel options with 32bit grub.efi.

---

### Post by user12021 on 2008-12-02
Tell me if you get anything to work.

32 bit grub1 can load a 64 bit os. i don't see why 32 bit grub2 can't do it.

---

### Post by pxwpxw on 2008-12-02
> **pxwpxw said:**
> **user12021**

I built the x86_64 grub efi and tried it, but no good, same results  you reported.
refit reports x86_64 not supporteds, refit shell is IA32. 
Apple boot screen just ignores it (defaults to the current boot when selected).

Now that I have an amd64 ubuntu system, I will go back to try some other kernel options with 32bit grub.efi.

I tried kernel boot options fro ACPI, PCI  etc, no luck with that approach.

---

### Post by pxwpxw on 2008-12-02
> **user12021 said:**
> Tell me if you get anything to work.

Yes certainly.
> 
32 bit grub1 can load a 64 bit os. i don't see why 32 bit grub2 can't do it.
Yes, exactly.

It is loading the 64bit kernel and getting it started, as you have shown, but the problem then is after the kernel is loaded and the booloader has terminated. The kernel/initramfs then has to use the EFI interface to the hardware, not the bios compatibility that it uses when booted by grub-pc.
You could see all this in the startup log dmesg - if it got far enough to produce one. It is the same sort of issue that requires disabling accelerated graphics.

So it is the difference in configuration between the current i386 and the amd64 that is the problem, not the 32/64 bit. A different 64 bit kernel configuration might work around it. 
The grub2 compile defaults to 32bit for apple efi, and the grub.efi built with the x86_64 configuration is  incompatible with my MacBook and refit, so the suggestion to use x86_64 for a MacBook may not have been meant for the MacBook 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook). 
I had to install  the gcc-multilib package to build the x86_64 on my i386 installation.

The short answer is that the current grub.efi works for  i386 kernel and the i386 installation.
but it does not work with the AMD64 installation.
 The grub source built wit ./configure --with-platform=efi
will build for the default target i386 for intel macs.

You can still use the grub.efi to load eternal i386 kernels.

Your efforts to get it going have been very useful in exposing the 64 bit issue, I will look a bit more at that, but I doubt if I can take it much further, rapidly getting out of my depth here.

Sorry you had all that trouble, your problem was probably entirely due to the amd64 system, I was hoping to get your system running with grub.efi, it really does work very well.

I will add a note to my grub2 EFI thread    
[grub2 EFI boot loader internal/external booting]("http://ubuntuforums.org/showthread.php?t=995704")

---

### Post by user12021 on 2008-12-03
That's a real shame.
Oh well, I guess I'll just have to bite the bullet, and continue to boot with grub1.
Thanks for all you did to help.

---

