---
title: "Per-Directory RAID1 software solution?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-01
Having just moved away from XP, the only thing I'm still missing is the equivalent of MirrorFolders which is a software implementation of RAID1 (more or less) that allows you to mirror specific files and directories to another location in real time.  Is there a Linux/Ubuntu equivalent of this?

Thanks,

-Doc

---

### Post by kidders on 2007-06-02
Hi there,

That all depends on what you mean by "more or less" RAID 1, and what the other location is. I often store things on RAID arrays and symlink them to their original locations ... Imagine **ln -s /mnt/raid_array/databases /var/lib/mysql**, for example.

Provided your other location is in the same general area of a network, you could use ATA over Ethernet (with RAID 1 on top) to create what would effectively amount to a real-time mirror. (AoE packets are not routable afaik.) This would, of course, be predicated on having adequate backup power.

Is that anything like what you're after?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Doc.Caliban on 2007-06-02
It sounds like it.

I'm mirroring to an external drive and want to be able to select individual directories (recursive) to be mirrored in real time to a directory on the external drive.

Would that solution work in my case?

---

### Post by kidders on 2007-06-02
Not exactly. You'd be mirroring an entire filesystem (that would just happen to contain the directories you were interested in). Since you'd only be involving one PC, all you would need is a small RAID 1 array.

Can I ask what the purpose would be?

---

### Post by Doc.Caliban on 2007-06-02
It's always been my backup scheme.  Everything that is important to me was mirrored in real time to an external drive.  When I got to work, the drive goes into an empty box of pancake mix on the shelf in the kitchen.  If someone breaks in and lifts my laptop, I don't lose any of my data.

-Doc

---

