---
title: "installing on an external usb drive... on a mac!"
date: 2007-09-27
forum: Apple PPC Users
---

### Post by Lo'oris on 2007-09-27
Is it possible to install ubuntu on an external usb drive, if I have a mac/ppc?

Please notice that the drive may be not connected at times, and I'd need the boot loader to boot anyway the OSX in the internal hdd even if the usb one is off.

I searched and found nothing about it.

I have an iBook G4 new, and OSX 10.3.9, if that matters.

---

### Post by pxwpxw on 2007-09-27
> **Lo'oris said:**
> Is it possible to install ubuntu on an external usb drive, if I have a mac/ppc?

Please notice that the drive may be not connected at times, and I'd need the boot loader to boot anyway the OSX in the internal hdd even if the usb one is off.

I searched and found nothing about it.

I have an iBook G4 new, and OSX 10.3.9, if that matters.

Yes it is possible for an external hard disk, but not as easy as a standard install.

If your external casing can use a firewire connection that is nuch better.
Either way, you need to put some boot files on your Macosx partition, or it is better if you can make a small hfs partition (about 50Mb) on your internal drive. 
With OSX 10.3.9, I think you would need to re-install macosx for that, or risk shrinking the macosx partition with the ubuntu partitioner.

You may need to use the Option-key - Apple Picker to choose between macosx or linux.

---

### Post by Lo'oris on 2007-09-27
> **pxwpxw said:**
> Yes it is possible for an external hard disk, but not as easy as a standard install.
Because I have to install the boot-loader manually, or there are other problems?

> **pxwpxw said:**
> Either way, you need to put some boot files on your Macosx partition, or it is better if you can make a small hfs partition (about 50Mb) on your internal drive.
Because the bootloader is like grub that reads a config file (and not like lilo that have it built in the mbr)? Because the kernel must reside on the internal hd? Or both? -.-

> **pxwpxw said:**
> With OSX 10.3.9, I think you would need to re-install macosx for that, or risk shrinking the macosx partition with the ubuntu partitioner.
I've made a full (I hope) backup anyway, but re-installing everything would be... unpleasant. And the full backup is in the (already partitioned) external usb drive, so I can't risk losing them both :P

So far I've not understood how much safe is the partition shrinker (is it parted or another one?). Anyone tested it on 10.3? (disk is FUJITSU MHT2060AT 60GB, if that matters).

> **pxwpxw said:**
> You may need to use the Option-key - Apple Picker to choose between macosx or linux.
What's that? A sort of bootloader? Option-key? If it implies holding the option key while booting, well, I use an external usb keyboard. I *can* (for now, but keyboard is a bit broken and sometimes keys die) use the laptop's too, but it would be slightly inconvenient. Actually I have almost everything external, and I'm using the iBook as it was a desktop (I understand the external monitor is supported, if not during install phase, right? same thing for airport extreme, right?).

---

### Post by stmiller on 2007-09-27
You should be able to run the Ubuntu installer as normal, and just make sure to select the external drive as where you want to install Ubuntu.

Mac hardware cannot boot to a USB external drive for an operating system. Only firewire.

To get it to boot to a USB Linux drive, you'll have to create a custom yaboot.conf and write that to the boot partition of the internal drive. This is sort of advanced to set up, but do-able.

So like pxwpxw says, for an easy way you can just hold down the 'Alt' key at boot which goes to a boot loader menu and there you can select Linux on the external drive. This will only work with a firewire drive though. :)

---

### Post by Lo'oris on 2007-09-27
> **stmiller said:**
> You should be able to run the Ubuntu installer as normal, and just make sure to select the external drive as where you want to install Ubuntu.

Mac hardware cannot boot to a USB external drive for an operating system. Only firewire.

To get it to boot to a USB Linux drive, you'll have to create a custom yaboot.conf and write that to the boot partition of the internal drive. This is sort of advanced to set up, but do-able.
Just one final question before I proceed.

Let's say I install everything but not the bootloader. Then I reboot to OSX. Will I be able to boot ubuntu using a boot cd or something like that, and *then* install the bootloader?

---

### Post by stmiller on 2007-09-27
Yes- the alternative CD has a 'rescue mode' where you can do some utilities at the command line. But I caution you: you will have to make a custom yaboot.conf to point to the location of your USB drive. And the yaboot.conf must be written to the internal drive, writing over the correct partition. 
This is very advanced stuff. Search google or this forum section for more info on this. It has come up here before I believe.

But possibly you can just hold down 'Alt' while booting to pick Linux to boot into, and avoid all of this yaboot stuff. (? I cannot confirm if this will work with a USB drive.)

---

