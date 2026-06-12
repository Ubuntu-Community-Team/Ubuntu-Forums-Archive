---
title: "OSX is... gone? noooooooooo"
date: 2008-01-31
forum: Apple PPC Users
---

### Post by JustAboutRealJAR on 2008-01-31
sorry about the melodramatic title......

I installed kubuntu 7.10 Gutsy, and set it to guided - use remaining disk space...

well everything went well and kubuntu is running great... unfortunately, OS X seems to have disappeared... why won't it boot?

;(

Here's what happens when I tell yaboot to boot osx (press x)...

it goes into the normal boot up screen with the apple logo in the center and the spinner animation toward the bottom... but then... (after aboutt 2 or 3 min) the apple logo turns into a circle with the cross bar. I don't know the official name for that symbol... but it looks like this: [No Symbol]("http://en.wikipedia.org/wiki/Image:No_sign.svg")

I'm kind of upset... please help?

---

### Post by oswaldkelso on 2008-01-31
It sound like something is a little corupted somewhere before you mess to much with your system make sure osx still exists, sound like it does but check anyway from a terminal as root.

# fdisk -l

Becareful with fdisk you can wipe your system so no typos l is a small L.
I'm sure it there if it is I would just start over with osx install disk using the option that just keeps every thing as it was and replaces the system folder this option still gives you access to the old system folder should enything go missing.

I did this last month for my X as osx was playing up nice and easy you keep all your settings and applications.   If you do reinstall the system folder it will boot into osx hold down the option/alt key to select kununtu and you can change your boot option then. I would wait and see if anyone else comes up with something easier quicker to try first. But its sound like a hickup not a disaster (finger crossed).

---

### Post by JustAboutRealJAR on 2008-01-31
seems to be there...

```
$ sudo fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1               Apple_HFS Apple                     63 @ 1         ( 31.5k)  HFS
/dev/hda2         Apple_Bootstrap untitled                1954 @ 73400384  (977.0k)  NewWorld bootblock
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1  73138176 @ 262208    ( 34.9G)  HFS
/dev/hda4         Apple_UNIX_SVR2 untitled            15625001 @ 73402338  (  7.5G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                 3490946 @ 152810542 (  1.7G)  Linux swap
/dev/hda6         Apple_UNIX_SVR2 untitled            63783203 @ 89027339  ( 30.4G)  Linux native
/dev/hda7              Apple_Free Extra                 262144 @ 64        (128.0M)  Free space

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0

```

---

### Post by JustAboutRealJAR on 2008-01-31
hey... I just mounted the /dev/hda3... and verified that it still has the files from my old OSX installation

```
jim@G-Power-4:~$ sudo mkdir /media/hda3
jim@G-Power-4:~$ sudo mount /dev/hda3 /media/hda3
jim@G-Power-4:~$ cd /media/hda3/
jim@G-Power-4:/media/hda3$ ls
Applications  bin    Desktop DB  dev  Library  mach_kernel  Network  sbin    tmp    usr  Volumes
automount     cores  Desktop DF  etc  mach     mach.sym     private  System  Users  var

```

---

### Post by BladeMelbourne on 2008-01-31
Mac OS X is installed on my /dev/hda3 partition too:
```
mskinner@ZoeAnja:~$ sudo fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_UNIX_SVR2 home                97656251 @ 11904165  ( 46.6G)  Linux native
/dev/hda3               Apple_HFS tiger               11888100 @ 16065     (  5.7G)  HFS
/dev/hda4         Apple_UNIX_SVR2 root                43441956 @ 109560416 ( 20.7G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                 3299116 @ 153002372 (  1.6G)  Linux swap
/dev/hda6              Apple_Void                            0 @ 0         (  0.0k)  Unknown
/dev/hda7         Apple_Bootstrap boot                   16001 @ 64        (  7.8M)  NewWorld bootblock

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0
```

This is the contents of my /etc/yaboot.conf file. Note the line containing: macosx=/dev/hda3

```
boot=/dev/hda7
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash video=ofonly"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="nosplash video=ofonly"
```

Could you please post the contents of your /etc/yaboot.conf so we can take a look at it? This file is on your Linux partition, not your Mac partition.

It's a valid assumption that your data is still intact on your Mac partition. Now we need to determine whether that partition can be booted.

Thanks.

---

### Post by JustAboutRealJAR on 2008-01-31
I've tried setting hda1, hda2, and hda3 as the osx boot partition, none worked (following each change with: "sudo /usr/sbin/ybin -v")

anyway here's my yaboot.conf... hope it helps:
```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3
brokenosx

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

```

I also added brokenosx in there, because I read you need it if you have OSX on an HFS+ partition. but it didn't change anything

Thanks so much for the help and support guys :)

