---
title: "Drive Mounting Question"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by herrdoktor330 on 2006-08-06
I'm having the most unusual problem. Maybe you all have some insight? Here's what I'm working with:

I have an nforce2 mobo with IGP, 1 80 GB HD running from the mobo's IDE, and 3 HDs running off of a PCI IDE expansion card.

The first problem I had was from the initial installation: When I installed Dapper Drake the first time, I received a grub error #17. I worked around this problem by disconnecting the IDE cables from the IDE riser card and reinstalled. This seemed to get me around the grub error. After the install was complete, I hooked the IDE cables back up and the "Disks Manager" recognised the HDs. One of the partitions was EXT3. the rest were NTFS. I would set up the mount information from that program. However the mounts would not be available after a reboot.

To further mess things up, I compiled the new 2.6.17.7 kernel. After the new kernel install, "Disks Manager" doesn't recognise the partition file systems anymore. I followed the directions from the following forum thread:

[http://www.ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17)

If anyone has a suggestion as how to fix this, I'd take the help.

---

### Post by OU812 on 2006-08-07
This may be too late, but try doing

```
sudo /sbin/fdisk -l
```

to list all partitions on all detected drives. This will give you clues as to how to add these partitions to your /etc/fstab. In fact, you may want to post that here to help expedite a solution. Thanks.

john

P.S. Try looking at this link to find out how to add windows partitions.

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

---

### Post by herrdoktor330 on 2006-08-07
Thank you much, my good man. But I just got done reinstalling from the CD.

For my personal enlightenment, do non-mounted internal drives not detect after a kernel compile? I thought that one of the options I picked for compilation might have caused the problem. You have to fogive, but I'm a severe linux noob. I'm still trying to make heads and tails of the file system and how things are organized.

Oh well... I'm up to about 8 separate reinstallations of Ubuntu on 2 computers. I'm getting better every time around.

As a note, I'll be back with you all about this one. I'm sure this fight isn't over.

---