### Post by Lo'oris on 2007-09-27
The only useful page about this I found was [this one](http://www.macosxhints.com/article.php?story=20061017084322177).
Not nice, since reading all the comments, it more or less say "it's random, for someone works for someone doesn't".

Also, they don't talk about booting into linux, only into osx, so it may differ.

I'll try installing ubuntu into the usb drive, not caring about booting, and I'm downloading the alternate cd. Then, we'll see.

*edit*: if searching google didn't help much, searching this forum I found something, I'll read it and let you know

---

### Post by Lo'oris on 2007-09-27
ok searching the forum archives I found many threads but few solutions.

I'll quote the most (only?) one that is both relevant and not chaotic:

> **pxwpxw said:**
> From what you say, these look to be the options:

1. You might be able to shrink the MacosX partition to make room for a linux boot partition, Apple_Bootstrap, hfs format, around 30Mb. This would hold  boot and kernel files ofboot.b, yaboot, yaboot.conf, vmlinux, initrd.img.  Probably try to include that bootstrap partition in the linux install, then add kernel images and edit yaboot.conf. This would give a text boot menu to select Macosx or linux, with preselected default and timeout.
Catch: I dont know how shrinkable your Macosx partition might be.

2. Or put the boot and kernel files, except for ofboot.b. in the existing MacosX hfs+ partition. This would use the Option apple picker to boot Macosx, with auto boot to the external linux via boot-device setting and yaboot, otherwise I think it will default to macosx if the external is missing. 
Just accept an installer default boot partiton on the external usb. Later the yaboot install to usb bootstrap  partition will probably fail, just continue (it will install the yaboot package files on the root / partiton).

Both options are easier said than done, but I think (2) would be easiest to try, you could always go to (1) later.
I'd go try option 2.
I'm just a bit confused, let's see if I understood correctly.
• I install ubuntu on usb drive, not touching the internal one
then, after it's installed
• I move the /boot from the usb drive to the internal one
• I make according changes of paths in the yaboot.conf file (that is similar to grub.conf, isn't it?)
• to boot, I'll need to hit the alt key (hope usb keyboard will work)

did I get it right?

one question: the quoted post assumes it will boot by default to ubuntu, and also is unsure if it will boot osx if the usb drive is off. Any news about that?

---

### Post by Lo'oris on 2007-09-27
hoping it will be useful:

```
[root@Argothia looris]# nvram boot-device
boot-device     hd:,\\:tbxi

[root@Argothia looris]# bless -info -verbose
Current OF: hd:,\\:tbxi
bsd name is /dev/
Could not get partition type for /dev/
Can't get device for hd:,\\:tbxi: 3

[root@Argothia looris]# diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *55.9 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:              Apple_HFS Argothia           55.8 GB   disk0s3
/dev/disk1
   #:                   type name               size      identifier
   0: FDisk_partition_scheme                    *153.4 GB disk1
   1:           Linux_Ext2FS                    94.1 MB   disk1s1
   2:              Apple_HFS Abura Gaeshi       48.8 GB   disk1s2
   3:             DOS_FAT_32 ONI                55.7 GB   disk1s3
   4:           Linux_Ext2FS                    7.8 MB    disk1s5
   5:           Linux_Ext2FS                    47.3 GB   disk1s6
   6:             Linux_Swap                    1.4 GB    disk1s7

[root@Argothia looris]# pdisk /dev/disk0 -dump
/dev/disk0  map block size=512
   #:                 type name                  length   base      ( size )
   1:  Apple_partition_map Apple                     63 @ 1        
   2:           Apple_Free                            0+@ 64       
   3:            Apple_HFS Untitled           116948022 @ 262208    ( 55.8G)
   4:           Apple_Free                            0+@ 117210230

Device block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0

[root@Argothia looris]# file /dev/disk* -s
/dev/disk0:   Apple Partition data block size: 0 first type: ple_partition_map, number of blocks: 4145520,
/dev/disk0s1: Apple Partition data block size: 0 first type: ple_Free, number of blocks: 0,
/dev/disk0s3: Apple Partition data block size: 0 first type: ple_Free, number of blocks: 0,
/dev/disk1:   x86 boot sector
/dev/disk1s1: x86 boot sector, extended partition table
/dev/disk1s2: x86 boot sector, extended partition table
/dev/disk1s3: x86 boot sector, extended partition table
/dev/disk1s5: data
/dev/disk1s6: Linux rev 1.0 ext3 filesystem data (large files)
/dev/disk1s7: Linux/i386 swap file (new style)
```

in the USB drive, first there are 100 free MB, then three extended linux partitions (boot, root and swap), then an HFS+ and a VFAT partition.

afaik there's free space in the internal drive between 2 and 3, dunno if it can be used or not.

---

### Post by Lo'oris on 2007-09-27
I've poked around a bit.

>    1:           Linux_Ext2FS                    94.1 MB   disk1s1
This was supposed to be free space, for some reason it wasn't.
Now I've deleted it, and since when I run yabootconfig it says I must have a AppleWTF 800k partition, I tried to create it.

But both fdisk and mac-fdisk, that have the command to create it, say that /dev/sde (as this usb drive is called under linux) have no record label.

parted instead sees it, but can't create that kind of partition, afaik.

partman sees the disk, creates the partition, but... well it fakes. It actually created an ext partition O_o

I'm clueless. I wanted to at least *try* to install yaboot there, but it's a mess, I can't even understand why some programs don't work :/

and the installer is bugged, I choose the option "use free space as you wish" and it pretended to create a root, a boot and a swap partition.
but it ignored the boot one, and installed boot files in the root.

ideas anyone?

---

### Post by pxwpxw on 2007-09-27
[B]Lo'oris
[/B]
I just looked at the thread again, I will try to post an outline  after I read the details already posted. You have gone right off track - it is not meant to be nearly as difficult as all that. You are correct that booting external Macosx is a different proposition - mainly because Apple designed for it. Might be some hours before I can get to it.

---

### Post by Lo'oris on 2007-09-28
good, good, I'll wait, thanks : )

---

### Post by pxwpxw on 2007-09-28
yaboot external booting
[http://ubuntuforums.org/showthread.php?p=3441233#post3441233](http://ubuntuforums.org/showthread.php?p=3441233#post3441233)

---

### Post by Lo'oris on 2007-09-28
> 2. A separate Apple_Bootstrap hfs partition and full yaboot instllation on the internal drive will allow normal boot selection by the Apple Option key graphical picker (Apple Picker), or the ofboot/yaboot text menu.
Since I've found 100 free MB in my internal drive, how can I create this partition there?
IF they are really free and not some other osx thing I can't imagine.

edit: sorry if I've answered here and not in the linked thread, I've no idea why I did that -.-

---

### Post by pxwpxw on 2007-09-29
> **Lo'oris said:**
> Since I've found 100 free MB in my internal drive, how can I create this partition there?
IF they are really free and not some other osx thing I can't imagine.

edit: sorry if I've answered here and not in the linked thread, I've no idea why I did that -.-

I think there may be a problem with your external drive using the MSDOS or MBR partitioning scheme. Normally, for a Macosx system, I would set the drive up from the start as an Apple Partition Map scheme (using Disk Utility). I think this is going to make trouble, and probably responsible for some partitioning problems you have already seen.

 I have just been looking at a WDC Mybook which comes with msdos partitioning and checking with an iBookG4, macosx and linux.
Although I can boot linux on an MBR system ext3 primary partition,( using yaboot on the iBook) there seem to be problems with hfs (macos) partitions, and limitation to 4 primary partitions. I cannot get extended/logical to do much, and gparted gets discouraged easily.

So would it be possible to reformat the external to Apple Partitoning scheme. The external I use for linux ppc is formatted that way, no limitations - but not good for windows PC machines.

In the apple partioning there are some 128MB "apple free" spaces between hfs partitions, and I have been using them for bootstrap partitions - so far without problems, no guarantees though. These do not show in macosx diskutil. 
  
Can you use firewire? - that is much better option than usb.

Can you run pdisk for the external (/dev/disk1) to see what happens, and it would be a good idea to get a ubuntu Desktop feisty 704 CD burned to help with checking the system and partitioning as seen by ubuntu, or for post-install fixups.

Need to get accurate partitioning info to see what comes next.

---

### Post by Lo'oris on 2007-09-29
> **pxwpxw said:**
> I think there may be a problem with your external drive using the MSDOS or MBR partitioning scheme [...]
changing it is not an option, unfortunatly, because the disk must also be used by windows people. And it doesn't support firewire, btw :/

> **pxwpxw said:**
> In the apple partioning there are some 128MB "apple free" spaces between hfs partitions, and I have been using them for bootstrap partitions - so far without problems, no guarantees though. These do not show in macosx diskutil.  
well, this is good, I guess we can use it for making an apple_bootstrap in the internal disk, then?

> **pxwpxw said:**
> Can you run pdisk for the external (/dev/disk1) to see what happens, and it would be a good idea to get a ubuntu Desktop feisty 704 CD burned to help with checking the system and partitioning as seen by ubuntu, or for post-install fixups.

Need to get accurate partitioning info to see what comes next.
The cd, I already have :)
pdisk isn't happy. -l (the letter) option doesn't exist here (10.3), so i guessed the correct command would be "pdisk /dev/disk1 -dump", but it returned nothing.
```
[root@Argothia looris]# pdisk /dev/disk1 -dump
[root@Argothia looris]# 
```

Maybe I reboot to ubuntu and do it with fdisk and parted?

---

### Post by Lo'oris on 2007-09-29
we have something odd going on here.
I've booted the live cd, and noticed that using it the internal disk was hda, and the external sda (contrary to the alternate cd which saw it as sde).

While I was able to fdisk the internal one without problems, any attempt to do it to the external one, failed. Both fdisk, mac-fdisk, and parted.

Surprisingly, very surprisingly, gparted worked instead O_o
While I'm completely clueless about why parted doesn't work but gparted does (don't they both use libparted?), I had no better idea than taking a screenshot.

[http://looris.net/~looris/salcazzo/sda_screenshot.png](http://looris.net/~looris/salcazzo/sda_screenshot.png)

please notice that sda5 is empty, and everything is inside sda6 (a bug in the installer, I guess).

```
root@ubuntu:~# fdisk -l /dev/hda
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2              Apple_Free                       262144 @ 64        (128.0M)  Free space
/dev/hda3               Apple_HFS Untitled           116948022 @ 262208    ( 55.8G)  HFS
/dev/hda4              Apple_Free                           10 @ 117210230 (  5.0k)  Free space

Block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0
```

---

### Post by pxwpxw on 2007-09-29
**Lo'oris**
You still have not answered my question about using firewire instead of usb??

I think you may have to trash that external and repartition as an Apple drive, but go ahead and try it as is to see how things work.  First find your /boot partitiion and post
 ```
 
ls -l /boot/ 
df

```

Yes for ppc, fdisk=mac-fdisk ( ls -l `which fdisk` ) and they are Apple centric. parted I think sees apple and mbr stuff, and so on. PC fdisk cant see apples. 
Thats all caused by having the MSDOS MBR partitioning on the external, and will be trouble.

There's ypur Apple_Bootsrap answer at /dev/hda2 128MB.
 You can easily make it an hfs partition using Gparted running the  desktop CD   choosing New partiton, hfs format. The hfs has a name length limit, I think its 31 characterrs, you hve to shorten kernel names for copying to hfs sometimes , but is writeable from both linux and macosx, very convenient. Thats all you need to boot from yaboot with kernel,  and you can just converrt it later to a genuine Apple_Bootstrap.
 
Easiest way to make it a proper Apple-Bootstrap is to do it in the install partitioning.
Delete it,, then select it and choose "Use as boot" then automatically the installer gives it the correct name and format and uses it for yaboot. But you need to be using the Alternate CD, manual partitoning, and probably Expert install. 
Anyway, a trial install is the easiest way to get the details right -  no fancy stuff, just see how it all goes and do the final install later.

---

### Post by Lo'oris on 2007-09-29
first of all, thanks for the prompt reply, and sorry if I took so much to answer, but sometimes I don't receive email notifications O_o

> **pxwpxw said:**
> **Lo'oris**
You still have not answered my question about using firewire instead of usb??
I messed up the quote when I did, so you didn't notice, sorry :P
It doesn't support it :/

> **pxwpxw said:**
> I think you may have to trtash that external and repartition as an Apple drive
this I think I can't do because also people with XP will use that disk :/

> **pxwpxw said:**
> but go ahead and try it as is to see how things work.
[...]
I'm going to!

> **pxwpxw said:**
> First find your /boot partitioon and post
 ```
 
ls -l /boot/ 
df

```
I'll do that now.

---

### Post by Lo'oris on 2007-09-29
/boot is in sda6, just like all the rest of ubuntu.
I guess there's some kind of bug in the installer, since it said it would have used sda5 for /boot, but it didn't even touch it.

I've created an hfs partition in hda, and put everything that was in /boot except the symlinks.

now I guess I'm supposed to install yaboot, with an appropriate configuration file, and convert the partition to real apple_bootstrap?

when I rebooted after doing this, I guess OpenFirmware noticed partitions were changed, because appeared a folder icon with a "?", that soon became a Finder icon, and immediatly booted as normal. I guess that's supposed to happen, and while there was the "?" it was scanning for new bootable partitions.

```
ubuntu@ubuntu:~$ ls -l /boot/
total 23242
-rw-r--r-- 1 root root  386247 2007-04-15 06:47 abi-2.6.20-15-powerpc
-rw-r--r-- 1 root root  399921 2007-04-15 06:54 abi-2.6.20-15-powerpc64-smp
-rw-r--r-- 1 root root   71267 2007-04-15 05:03 config-2.6.20-15-powerpc
-rw-r--r-- 1 root root   69317 2007-04-15 06:02 config-2.6.20-15-powerpc64-smp
lrwxrwxrwx 1 root root      34 2007-04-15 13:54 initrd.img -> initrd.img-2.6.20-15-powerpc64-smp
-rw-r--r-- 1 root root 7937103 2007-04-15 13:54 initrd.img-2.6.20-15-powerpc64-smp.bak
lrwxrwxrwx 1 root root      28 2007-04-15 13:53 initrd.img.old -> initrd.img-2.6.20-15-powerpc
-rw-r--r-- 1 root root  738673 2007-04-15 06:47 System.map-2.6.20-15-powerpc
-rw-r--r-- 1 root root 1465679 2007-04-15 06:54 System.map-2.6.20-15-powerpc64-smp
lrwxrwxrwx 1 root root      31 2007-04-15 13:54 vmlinux -> vmlinux-2.6.20-15-powerpc64-smp
-rw-r--r-- 1 root root 4572309 2007-04-15 06:47 vmlinux-2.6.20-15-powerpc
-rw-r--r-- 1 root root 8156208 2007-04-15 06:54 vmlinux-2.6.20-15-powerpc64-smp
lrwxrwxrwx 1 root root      25 2007-04-15 13:53 vmlinux.old -> vmlinux-2.6.20-15-powerpc

ubuntu@ubuntu:~$ ls -l /media/Untitled/
total 13135
-rw-r--r-- 1 ubuntu ubuntu  386247 2007-04-15 06:47 abi-2.6.20-15-powerpc
-rw-r--r-- 1 ubuntu ubuntu   71267 2007-04-15 05:03 config-2.6.20-15-powerpc
-rw-r--r-- 1 ubuntu ubuntu 7679731 2007-09-27 20:43 initrd.img-2.6.20-15-powerpc
-rw-r--r-- 1 ubuntu ubuntu  738673 2007-04-15 06:47 System.map-2.6.20-15-powerpc
-rw-r--r-- 1 ubuntu ubuntu 4572309 2007-04-15 06:47 vmlinux-2.6.20-15-powerpc

ubuntu@ubuntu:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
tmpfs        tmpfs      257552       268    257284   1% /lib/modules/2.6.20-15-powerpc/volatile
tmpfs        tmpfs      257552       268    257284   1% /lib/modules/2.6.20-15-powerpc/volatile
varrun       tmpfs      257552       108    257444   1% /var/run
varlock      tmpfs      257552         0    257552   0% /var/lock
udev         tmpfs      257552       200    257352   1% /dev
devshm       tmpfs      257552         0    257552   0% /dev/shm
tmpfs        tmpfs      257552        12    257540   1% /tmp
/dev/sda5     ext2        7745        45      7300   1% /media/disk
/dev/sda2  hfsplus    51199152  48703316   2495836  96% /media/Abura Gaeshi
/dev/sda6     ext3    48813188   2037296  44296264   5% /media/disk-1
/dev/sda3     vfat    58407888  52006672   6401216  90% /media/ONI
/dev/hda3  hfsplus    58474008  42429200  16044808  73% /media/Argothia
/dev/hda2      hfs       65526     14162     51364  22% /media/Untitled

root@ubuntu:~# fdisk -l /dev/hda
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2               Apple_HFS untitled              131073 @ 64        ( 64.0M)  HFS
/dev/hda3               Apple_HFS Untitled           116948022 @ 262208    ( 55.8G)  HFS
/dev/hda4              Apple_Free Extra                 131071 @ 131137    ( 64.0M)  Free space
/dev/hda5              Apple_Free Extra                     10 @ 117210230 (  5.0k)  Free space

Block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0
```

---

### Post by pxwpxw on 2007-09-29
That seems ok so far. You dont do anything to hda2 except add files - thats your temporary yaboot hfs boot partition? Lets just call it "hda2" for now.
Don't confuse that with the /boot partition you copied the kernel from as seen in   /media/Untitled.
 And hda2 does not need the Apple_Bootstrap label for running yaboot. 

Your ubuntu root is /dev/sda6.
Please correct me if I get anything wrong here. 

I cant comment on everything, but all seems as expected, just press on with getting ubuntu rebooted. 

The installer has probably changed your boot-device to something wrong, hence the [?].

Check that from Macosx so we know what the installer did -
```

 nvram boot-device

```

You now need to get a copy of yaboot onto your hda2 partition.
You will find one in the /install folder of your Ubuntu CD, or in your installed system in /usr/lib/yaboot/


Then your yaboot.conf can be based on my yaboot-external-booting thread example, the usb section, modified for your system. Try fixing it yourself for your system and post it here for me to debug. I want to know how people go with that task.

---

### Post by Lo'oris on 2007-09-29
> **pxwpxw said:**
> That seems ok so far. You dont do anything to hda2 except add files - thats your temporary yaboot hfs boot partition? Lets just call it "hda2" for now.
Don't confuse that with the /boot partition you copied the kernel from as seen in   /media/Untitled.
 And hda2 does not need the Apple_Bootstrap label for running yaboot. 

Your ubuntu root is /dev/sda6.
Please correct me if I get anything wrong here. 
everything correct

> **pxwpxw said:**
> The installer has probably changed your boot-device to something wrong, hence the [?].
the installer? actually, I did it by hand.

> **pxwpxw said:**
> Check that from Macosx so we know what the installer did -
```

 nvram boot-device

```
```
[root@Argothia looris]# nvram boot-device
boot-device     hd:,\\:tbxi
```
(just like it was before)

> **pxwpxw said:**
> You now need to get a copy of yaboot onto your hda2 partition.
You will find one in the /install folder of your Ubuntu CD, or in your installed system in /usr/lib/yaboot/

Then your yaboot.conf can be based on my yaboot-external-booting thread example, the usb section, modified for your system. Try fixing it yourself for your system and post it here for me to debug. I want to know how people go with that task.
done:
```
timeout=10
default=usb

image=/vmlinux
label=ubuntu
root=/dev/sda6
read-only
initrd=/initrd.img
device=hd0:
partition=2
```
(vmlinux and initrd.img are copies of the ones with longer names)
correct me if I'm wrong:
device=hd0: and partition=2 are just like in parted you do hd0(2) or something like that?
so, maybe I need to use partition=1 because it starts from 0 instead? or not? mmh but I notice you said it was sda3, and you use partition=3, so my partition=2 maybe is correct.

then I guess I'll have to call
```
nvram "boot-device=hd:2,\yaboot"
```

I'm a little confused by the auto-boot. If I understood correctly, I have to select either osx or yaboot with openfirmware, because yaboot can't boot osx?
I have a little problem with openfirmware: I notice the mouse doesn't work, and it only accepts keyboard selection. BUT my laptop keyboard has the arrows (except "left", for now) broken, so I wouldn't be able to do that when I won't have the usb keyboard at hand? That's one of the reasons I'd like to default to osx, if possible.

---

### Post by pxwpxw on 2007-09-30
**Lo'oris**

1. corrected yaboot.conf for your system.
```

###====yaboot.conf====
# 30sep2007pxw
# yaboot.conf for booting kernel in /dev/hda2 
# to external ubuntu root at /dev/sda6
# yaboot, yaboot.conf, vmlinux, initrd.img are all in the root of hda2.

timeout=10
# defaults to first image

###
image=/vmlinux
	label=ubuntu
	root=/dev/sda6
	read-only
	initrd=/initrd.img
device=hd:
partition=2
###
image=halt
# gets back to open firmware.
###===end yaboot.conf====

```

2. boot yaboot

```

sudo nvram "boot-device=hd:2,\yaboot"

```
Correct, and on restart expect to start ubuntu boot, but you wont see anything from yaboot unless you boot from the open firmware text screen.

3. Other

Mouse and keyboard problems - touch pad?

Open firmware devices
 hd: is /dev/hda 
 hd:2,\yaboot  is /dev/hda2/yaboot
Not like grub.
 
This boot method is only a temporary fix until the final yaboot install can be done, but it should be workable although a bit inconvenient. Its a bit rough but will let you check the ubuntu installation and go from there.

4. Getting back to Macosx on /dev/hda3

If you can use your ubuntu desktop CD to access the forum here, that should cover most problems, but here is a survival kit, suggest you try some of this stuff.

Option key - hold down then start up, gives the Apple picker - graphical screen with icons one for macosx, none for linux. May take a minute for the mouse cursor to be enabled.

Zap Pram - hold down Command-Option-P-R at start for 2 chimes. Resets boot-device
(to hd:,\\:tbxi)

From open firmware text screen - hold down Command-Option-O-F at start.
```

For macosx
0> boot hd:,\\:tbxi

For yaboot
0> boot hd:2,yaboot

To restart 
0> reset-all

```
Other OF commands - printenv, setenv, devalias, dir

From ubuntu:
 the boot-device can be read and set using nvsetenv
(partition number for macosx will be necessary when the full yaboot install is on hda2, also a tbxi type)
```

sudo nvsetenv boot-device "hd:3,\\\:tbxi"
nvsetenv boot-device
## sometimes \ needs an extra \, so always check the result to make sure, varies. 

```

And from macosx, to set it for ubuntu
```

sudo nvram boot-device="hd:2,\yaboot"

```

---

### Post by Lo'oris on 2007-09-30
ok that's fine I'll try.
just one thing: from ubuntu live cd I can't access Internet because it fails to load the module for airport extreme. It said something like bcm43xx, module not loaded. I'll post the exact error if it can't find it again.
but don't worry, in case of emergency I can move the computer where cable reaches ;)

---

### Post by Lo'oris on 2007-09-30
fine. I was able to boot to linux and boot back to osx. What's next step? :)

airport and dual head still don't work, but this will go to a new thread, I guess

---

### Post by pxwpxw on 2007-09-30
Good, I think you just made history.

Next is to make the Apple_Bootstrap and re run yaboot installer all from ubuntu on the external.
Using mac-fdisk b to create a standard small  Apple_Bootstrap partition at the start of hda2 and then yabootconfig does the rest ( including rewrite yaboot.conf) , for the bootstrap without the kernel. 

Then use gparted to make the rest of old hda2 into a hfs partition around 100Mb+, as before, dont know what number that will be say hdax. So vmlinux and initrd.img go in hdax, leaving about 100Mb for use. 

Then fixup yaboot.conf on the bootstrap, for new kernel path, You will need morre info on that laterr. ( The yaboot.conf in /etc/yaboot.conf is only used for installation). 

So first step, copy all of hda2 to a folder on Macosx or somewhere safe on the external or a usb stick.
But you can easily just make new kernel copies from ubuntu to hdax now.

Also please post the original yaboot.conf found in /etc/yaboot.conf so I can see what the installer did first time.

Find out howw to drive mac-fdisk, it makes a 800Kb bootstrap using meu item b. You can copy and paste the base address from the partiition listing to the command in mac-fdisk, and you can do a trial run by not writing the change. You will understand alll that when you run mac-fdisk, the manual for mac-fdisk is around 10 years out of date.

I think thats a bit sketchy, and yabootconfig needs care to ensure it hits the right target, please read and ask if you need more detail, I possibly missed some vital item.

---

### Post by Lo'oris on 2007-09-30
> **pxwpxw said:**
> Good, I think you just made history.

Next is to make the Apple_Bootstrap and re run yaboot installer all from ubuntu on the external.
Using mac-fdisk b to create a standard small  Apple_Bootstrap partition at the start of hda2 and then yabootconfig does the rest ( including rewrite yaboot.conf) , for the bootstrap without the kernel. 

Then use gparted to make the rest of old hda2 into a hfs partition around 100Mb+, as before, dont know what number that will be say hdax. So vmlinux and initrd.img go in hdax, leaving about 100Mb for use. 

Then fixup yaboot.conf on the bootstrap, for new kernel path, You will need morre info on that laterr. ( The yaboot.conf in /etc/yaboot.conf is only used for installation). 

So first step, copy all of hda2 to a folder on Macosx or somewhere safe on the external or a usb stick.
But you can easily just make new kernel copies from ubuntu to hdax now.

Also please post the original yaboot.conf found in /etc/yaboot.conf so I can see what the installer did first time.

Find out howw to drive mac-fdisk, it makes a 800Kb bootstrap using meu item b. You can copy and paste the base address from the partiition listing to the command in mac-fdisk, and you can do a trial run by not writing the change. You will understand alll that when you run mac-fdisk, the manual for mac-fdisk is around 10 years out of date.

I think thats a bit sketchy, and yabootconfig needs care to ensure it hits the right target, please read and ask if you need more detail, I possibly missed some vital item.

[as you can read here](http://ubuntuforums.org/showthread.php?p=3451088), I'm now posting under ubuntu, with a working Airport Extreme : )

now, let's finish the yaboot job.
I'm not really sure I understood what you said, so I'll try to "explain" it and you correct me if I'm wrong.

· I backup /dev/hda2
· with mac-fdisk, i delete that partition, and create at the beginning of that free space one of type apple_bootstrap, of exactly 800k (k-bytes, right?)
· I run yabootconfig that does some things to that patition
· I use all the remaining free space (more or less 100MB) to create an hfs partition, with (g)parted
· I put the old backupped hda2 contents into this new hfs partition
· I adjust values of yaboot.conf to point them to the new hfs partition
· I reboot

so, if I understood correctly, we need two partitions because kernel doesn't fit in the apple_bootstrap one, that have (for some reason only Jobs knows) to be exactly 800k or won't work.

And I'll post here both the original and the modified yaboot.conf.

Under both osx and linux I'll be able to select the default boot device, and with alt will be able to choose one of them using openfirmware, right?

Tell me if I got everything right and I'll proceed, after all if I misunderstood something, it would be a mess : P

---

### Post by pxwpxw on 2007-09-30
Not quite right.

Yes you delete hda2 first in ubuntu. mac-fdisk or gparted should do.

I prefer this way: 
mac-fdisk makes 800Kb sized NewWorld Bootstrap automatically when you use the b option, you just have to give it the base address, which you read off its partition list for hda2. You dont get to choose the size.
For booting, any hfs compatible size will do, no magic size.

In that case, only vmlinux and initrd.img go in the larger hfs partition which can be seen by Macosx and ubuntu. and easily formatted by gparted.
(You can put them in Macosx partition, but problem writing from ubuntu).

Or if you like, mac-fdisk can create an Apple_Bootstrap partition and you specify the type, the start, and the size, it could use the whole of hda2, and then that is the bootstrap with room for vmlinux and initrd.img but you add them after reinstalling yaboot, which erases the bootstrap partition.
 Then you dont need the extra partition. The catch is, Macosx cant see the Apple_Bootstrap partition, not essential but convenient.

Your choice.

You do need to read man yabootconfig and it will overwrite the existing yaboot.conf.

sudo yabootconfig -b /dev/hda2 --debug --noinstall will just write yaboot.conf for a trial run (check that command, its from memory).

Carry on.

---

### Post by Lo'oris on 2007-09-30
now openfirmware boots both osx and linux : )

bootstrap is /dev/hda2, /boot is /dev/hda3, and root is still /dev/sda6

I encountered some problems, such as:
&#8226; (g)parted can't format hfs drives for some reasons, and fdisk doesn't format them but that's known
so i had to:
- delete the old hda2
- create the bootstrap with fdisk
- create hda3 with gparted
- install hfsutils and format both with hformat

also notice that putting hfs partitions in fstab doesn't support many options, so I had to put in only "default" and check=0

here's yaboot.conf, it's the same as the original, I just added image=halt and changed the timeout down to 5.

```
boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/sda6
timeout=5
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

image=/vmlinux
	label=ubuntu
	read-only
	initrd=/initrd.img
	initrd-size=8192

image=halt
```

still some questions/doubts.

1) is openfirmware always that slow? it's painful! it takes LESS time to boot the whole system after that, than the single openfirmware!

2) is it supposed to boot in text mode, instead of the nice ubuntu loading bar like the live cd has? Fine, I've had text mode boot for years, but if there's an easy way to get the graphical one, is better ; )

3) can I safely change the default back and forth with nvram/nvsetenv? in this case, if the booting choosing process can't be quickened, I think I'll make some scripts to change it easily and boot into the desired system

