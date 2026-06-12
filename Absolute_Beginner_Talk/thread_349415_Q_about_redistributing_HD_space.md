---
title: "Q about redistributing HD space"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Beamvr6 on 2007-01-30
When I started using Ubuntu a few months ago it was installed as a dual boot next to XP. Although the ultimate goal was to get rid of XP completely I decided to maintain an XP install because it is much better playing games despite a lot of efforts with Cedega. For all other purposes Ubuntu (6.0.6) is hear to stay. :D 

With the now limited use of XP a lot of potential disc space is available for Ubuntu and I am looking for the best way to do so.

HW situation:
- 1 physical SATA HD 250GB with 2 NTFS partitions for XP (sda1 and sda5 in Ubuntu)
- 1 physical EIDE HD 80GB with ext3 partitions for Ubuntu

I plan to use most space on sda5 for Ubuntu but not all. My ideal would be if that space on sda5 is directly available for my Home Folder.

I made a plan for it but like to verify if it makes sense and leads to the desired situation:
- Free up required space on sda5 (thru XP of course)
- Reboot using a bootable CD-Rom running partition magic.
- Reduce sda5 in size
- Create a new ext3 partition
- Merge that partition with the ext3 partition containing Home Folder (so that partition is on 2 physical HDs).
- Reboot to Ubuntu and bingo.

Is it this straightforward, do I need to be more? Is it possible at all? I also haven't tested yet if partitions on 2 HDs can be merged, if not are there other means to have it under the roof of the Home Folder?

TIA

---

### Post by Rinzwind on 2007-01-30
If you can resize XP from within XP all you need to do is to put it into a non-formatted partituon. 

From within Ubuntu all you need is Gparted. 

I don't think that these steps:
> - Reboot using a bootable CD-Rom running partition magic.
- Reduce sda5 in size
- Create a new ext3 partition
- Merge that partition with the ext3 partition containing Home Folder (so that partition is on 2 physical HDs).
- Reboot to Ubuntu and bingo.

need to be done from outside of Ubuntu.

---

### Post by Beamvr6 on 2007-01-30
Thnx Rinzwind, going to try it that way.

---

### Post by Beamvr6 on 2007-01-30
K, the plan changed a little as for some reason I could not get Gparted to resize the NTFS. I could however in XP. Then used Gparted to create an ext3 partition on the unallocated space. 

Disks Manager now reports the partition as follows:
- Device: /dev/sda6
- Filesystem: Extended 3
- Access path: none
- Size: 81.45 GiB (Free space not available)
- Status: Inaccessable

There is a Format option, Change access path option, Enable option.

I feel unsure how to proceed from here, advice appreciated / needed.

---

### Post by Beamvr6 on 2007-01-31
Seems to be resolved now.

Last steps after creating the new ext3:
- make a new folder data in folder username
- edit fstab (add a line like "/dev/sda6 	/home/username/data	ext3	defaults	 0 1")
- give permissions ("sudo chown -R username:username /home/username/data" followed by "sudo chmod -R 755 /home/username/data"

Another thing learned in the wonderful world of Linux. :)

---

### Post by erissiva on 2007-01-31
I am having a similar problem. I no longer have a use for XP on my hard drive. I have deleted the XP partition, formatted in Ext3 format and resized my Xubuntu install partition to fill the entire drive (other than swap, etc., of course).
However, when I run Xubuntu it only recognizes the original amount of space instead of the entire amount. When I try to use QTparted to view anything on the drive (using sudo qtparted), it gives me the error:
```
Critical error during ped_disk_new
```

I don't really know what to do. How would I get it so that the OS recognizes the partition as filling the whole drive? I'm pretty new to linux, not to computers in general, and I'm starting to get used to the terminal - but I'm totally stumped.

Edit: Oh, and the terminal is giving me the error
```
Error: Can't have overlapping partitions.
``` when I try to do anything in QTparted.

---

### Post by Beamvr6 on 2007-01-31
> I have deleted the XP partition, formatted in Ext3 format and resized my Xubuntu install partition to fill the entire drive

So you created a new Ext3 partition AND resized an existing partition over it? That could explain the overlap issue. Best use a partition manager again and solve the overlap situation.

---

### Post by erissiva on 2007-01-31
Well, I noticed my mistake after having immediately created the partition. So, I had deleted the partition before resizing the Kubuntu main partition (/dev/hda2). So - originally there would have been overlap, but I thought I fixed that the first time.
I'll try using the partition manager again to see if I can't fix it. That's for pointing that out.

---

