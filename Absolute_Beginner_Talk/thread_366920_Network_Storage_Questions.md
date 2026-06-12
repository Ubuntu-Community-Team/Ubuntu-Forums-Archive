---
title: "Network Storage Questions"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by GTBee on 2007-02-21
I am interested in adding Ubuntu which will give me a Ubuntu and Win XP Pro (may also add Mac) home network.  I would like to add some type of Network Storage or hard drive for backing up my computers and also for central storage of my music and DVD movies.  It appears that the Western Digital and Seagate network storage products do not support Linux.  LaCie's network drive supports all 3 OS, but uses FAT32 format.  FAT32 doesn't support movies.

1) any recommendations for Network storage device/product?  I could set up a file server but like the simplicity and ease of use of the NAS hard drive.

2) LaCie says that with their browser configuration I can reformat the drive to ext3.  How does ext3 perform (I am not highly technical, but get by) and are there any issues accessing this drive from a WinXP or Mac?  (I assume/believe ext 3 will support the large file sizes)

3) LaCie says their large drive will support XFS- is there a better format I should use for my needs?

Any other concerns or recommendations I should consider?

Thank you for your help- GTBee

---

### Post by Jussi Kukkonen on 2007-02-21
Actually using any network storage device should be possible from any OS that supports the file sharing protocol (SMB mostly, some devices also do NFS), regardless of what they "support". If the manufacturer is stupid enough the administration might be windows-only, but the ones I've seen have been web-based...

The FAT32-reliance may indeed be a problem if you intend to store large files -- 2GB is the limit IIRC. ext3 should do fine (I use it myself for my digital TV recordings), and as long as you are accessing the files through the SMB share the actual filesystem doesn't matter to any 'client' OS. Of course, if at some point you want to attach the disk straight to your Windows-machine, you'll have to install 3rd party ext-support...

---

### Post by l951b951 on 2007-02-21
We have a(n) HP Media Vault at my home.  It supports NFS for linux and also supports windows shares.  It comes with a ghost program for your windows machines, and I use rsync to back up my files on my linux machines.  It worked out of the box, and there is plenty of web documentation for finding How-Tos to set up NFS and mount the drives at boot.  It has 512 gigs out of the box, expandable to 1.2 TB.

---

