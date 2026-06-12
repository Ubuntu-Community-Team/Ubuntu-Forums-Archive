---
title: "Ext2 vs. Ext3 vs. NTFS formatting size?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by MetalMusicAddict on 2005-12-04
In my experimenting with converting my server from XP to Ubuntu I am playing around with [Ext2 IFS]("http://www.fs-driver.org/"). A driver for windows that will let you use ext2/3 formatted drives in windows.

I have a 80gig NTFS drive that when formatted I have about 74gigs of space. Now formatted as a ext3 drive I have 70gigs free space. 

So Im wondering does the journaling feature of ext3 take up more space than ext2 does in writing the allocation table? I want to use ext2/3 but loosing about 4 gigs is a little painful. :)

I was thinking about [ReiserDriver]("http://rfsd.sourceforge.net/") if I went with ReiserFS but it only gives read access.

---

### Post by MetalMusicAddict on 2005-12-04
Bump?

---

### Post by MetalMusicAddict on 2005-12-05
Last one and Ill call it quits.

---

### Post by az on 2005-12-05
It would be intersting to see the difference between ext2 and ext3.  I do not think the journaling consumes that much.  

I know the creation of the filesystem allocates about 5 percent for reserved-blocks (superuser deamons) to be able to continue to write to the filesystem after non-root processes have consumed the disk.

What esle is there?  Inodes and other filesystem data?

---

### Post by MetalMusicAddict on 2005-12-05
[QUOTE=azz]It would be intersting to see the difference between ext2 and ext3.  I do not think the journaling consumes that much.[/QUOTE]
The only way I could figure would to format the drive again. Do I really need journaling? I know the win side doesnt care but is it really an asset to a home linux server?

BTW -[Ext2 IFS]("http://www.fs-driver.org/") works great. Ive had no problems *using* the drive. If you must use a ext2/3 drive in windows I recommend it.

---

### Post by Adrian on 2005-12-05
I had the same "problem" when I was about to format my 160Gb drive. I ended up formatting the drive twice to compare them both. Since the difference in available diskspace was negligible (I don't remember the exact numbers though), I went with ext3.

That driver really rocks. I find it a little surprising that it's not used by more people.

---

### Post by MetalMusicAddict on 2005-12-05
[QUOTE=Adrian]I had the same "problem" when I was about to format my 160Gb drive.[/QUOTE]
So on a 160Gb drive how much free space did you have after formatting? I have several large drives I have still to format.

I used PartitionMagic to do the formatting. I dont think it would matter but I wonder if I used qparted to format would it be different?

---

### Post by Adrian on 2005-12-05
[QUOTE=MetalMusicAddict]So on a 160Gb drive how much free space did you have after formatting? I have several large drives I have still to format.

I used PartitionMagic to do the formatting. I dont think it would matter but I wonder if I used qparted to format would it be different?[/QUOTE]

Sadly, I don't remember this exactly, but I think it was a couple of gigabytes. Thinking about it, the drive was originally NTFS formatted, and I actually noted that a lot of space was occupied even though the disk was empty. "Lousy system!", I thought to my self and ext3 formatted it instead. Unfortunately, ext3 consumed more space than NTFS did, but not very much really. Maybe one gig more? Something like that. That's why I have forgotten, I guess, since I understood that the waste of diskspace probably was impossible to avoid. However, I formatted it to ext2 to check the difference so I guess I was a little concerned (or just curious :) ) after all.

If I remember things correctly, I used the Ubuntu installer to format the drive since I upgraded to Breezy at the same time. I actually specified that I wanted to reserve 0% (instead of the default 5%) of the blocks, since I was going to read a lot more from the disk than I was going to write to it anyway (hence minimizing the need of emergeny handling), and because you can change that later using the tune2fs command.

The alternative, FAT32, will probably give you more available diskspace as long as the disk contains no data, but after a couple of files, it will rapidly fill the disks with unusable empty blocks due to internal fragmentation. To use the disk efficiently with FAT32, I suppose it's best to divide the disk into 5 small partitions and who wants to do that? :)

---

### Post by MetalMusicAddict on 2005-12-05
FAT is a no go because I wouldnt be able to store larger than 4 gig files on it. :)

I think I format it with qparted to see if theres a difference from PartitionMagic. Shouldnt be but who knows?

---

