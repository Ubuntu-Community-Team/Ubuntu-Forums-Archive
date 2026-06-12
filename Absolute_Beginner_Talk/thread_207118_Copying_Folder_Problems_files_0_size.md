---
title: "Copying Folder Problems: files 0 size"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by TimJ on 2006-07-01
I've searched around and can't find a thread with this problem. Apologies if it's known and thanks if anyone can point me toward a known solution.

I need to copy a documents folder, which has subfolders in it. I try copying and past in folder to both an external hard drive and, separately, a memory stick. In both cases the folders seem to copy over. If I immediately check them then all the folder structure is there and all the files, at their correct size. However, once I turn off the external hard drive or remove the memory stick, and then reaccess, all my files are at 0kb. I need to be able to transfer the files to work so the hard drive and memory stick are formatted under MS-XP.

Any ideas what I'm doing wrong in copying?

---

### Post by jorn on 2006-07-01
What filesystems are we talking about?
You can't copy files between ntfs(winxp) and Ubuntu(mostly ext3)

---

### Post by T700 on 2006-07-01
Windows XP generally formats drives with a file system called NTSF.  Because Microsoft has refused to release the specifications to NTSF, there is no good way for Linux to write information to it, although information can be read and copied with no trouble.  There are some projects in the early stages to allow Linux to write to this kind of file system but they are in beta (testing) and should not be used for valuable data.  If you need to be able to read/write in both Linux and Windows, you should use FAT32 for the file system.

The solution is to use a graphical application such at gparted to reformat the drives.  Remember when using gpart to start with the command gksudo rather than sudo, since it is a graphical application.  You can even partion and format part of the drive for native Linux file systems and part for FAT32.  

Good luck,
Paul

---

### Post by TimJ on 2006-07-04
Thanks for the replies and sorry I didn't provide enough info first time around. The memory stick has always been formatted in Fat32 and it was transferring from Ext3 to Fat32 which was causing the problems. I'll give it another format and see what happens.

---

