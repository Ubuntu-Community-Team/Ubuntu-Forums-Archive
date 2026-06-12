---
title: "GUI interface for permissions, volume labels, mounting?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Tsu Dho Nimh on 2007-12-19
I just installed two SATA drives, and upgraded the disk the system is on to a larger HD, so I have three freshly formatted (ext3) drives.


1 - ROOT owns them now. How do I make them usable for ordinary users?  Is there a GUI interface?

2 - Is there a GUI interface that will let me name them something besides disk, disk-1 and disk-2 ?

3 -  Is there a GUI interface that will let me set them to auto-mount whenever anyone logs in?

---

### Post by NateMan on 2007-12-19
I wouldn't use a gui to do those things. seems like just asking for trouble, and as far as I know there is no gui. check out the links about halfway down this thread:
[http://ubuntuforums.org/showthread.php?t=541873](http://ubuntuforums.org/showthread.php?t=541873)

very nice howto on changing around the filesystem.
Good Luck!

---

### Post by Tsu Dho Nimh on 2007-12-19
Thanks for trying, but those links all lead to the same incomprehensible pages I've already looked at. 

And when you type as badly as I do, pointy clicky interfaces prevent errors.

---

### Post by Niniel on 2007-12-19
Why do you want to name/label the drives?
My understanding is that you can just mount them to a directory, say your home directory, and it will then look as if you had a ton of space, without having to jump drives.

---

### Post by andechs on 2007-12-20
The to set the disks' permissions in a GUI you have to first login as root. This means first allowing the root to login in the GNOME login window. Then right click on the mounted disks, click on on properties, then click the permissions tab. For full permissions set your username as the owner, along with R/W, create and delete files. Restart and you should have access with other users. To rename, I would try changing the mount point information, but my intuition thinks it doesn't work. No clue how to help on the auto mount, I'm still fairly new to this.

---

