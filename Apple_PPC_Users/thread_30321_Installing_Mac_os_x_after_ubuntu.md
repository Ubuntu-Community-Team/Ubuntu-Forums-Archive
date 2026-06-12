---
title: "Installing Mac os x after ubuntu"
date: 2005-04-28
forum: Apple PPC Users
---

### Post by prio on 2005-04-28
I have a powerbook with ubuntu and mac os x. 
I want to clear my mac os x partition, resize it and reinstall mac os x and openbsd. I dont however want to have to reinstall ubuntu.
I am now too familiar with yaboot so I was wondering if someone could give me some advice. After I install Mac OS X what will I have to do to reinstall yaboot? 
And a bit OT for here, is it possible to boot OpenBSD using yaboot?
Thanks.

---

### Post by farruinn on 2005-04-28
[QUOTE=prio]I have a powerbook with ubuntu and mac os x. 
I want to clear my mac os x partition, resize it and reinstall mac os x and openbsd. I dont however want to have to reinstall ubuntu.
I am now too familiar with yaboot so I was wondering if someone could give me some advice. After I install Mac OS X what will I have to do to reinstall yaboot? 
And a bit OT for here, is it possible to boot OpenBSD using yaboot?
Thanks.[/QUOTE]

This will depend on your current partition map. Hopefully the yaboot partition comes [B]before[\B] your Mac OS X (soon to be OS X+OpenBSD) partitions because once you reinstall OS X your boot device will be set to the OS X partition.  Holding command+option+p+r at boot until you hear a third chime will reset to the first boot partition.  As for using yaboot for OpenBSD, I don't know how, but it looks like it's possible from a quick look at some google results.

---

### Post by gruepig on 2005-04-28
[QUOTE=prio] And a bit OT for here, is it possible to boot OpenBSD using yaboot?
Thanks.[/QUOTE]

Yes, yaboot will boot to OpenBSD's bootloader.  You need to add a line 'bsd=/dev/hdaX' (where hdaX is your OpenBSD partition) to your /etc/yaboot.conf file and then run 'mkofboot -b /dev/hdaY' (where hdaY is your boot partition).  You also need to copy the BSD bootloader (ofwboot) into /usr/local/lib/yaboot/.

For more details, see /usr/share/doc/yaboot/examples/yaboot.conf.multi-boot on your system and/or [http://www.abl.com/opt/sushidot/](http://www.abl.com/opt/sushidot/).

Note: You should also be able to boot OpenBSD directly from Open Firmware. Hold down apple-option-O-F at boot to enter Open Firmware and type (sometime like) 'boot hd:,ofwboot'.

---

### Post by prio on 2005-04-28
excellent. thanks. I cant remember my partition map off hand. Hopefully its first. I will check tonight.

---

### Post by prio on 2005-04-28
My partition table is as follows.
```
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map                           63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 101833792 (977.0k)  NewWorld bootblock
/dev/hda3               Apple_HFS Macintosh HD       101569984 @ 262208    ( 48.4G)  HFS
/dev/hda4         Apple_Bootstrap bootstrap               1600 @ 101832192 (800.0k)  NewWorld bootblock
/dev/hda5         Apple_UNIX_SVR2 untitled            14669922 @ 101835746 (  7.0G)  Linux native
/dev/hda6         Apple_UNIX_SVR2 swap                  704572 @ 116505668 (344.0M)  Linux swap
/dev/hda7              Apple_Free Extra                 262144 @ 64        (128.0M)  Free space

```
My yaboot.conf is as follows
```
boot=/dev/hda4
device=/pci@f4000000/ata-6@d/disk@0:
partition=5
root=/dev/hda5
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3
<snip>
```
I take it yaboot is on hda4? Is there anyway to reinstall yaboot after a mac os x install with a setup like above? Thanks.

---

### Post by gruepig on 2005-04-28
[QUOTE=prio]I take it yaboot is on hda4? Is there anyway to reinstall yaboot after a mac os x install with a setup like above? Thanks.[/QUOTE]

Yes, your yaboot is on hda4.  

You may have to reorder your partitions (that's 'r' from within fdisk) so that yaboot comes before OS X and then run mkofboot or ybin.  It's been awhile since I've done this, so you should check before you follow these instructions ... If you can't boot to Linux, you may be able to boot from firmware with 'boot hd:,yaboot' or 'boot hd:4,yaboot'.  If that doesn't work, you'll want to boot off a CD (Ubuntu, Knoppix, whatever), edit the partition table, mount /dev/hda4, chroot to /dev/hda4, and run mkofboot or ybin.

---

### Post by ssam on 2005-04-29
i am not sue if it would work in this case, but if you hold down [alt] at boot time you should get a list of bootable partitions.

---