4) the *real* yaboot.conf, the one which is used, is that one in the bootstrap partition. the one in /boot and the one in /etc are useless, right?

5) image=halt doesn't work as expected. I thought it would boot osx, but looks like I misunderstood... it prompts openfirmware prompt, right? So, is there a way to boot osx from yaboot? it would solve the problems 1 and 3 : )

---

### Post by pxwpxw on 2007-09-30
I'm  lost, where have you got to now and how are you booting now.
Have you looked at man yabootconfig to see what it does? It will write /etc/yaboot.conf and Apple_Bootsrap /yaboot.conf,
but you can keep another  yaboot.conf for manually booting with yaboot as a backup - as you have been doing.

re dalays in openfirmware, when you refer to "Openfirmware" do you mean the Apple graphical icon picker screen, or the interactive Open firmware text screen i.e. what you get using Commad-Option-O-F. All this should improve greatly when you get finished with the boot installation.


About gparted and hfs, there was no problem before when originally creating new hda2 and selecting hfs filesystem, but that was done when you booted from the CD. Maybe you had that problem using gparted from the booted system - solution do it from the CD - comments? (useful info for others).

re halt - thats what it does, drop back to open firmware, but you cant do much at that level it is broken, just reset-all. Its only meant as an abort.

---

### Post by Lo'oris on 2007-10-01
I've already run yabootconfig, that has installed everything in hda2, the apple_bootstrap partition created yesterday.
while the kernel resides in hda3, and the rest of the system in sda6.

