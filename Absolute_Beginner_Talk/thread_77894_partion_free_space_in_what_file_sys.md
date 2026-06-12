---
title: "partion free space in what file sys"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by ramdez on 2005-10-17
Hello All,  recently I began using Ubuntu on a storage hd that I have and run it off of /hda1  i have 4 total partitions on the drive, 1 being ubuntu, 2,3,4 being old FAT windows drive with some music, vids and files.  I have another partition, unused 'free space' at the end of this drive.  I cannot access it yet, assuming b/c it's unpartitioned and I cannot find a utility in ubuntu/gnome to do this.  I'm kinda scared to touch it w/ a console utility and I think I might just resort to win98-fdisk-fat file system and then mount it.  But now that I have this opportunity, would it be better to mount it in some linux file system instead of FAT? I do share these partitions via samba, would making it ext3 affect these windows users?

 Basically, what filesystem should I make this free space that would be best and still let my windows users access it.  Thanks.

---

### Post by Spoofhound on 2005-10-17
In general FAT is probably the simplest and most effective filesystem if you want to share files between linux and windows users. Its how I share files between my home pcs. For partitioning work I use gparted in Gnome, which can be installed via synaptic. Its pretty straightforward and works well (at least the once or twice I've had to use it)

---

