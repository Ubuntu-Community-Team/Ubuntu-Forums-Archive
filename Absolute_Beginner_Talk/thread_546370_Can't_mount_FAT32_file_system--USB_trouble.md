---
title: "Can't mount FAT32 file system--USB trouble"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by rshel on 2007-09-08
OK,

I was looking at the Properties (right-click) of a flash drive mounted on my desktop; under the tab Volume, there is a button "Settings." Stupidly, I clicked on it and changed the filesystem to Fat32 (don't ask why, trying to fix minor related problem that I have now forgotten--stupid, as I said). Anyway, now Ubuntu will not mount the flashdrive at all. I get a message saying that Ubuntu cannot mount it because it is a FAT32 FS, which my system cannot use. Of course, I have other flash drives that are fat32 and mount fine. I have access via samba to various fat32 network shares. They mount fine. I can see the problem flashdrive in fdisk, which shows that it is fat16, and in gparted; gparted will not allow me to format it to anything, giving me an error that it cannot perform the task. I formatted the flashdrive as a ntfs on a windows machine, but ubuntu still sees it as fat32 when I try to mount it.  

I have tried modifying fstab to give me permission, etc. Same problem. I seem to have set some FAT32 bit on and now cannot turn it off.

Of course, since the flashdrive won't mount, I cannot return to the properties/Volume tab and reset the settings. 

Any ideas what I have done here? Or how to resolve it?

---

### Post by alan_daniel on 2007-09-08
I'm not much of an expert on file systems in general, but it sounds to me like in the conversion you may have corrupted some of the data on the disk. Can you somehow see any of the data on the disk to know that it's still intact (whether it's with fdisk, windoze, etc)?

---

