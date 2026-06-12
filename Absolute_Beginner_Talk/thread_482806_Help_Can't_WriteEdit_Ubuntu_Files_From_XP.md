---
title: "Help: Can't Write/Edit Ubuntu Files From XP"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by apolloxi on 2007-06-24
I used the "EXT2 FS" program to make my XP files accessible to Ubuntu and "share" between the two partitions. All the files are only "read-only" on Ubuntu, though.

Does anyone have any idea how I can enable write access to these files on Ubuntu?

---

### Post by 5-HT on 2007-06-24
ext2fs will provide ext2 (and ext3 just without the journal) support for XP, it will not give Ubuntu any support for NTFS.
What filesystem are you using in windows? Ubuntu already has native vfat support, and read-only NTFS support.  If you want to allow read/write ability for NTFS you'll need to check out something like [ntfs-3g.]("http://www.ntfs-3g.org/")

Warning: Mircosoft have never released the specs for NTFS! While ntfs-3g is a great project and has reached stable status, data corruption is still possible.

---

### Post by freebird54 on 2007-06-24
Here is a link to one way to do it..

[http://www.fs-driver.org/](http://www.fs-driver.org/)

This provides you with a way to read/write ext2 (or 3) data directly from Windows using an Installable File System interface.

Personally I run the other way around (r/w from linux on Win drives) - but flexibility is a wonderful thing.... :)

---

### Post by apolloxi on 2007-06-24
I downloaded and installed NTFS-3G, and I checked "Enable write support for internal/external device." And, when I click on "Properties" for the files in question, the "access" of the owner "Root" (which I am apparently now, since it still says I am not the owner) now says "Read and write" but I still can't write. I open the files and they still say "Read only" and I am still unable to write in them.

Windows partition is NTFS, obviously.

Is there an additional step I should've done, or a step that I missed?

---

### Post by apolloxi on 2007-06-24
Can someone help me, please? (Read previous post.)

---

### Post by logos34 on 2007-06-24
It might take a reboot before the changes to fstab take effect and your ntfs partitions actually mount correctly using fuse driver.

---

### Post by Nikron on 2007-06-24
> **apolloxi said:**
> Can someone help me, please? (Read previous post.)

You aren't the owner.  Root is the super user.  You need to change root to your name.

---

### Post by apolloxi on 2007-06-24
How do I do this?

I looked up the "chown" command but the Terminal isn't being responsive to the apostrophe that I used in naming the folder I'm trying to get. It completely ignores it.

For example, the folder is named "Sean's Stuff", which is located in "/" but, whenever I do a command, such as "ls /Sean's Stuff" it says "ls /Seans Stuff: No file or directory exists", and it treats like "Seans" and "Stuff" were two separate things, instead of one name.

---

### Post by freebird54 on 2007-06-24
If you have spaces or other special characters in your filenames, the easiest way to refer to them is with double quotes around them.  So -  **"Sean's Stuff"** should work.  This is the same as it is in Windows, if you happen to be working from the command prompt.

There are other ways - but that should get you going for now!

BTW - you have me somewhat confused.  Are you trying to read/write Windows files from  inside Ubuntu - or are you read/writing Ubuntu files from Windows?  Both can be done - but there are different details involved!

---

### Post by apolloxi on 2007-06-24
I am trying to read/write files that were originally on XP inside of Ubuntu. Currently, the files are in my Ubuntu drive (which I gave the letter "G" to), but they were originally on XP. I used the EXT2 IFS program to move them to the G Drive.

And, I made some progress, I think. To make it less confusing for myself, since I didn't know about the double quotations trick, I went back to XP and renamed the folder "SAM" (my initials). Then, I went to Ubuntu and did the "sudo chown sean /SAM" command, which successfully gave me ownership of the folder. But, for some reason, it won't apply to all of the contents inside, even when I went to "Properties" and clicked "Apply permissions to enclosed files." Everything within the folder still belongs to "root", and is still read-only.

Is there a way to change the ownership for EVERYthing inside?

---

### Post by logos34 on 2007-06-24
> Is there a way to change the ownership for EVERYthing inside?

**chown -R**

---

### Post by apolloxi on 2007-06-24
Okay. I discovered the "-R" operand. Almost everything in the folder belongs to me but two folders (which, ironically, are the most important folders   x_X). They're called "- Portfolio" and "- Portfolio 2". They're being resistant for some reason. Even when I try to directly change their ownership by doing "sudo chown -R sean /SAM/"- Portfolio", it acts like it succeeded but, in reality, nothing changes.

Why are these two beloved folders rejecting their rightful owner?   ;_;

---

### Post by apolloxi on 2007-06-24
Whoops. Ignore that last post, everyone. EVERYTHING in the folder now belongs to me. I guess I needed to reload the screen for changes to be visible.

Problem solved.

Thanks for all the help, everyone.   ^_^

---

