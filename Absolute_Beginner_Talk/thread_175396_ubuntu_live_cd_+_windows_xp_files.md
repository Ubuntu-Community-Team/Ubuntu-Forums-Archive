---
title: "ubuntu live cd + windows xp files"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by hypertonic on 2006-05-13
hey,

i just discovered ubuntu, but, just to be safe, i like to start of easy with the live-cd.

the problem is that I would like to try out al kinds of things in ubuntu, like the mediaplayer, the office-suite and so on. The only problem is that, with most of these tries, I should have some files from my My Documents folder in Windows xp, and those files, I cant find anywhere in the filebrowser of ubuntu.

Anybody knows where i can find them?

thanks,
hype

---

### Post by Kvark on 2006-05-13
1. Make a folder in your linux home directory, call it "windows", "c" or something.
2. Open the disk manager, it's in the menus at "System -> Administration -> Disks".
3. Select your hard disk in the Storage List.
4. Under the partitions tab choose your Windows partition. You should recognize it on that it's filesystem is ntfs.
5. Click the "change" button next to the "access path" field and choose the folder you created in step 1.
6. Click the "activate" button and then you'll find your Windows files are in that folder.

When you have installed Ubuntu you'll want to add a line to a file called /etc/fstab to make it mount your windows partition automatically each time you boot Ubuntu. But thats another story and I'm sure there is a howto for that somewhere on these forums.

---

