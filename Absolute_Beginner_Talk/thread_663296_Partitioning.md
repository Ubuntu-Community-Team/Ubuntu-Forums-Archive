---
title: "Partitioning"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2008-01-10
I plan on getting a new hard drive, and I'm trying to figure out how I should set up the partitions on my computer. In general I would like to set it up like this:

Windows XP (NTFS)
Windows Vista (NTFS)
Ubuntu (EXT3)
Data (?)
Swap (Swap)

The data partition would contain all my documents/music/videos as well as games. Basically all the big space eaters.

Now, the problem is, I don't know how to set up that partition. I was going to do NTFS and mount it as /home, but apparently that  can't be done due to permissions issues. I'm reluctant to use EXT3 or FAT because of performance (for the games). The only way I think could work is format it NTFS, move "My Documents" there under Windows XP, and then create a bunch of links in my ubuntu home folder for Documents, Music, etc... but that seems like a huge mess.

Any ideas?

---

### Post by mdpalow on 2008-01-10
Edit your post with how large the hard drive will be and how much space you think you might want to use for Windows/Vista/Ubuntu/Data and it'll be a lot easier to give you a good answer. 

Just throwing this out there... I would look to give Ubuntu _at least_ 20 gigs. Swap Drive could be 1-2 gigs, but no more.

Why not create one symbolic link from Ubuntu to the NTFS folder that holds your docs, movies, music. All of those file types will be fine between the two systems. If you make it EXT3 Windows won't be able to read/write to it. Although that makes me think if I read somewhere something about some add-on for Windows that now will let it see EXT3. Can't remember for sure. However, you're right about the permissions thing with NTFS and that could be problematic later..

I think if you buy a good size HD (no less than 320 and preferrably 500gigs), you'll have plenty of room for all three OS's, movies, games, docs, music, etc... and it'll make it easier to decide how you want to set it all up.

Don't know what you mean about using EXT3 for games. Probably not a good idea since Linux isn't great for most games.

Good luck...

---

### Post by ubutufan on 2008-01-10
Since this is going to be a multiboot system, I recommend that you save space for one more partition. This should be Page File for windows, on the likes of swap in ubuntu. Thus your windows partitions will not need to be defragmented every now and then

---

### Post by mrphud on 2008-01-10
when I created my dual boot I gave ubuntu 30 gigs. I left my secondary drive to handle all of my documents (which is nfts by the way). the swap needs to be like 512 megs or so. the boot should be about 50 megs the rest for the '/' install. This can be done from live cd installation

---

### Post by thelatinist on 2008-01-10
> **Raptor45 said:**
> I plan on getting a new hard drive, and I'm trying to figure out how I should set up the partitions on my computer. In general I would like to set it up like this:

Windows XP (NTFS)
Windows Vista (NTFS)
Ubuntu (EXT3)
Data (?)
Swap (Swap)

The data partition would contain all my documents/music/videos as well as games. Basically all the big space eaters.

Now, the problem is, I don't know how to set up that partition. I was going to do NTFS and mount it as /home, but apparently that  can't be done due to permissions issues. I'm reluctant to use EXT3 or FAT because of performance (for the games). The only way I think could work is format it NTFS, move "My Documents" there under Windows XP, and then create a bunch of links in my ubuntu home folder for Documents, Music, etc... but that seems like a huge mess.

Any ideas?

You don't have to save your documents in your home folder  In fact, I think it's better not to...then you don't have to worry about your data if you have to reinstall Linux.  I deleted the Documents, Music and Videos folders from my home directory and I just save everything on an NTFS partition mounted as Files.  I then set My Documents in Windows to point to that partition and changed the links in the places menu to reflect the new locations.

I recommend you put your swap at the end, your ubuntu ext3 partition right before it, and the shared data partition between your Ubuntu ext3 and your Vista NTFS.

Your drive would look like this:

```
First Partition: NTFS  (WinXP)
Second Partition: NTFS (Vista)
Third Partition: FAT 32 / NTFS / EXT3 (Shared Data)
Fourth Partition: EXTENDED
  Fifth Partition: EXT3 (Ubuntu)
  Sixth Partition: Solaris / Linux Swap
```

The size of each of these partitions will depend of course on what you want to do with with each OS and how many and what size programs you will install.  My Ubuntu partition with all installed apps is just over 3 GB, so you don't need a huge Ubuntu partition, especially if you will be keeping your documents on a separate drive.

It really doesn't matter what format you use for your shared data partition.  You can use ntfs-3g to mount an NTFS partition in Ubuntu, Ext2IFS to mount an ext3 in Windows, or you can use FAT32 natively in either.  Just be aware of the limitations of FAT32 (Especially the 4 GB file size limit, which can easily be exceeded by video editing software, etc.).

---

### Post by Raptor45 on 2008-01-10
Sizing isn't the issue, I can work that out.

I'm just not sure how to go about organizing my documents so they can be easily viewed between operating systems. Like "My Music" in windows is the same as "Music" in Ubuntu.

I think I'm just going to have to end up making a bunch of symlinks to sort it out.

---

### Post by thelatinist on 2008-01-10
> **Raptor45 said:**
> Sizing isn't the issue, I can work that out.

I'm just not sure how to go about organizing my documents so they can be easily viewed between operating systems. Like "My Music" in windows is the same as "Music" in Ubuntu.

I think I'm just going to have to end up making a bunch of symlinks to sort it out.

I'm not sure what your concern is.  If you mount the partition in both operating systems, it should be easy enough to get to any data.  If you are concerned about Save As... in Windows, set your My Documents folder to the root of that drive. There are all kinds of tutorials for that.  If you're worried about the links in your Places menu, then all you have to do is open Nautilus and change those bookmarks (in the "Bookmarks" menu of Nautilus) to point to the folders you want.

---

### Post by Raptor45 on 2008-01-10
> **thelatinist said:**
> I'm not sure what your concern is.  If you mount the partition in both operating systems, it should be easy enough to get to any data.  If you are concerned about Save As... in Windows, set your My Documents folder to the root of that drive. There are all kinds of tutorials for that.  If you're worried about the links in your Places menu, then all you have to do is open Nautilus and change those bookmarks (in the "Bookmarks" menu of Nautilus) to point to the folders you want.

I think thats what I'm going to end up doing.

---