I can boot using openfirmware, or simply change the default boot device with nvram.

I was just wondering if it was normal to have a non-graphical boot.

About hfs, I created hda2 originally, using the livecd, where gparted is. In the installed system, there wasn't gparted, I had to install it manually. It is possible that if hfsutils are not present, he can't manage hfs partition. But I don't know, since after I installed hfsutils too, I directly used hformat without trying gparted again.

---

### Post by pxwpxw on 2007-10-01
**** edited quote

> **Lo'oris said:**
> I've already run yabootconfig, that has installed everything in hda2, the apple_bootstrap partition created yesterday.
while the kernel resides in hda3, and the rest of the system in sda6.

**** hda3 was Macosx? is that the 100MB hfs now?
**** Please post /etc/yaboot.conf (that should be what yabootconfig generated.
**** did you edit the yaboot.conf?
**** Have you got another yaboot.conf  with the kernel? If so please post.

I can boot using openfirmware, or simply change the default boot device with nvram.
**** Open firmware - Is that Using the Option key start - graphical screen?

I was just wondering if it was normal to have a non-graphical boot.
**** Yes you get the ofboot x - l - c menu but you can make it default to your choice of OS and short timeout, but what you see  depends on the auto-boot? setting.

About hfs, I created hda2 originally, using the livecd, where gparted is. In the installed system, there wasn't gparted, I had to install it manually. It is possible that if hfsutils are not present, he can't manage hfs partition. But I don't know, since after I installed hfsutils too, I directly used hformat without trying gparted again.
**** understood.


Excuse the **** , I am too lazy to split the quote up.

I am not sure if you are all finished, it seems the startup options are not as good as I would expect.

Can we just review this to make sure I know what you have in various boot partitions- I will post a list of what I think you should have shortly - 

This is what I think you should have: 

Internal HDD

1. Apple_Bootstrap (Hidden from Macosx)
hda2 (hfs) 800 KB.
 ofboot.b, yaboot, yaboot.conf
Normal boot-device, formatted, blessed, and files installed  by yabootconfig:
Ofboot Text Menu options for macosx, linux, network, cdrom.
Should also give a TUX icon in the Apple Picker graphical screen.

2. Yaboot boot partiton 
hda3 (hfs) 100 MB
 yaboot, yaboot.conf, vmlinux, initrd.img
Alternative manual linux yaboot option, also can boot rescue or installer kernel images if they are added.

3. Macosx system partition "startup disk"
hda? (HFS+ journalled)
Not used for booting linux, but could be alternative for 2.

External HDD

(usb enclosure, MBR partitioning scheme)
sda6 linux root.
 /etc/yaboot.conf installed by yabootconfig.

---

### Post by Lo'oris on 2007-10-01
mmmh.

not as good as you say it should be.

I'm not sure what ofboot is. I have hda2 of type apple_bootstrap, it contains those three files, and yes apple_picked have a linux logo for that partition.

hda3 contains kernel and another yaboot.conf (why having it both here and there?) but the only option is the only kernel installed. And "halt", as I added.

when I boot if I choose linux partition (or if i blessed it) I get one lilo-like prompt, such as "boot: ", and if I don't prompt anything, it boots. Dunno if it was supposed instead to have a full screen text, or graphical, picker.

osx partition is not hda5 and it boots if i select it from apple picker.

root is still sda6.
and there's a third yaboot.conf in /etc, right.

some outputs:
```
root@Argothia:~# fdisk -l /dev/hda
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap bootstrap               1600 @ 64        (800.0k)  NewWorld bootblock
/dev/hda3               Apple_HFS untitled              131073 @ 1664      ( 64.0M)  HFS
/dev/hda4              Apple_Free Extra                 129471 @ 132737    ( 63.2M)  Free space
/dev/hda5               Apple_HFS Untitled           116948022 @ 262208    ( 55.8G)  HFS
/dev/hda6              Apple_Free Extra                     10 @ 117210230 (  5.0k)  Free space

root@Argothia:~# df -Th -x tmpfs -x usbfs
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext3     47G  2,4G   42G   6% /
/dev/hda3      hfs     64M   26M   39M  41% /boot
/dev/hda2      hfs    797K  167K  630K  21% /Apple_Bootstrap
/dev/sda3     vfat     56G   50G  6,1G  90% /media/ONI
/dev/sda2  hfsplus     49G   47G  2,4G  96% /media/Abura Gaeshi
/dev/hda5  hfsplus     56G   41G   16G  73% /media/Argothia
```

---

### Post by pxwpxw on 2007-10-01
I see. I think I know. When you get the boot: prompt, press tab, there is no op[tion in the minimal yaboot.conf that yabootconfig writes.
Post the  /etc/yaboot.conf  or the Apple_Bootstrap yaboot.conf if you can. The answer is in there.

---

### Post by Lo'oris on 2007-10-01
> **pxwpxw said:**
> I see. I think I know. When you get the boot: prompt, press tab, there is no op[tion in the minimal yaboot.conf that yabootconfig writes.
Post the  /etc/yaboot.conf  or the Apple_Bootstrap yaboot.conf if you can. The answer is in there.

indeed, it's a very simple conf (I thought I already posted that, sorry):
```
looris@Jasconius:~$ cat /Apple_Bootstrap/yaboot.conf 
## yaboot.conf generated by yabootconfig 1.0.8
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of: 
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/sda6
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

image=/vmlinux
        label=ubuntu
        read-only
        initrd=/initrd.img
        initrd-size=8192

image=halt
```

---

### Post by pxwpxw on 2007-10-01
Yes, see that last comment line macosx=
If macosx is on hda5

You just add in the boot yaboot.conf
macosx=hd:5  
or in the /etc/yaboot.conf
macosx=/dev/hda5


But you have to edit the Apple_Bootstrap one, or else you edit the /etc/yaboot.conf and then from ubuntu on the external you run
```

sudo ybin -v

```
Check man ybin, I'm in macosx, I think its -v for verbose.

---

### Post by Lo'oris on 2007-10-01
you're right!

now yaboot boots both systems, and I also noticed defaultos option which is nice.

I like ybin! And anyway I couldn't have done it without using it, because for some reason the apple_bootstrap partition (hda2) can be mounted only read-only!
I also used the restricted and password options. (I'd post the file but now I'm under osx and can't access it :P)

So, now boot works, system works, etc. But I still have one problem related to having the system installed into usb.

If it goes to sleep:
&#8226; it can't be awakened with usb peripherials, only with iBook keyboard (that's annoying, but I can live with that);
&#8226; when it awakes, EVERY usb peripherial keeps on sleeping, including the disk where root system resides -_-' you can imagine what happens next;
&#8226; unplugging and re-plugging makes keyb. and mouse work again, but not the hard disk, and all the system becomes unstable;
I also have the suspect that airport too doesn't awaken after sleep, but it's only a suspect.

So far, I've disabled sleep at all, but if there's a solution, I'd hear it : )

---

### Post by pxwpxw on 2007-10-02
> **Lo'oris said:**
> you're right!

now yaboot boots both systems, and I also noticed defaultos option which is nice.

Good, especially interesting to see it can be done on an external usb HDD with MBR partitioning system. 


> 
I like ybin! And anyway I couldn't have done it without using it, because for some reason the apple_bootstrap partition (hda2) can be mounted only read-only!

Lots of options for yaboot.conf, all require rerun of ybin. 

The Apple_Bootstrap type intentionally hides it from the macos. Thats why the other standard hfs boot partition is convenient. 

Read all about it in man  bootstrap, mkofboot, ybin, yaboot*.


> 
I also used the restricted and password options. (I'd post the file but now I'm under osx and can't access it :P)

Would you post a copy of /etc/yaboot.conf as edited, when you can; a useful example.


> 
So, now boot works, system works, etc. But I still have one problem related to having the system installed into usb.

Um.


> 
If it goes to sleep:
&#8226; it can't be awakened with usb peripherials, only with iBook keyboard (that's annoying, but I can live with that);
&#8226; when it awakes, EVERY usb peripherial keeps on sleeping, including the disk where root system resides -_-' you can imagine what happens next;
&#8226; unplugging and re-plugging makes keyb. and mouse work again, but not the hard disk, and all the system becomes unstable;
I also have the suspect that airport too doesn't awaken after sleep, but it's only a suspect.

So far, I've disabled sleep at all, but if there's a solution, I'd hear it : )

I think that is the solution.

I get that sometimes with external HDD, have not noticed it with usb sticks.
It is compounded by the external going to sleep, even happens sometimes with G5 powermac and external. Have to restart to get it back.

There seems to be a general ubuntu ppc bug with sleep or suspend and apple notebooks.

No idea how to fix it.

You could submit a launchpad bug report,  I think  there are some similar problems with sleep and suspend in the current mac intel note books. Don't quote me though.

---

### Post by Lo'oris on 2007-10-02
so, many many thanks, I'll post those confs when I reboot, and maybe I'll try to write a not-detailed step-by-step guide if you think it will be usefu.l

---

### Post by pxwpxw on 2007-10-02
Yes, great idea. I can link to here from my  yaboot booting thread, or put it there. The partitioning arrangement using the apple free 128MB interstitial space would be particularly interesting, save me doing it.
 Did you get a solution for your external monitor?

---

### Post by Lo'oris on 2007-10-02
yep! I found a thread here that beautifully explain hot to make mergedfb work (basically an easy cut'n'paste). The problem was there were to many supposed "solutions" badly written.

well, I made it work in clone mode, which is what I wanted in first place, but tried anyway to make it work in non-clone and failed. Also, I still have to set resolutions.
What doesn't work is sound, and flash, but I'll open a new thread for that : )

---

### Post by Lo'oris on 2007-10-05
here's my working yaboot.conf:
```
boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/sda6
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
defaultos=macosx
password=xxx

macosx=/dev/hda5
        restricted
        label=osx

image=/vmlinux
        label=linux
        restricted
        read-only
        initrd=/initrd.img
        initrd-size=8192
```
: )

---

