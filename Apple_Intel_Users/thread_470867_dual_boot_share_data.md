---
title: "dual boot share data"
date: 2007-06-11
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-11
i was wondering what opinions are there to share project data in dual boot situations.
i found this discussion that says you can mount ext3 on osx..
[http://forum.insanelymac.com/index.php?showtopic=34227](http://forum.insanelymac.com/index.php?showtopic=34227)

but i read a lot about right management problems. and running your data corrupt (i am scared). fat32 seems to be the save way.. well thats what i use for my memory sticks. but i am wondering if there aint better ways nowadays?

---

### Post by ronocdh on 2007-06-12
> **kzm. said:**
> i was wondering what opinions are there to share project data in dual boot situations.
i found this discussion that says you can mount ext3 on osx..
[http://forum.insanelymac.com/index.php?showtopic=34227](http://forum.insanelymac.com/index.php?showtopic=34227)

but i read a lot about right management problems. and running your data corrupt (i am scared). fat32 seems to be the save way.. well thats what i use for my memory sticks. but i am wondering if there aint better ways nowadays?
You could certainly create a FAT32 partition and use that as your media space for both OS X and Ubuntu. What I do personally is save everything to my OS X partition (HFS+, non-journaled) and mount that in Ubuntu. I've added it to my fstab so it mounts on boot. I did initially have permission problems, but this was solved by launching Nautilus as sudo and changing the permissions (be careful with this!). It is important to disable journaling in order for Ubuntu to read the OS X partition; I believe benanzo has posted previously about this.

However, I will say that every now and then I create a new document in OS X and I do not have permission to edit it in Ubuntu, and must regrant myself permissions, which can take a minute or two. I am already declaring permissions for directories recursively, but this does not seem to account for as-yet-uncreated files. If anyone can solve this, please reply!

I use [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") to mount my ext3 volume in OS X. Another option is MacFUSE, which, FWIW, I've heard isn't as stable on ext3, but grants many other cool possibilities.

---

### Post by kzm. on 2007-06-12
do you may be have the link about mounting your osx drive in ubuntu? if i can modify files this way, it would be fine with me.
about the permission problem.. a stupid question: would using the same user name in both os solve any thing? i guess the question is "no" and that even sounds obvious to me.

---

### Post by ronocdh on 2007-06-12
> **kzm. said:**
> do you may be have the link about mounting your osx drive in ubuntu? if i can modify files this way, it would be fine with me.
about the permission problem.. a stupid question: would using the same user name in both os solve any thing? i guess the question is "no" and that even sounds obvious to me.
Actually I have read that using the same username solves the problem of permissions. I personally am using the same username, and it didn't make filesharing effortless. Perhaps I wouldn't even be able to access the drive if the usernames were different, but I doubt this is the case.

To mount your OS X volume in Ubuntu, you'll need first to create a mount point for it: 
```
sudo mkdir /media/OSX
```
Then edit your fstab (although you'd be wise to make a backup, first):
```
sudo gedit /etc/fstab
```
Then add the following line to declare the mounting location of your OS X volume, which you just created:
```
/dev/sda2       /media/OSX           hfsplus user,rw 0 0
```
That's the location of the volume, the location of the mount, the filesystem, permissions, read/write permissions, then options. All clear? Good luck!

---

### Post by cevans on 2007-06-12
The permissions problems is due to the permissions being based on uid rather than user name. Looking at the ownership of your files on the OS X partition should give you the uid that OS X uses (apparently, OS X starts at 501, and most Linux distributions start at 1000). You can then change your uid on one of the systems.

Since I'm much more comfortable with Ubuntu, I changed my uid there rather than in OS X, though a change in OS X would be better. I'm not sure how to explain the process, but I simply changed the uid in /etc/passwd and ran sudo chown -R on my home directory.

---

### Post by Torajima on 2007-06-13
Another way to deal with permission problems on the Mac volume is to go back into OSX, choose the folder with the files you want to share, and choose File > Get Info.

Under Ownership & Permissions, look at details. Change access for Group and Others to read only (or read/write if you want to add files to the folder from Ubuntu). Now select "Apply to enclosed items".

I did this to my Picture folder, and now I can access all my wallpaper from Ubuntu.

---