---

### Post by JustAboutRealJAR on 2008-02-01
I just popped in the OSX installer DVD and it doesn't see ANY of the partitions... I thought that was interesting and possibly useful...

also... what happens if I simply toggle the boot flag to bootable on the OSX partition (hda3) ?

can you have more than one bootable partition?

---

### Post by JustAboutRealJAR on 2008-02-01
update: while fdisk can see the partitions... neither libparted (gparted, or qtparted), or mac osx disk utility can read the partition table... what is going on?

OSX disk utility (on the installer DVD) shows an empty partition table

QtParted returns the following error when you select hda
```
Critical error during ped_disk_new!
```

It offers only an 'ok' button with that error...

---

### Post by BladeMelbourne on 2008-02-01
I haven't had to use brokenosx.

```
brokenosx
    This option causes the menu entry for MacOSX to execute \System\Library\CoreServices\BootX from the macosx=device instead of the usual \\:tbxi. This is necessary if OSX is installed onto an HFS+ filesystem instead of UFS. When OSX is installed on an HFS+ filesystem MacOS will mount and debless the OSX partition. Add this option if the OSX menu entry breaks after booting MacOS. You should not use this option if OSX is installed on a UFS filesystem, for UFS installs you specify the OSX bootstrap partition which is protected against MacOS. This option requires macosx= to be set.
```

I can see two possible tests for you to try (if you're up for it):
1) Remove brokenosx and ensure macosx=open-firmware-path, or
2) Set brokenosx and remove the macosx line.

Can I ask what order you installed OS X and *buntu? For myself it was:
* Mac OS X 10.4
* Xubuntu 7.10
During this process my whole disk was wiped as I had backed up to external disk.

I assume you installed Kubuntu afresh on your system - there was no previous version of Linux anywhere?

I'm getting a little stumped for ideas - I haven't had yaboot problems before.

If it comes down to it, there may be one choice left:
1) Backup your files that are on your Linux partition to an external source (network, USB2 disk, etc).
2) Backup your files on your Mac partition to an external source.
3) Wipe disk and start again.

It may be tricky to do #2 - mounting and having full read access to your Mac files from Linux can be problematic. We can get you running MacOnLinux - so you can boot OS X in a Kubuntu Window whilst running Linux. This would need to be compiled - as MoL in the repositories is a little old.

---

### Post by JustAboutRealJAR on 2008-02-01
I've tried removing the brokenosx line several times and setting the macosx line to hda1, 2, and 3 (all the mac type partitions. also, I checked the yaboot.conf docs and it says brokenosx requires you to have an 'macosx=' line

as for backing up the files on my osx partition... that's no problem, I can mount/ access it fine... I don't know that it's necessarily a yaboot problem... I think it might be that I somehow messed up the boot process of OSX.

btw... the order of the installations was First OSX, and I intentionally left space on the drive for linux. once I had osx up and running (for several months of normal use) I decided to finally get linux running on this sucker... So I downloaded the Kubuntu alternate installer and everything went great: now I'm typing on this forum from kubuntu ;)

I really just don't feel like hunting down all the install cds/serial numbers/etc/etc/etc/etc for my osx software it'd be a whole weekend just to get everything reinstalled

I'm really stumped... I'm gonna try using macos= instead of macosx and see if that works

---

### Post by JustAboutRealJAR on 2008-02-04
ok no dice... I'm gonna throw in the towel and start over again *begins backing up files*

maybe I'll use Xubuntu this time since kubuntu is a bit slow on this nearly 3 year old machine

---

### Post by justin whitaker on 2008-02-04
Nevermind.

---

### Post by JustAboutRealJAR on 2008-02-05
reinstalled osx, then ubuntu... worked this time... weird

---

