---
title: "want to access my floppy drive just like on Windows OS"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-24
Hello,
I would like to have the ease of Windows OS when it comes to accessing my floppy drive/disk. 

This means:

1) when I put in the little disk into my drive, I could check out the contents just by going to a file manager (e.g. Thunar on Xubuntu). 


2) I could directly save a file from a program such as Gimp onto the floppy disk.

3) I could put in my disk and remove the disk anytime I like (excepting when stuff is being saved to disk, of course), without having to do anything special

I don't want to have to mess around with terminal and a bunch of commands and sudo commands. No "cp blahblah" or  fstab stuff or anything else. 

How do I achieve these goals?

---

### Post by mssever on 2006-08-24
I think that KDE automates this a bit, though I don't use KDE or floppies so I don't know for sure.

---

### Post by keith whitehouse on 2006-08-25
hi hanzj

on the top menu click places, then computer and the double click the floppy drive icon. When the floppy has loaded you will have the icon for it on your desktop. Drag and drop any files you want onto it and when you are finished, right click the icon and select the bottom option "unmount volume" this will force it to write any data to it.

best regards keith

---

### Post by bodhi.zazen on 2006-08-25
> **hanzj said:**
> Hello,
I would like to have the ease of Windows OS when it comes to accessing my floppy drive/disk. 

This means:

1) when I put in the little disk into my drive, I could check out the contents just by going to a file manager (e.g. Thunar on Xubuntu). 


2) I could directly save a file from a program such as Gimp onto the floppy disk.

3) I could put in my disk and remove the disk anytime I like (excepting when stuff is being saved to disk, of course), without having to do anything special

I don't want to have to mess around with terminal and a bunch of commands and sudo commands. No "cp blahblah" or  fstab stuff or anything else. 

How do I achieve these goals?

The only way I know how is to edit fstab. I know this is frustrating, but it not that hard.


```
/dev/fd0  /media/floppy  auto auto,user,rw,sync 0 0
```

---

### Post by hanzj on 2006-08-25
bodhi, i think i have edited fstab just as you said, but when I try to save a file directly from an application. it won't allow me.

---

### Post by bodhi.zazen on 2006-08-25
> **hanzj said:**
> bodhi, i think i have edited fstab just as you said, but when I try to save a file directly from an application. it won't allow me.

I am afraid this is a "partial fix" and the best I can do. The limitation is that you must still mount and unmount the floppy. This can be done from Thunar. Once the floppy is mounted you should be able to write to the floppy.

What this "fix" has done:

1. You should be able to mount and unmount yor floppy, as read-write, as a user, from the GUI (Thunar), without sudo or the use of a terminal.

2. The sync option makes it such that data is written to the floppy as soon as you hit the "save" button from your application. If you eject the floppy without unmounting you will not loose data.

3. You should now be able to avoid the terminal/command line altogether to accomplish your tasks.

The only thing I do not know how to fix is the need to mount and unmount the floppy manually (which, as above, you should now be able to do without using the command line).

I am sorry I do not know how to make Linux auto mount a flopyy when you insert a disk or auto unmount when you eject it.

I assume when you could not save a file directly from an application it is because the floppy is not mounted. You should be fine if you mount the floppy via Thunar first, then save from gimp.

The only other thought I had is after you edited fstab you should unmount the flopy (as root) and re-mount the floppy as your normal user.

If this is not working as described, please give me a little more details and I will try to help you further.

I am sorry this is not exactly as Windows, but it is the best I can do for you.

Perhaps someone who is more knowledgeable then me can help ?

---

### Post by fluffnik on 2006-08-26
> **hanzj said:**
> bodhi, i think i have edited fstab just as you said, but when I try to save a file directly from an application. it won't allow me.

FAT formatted floppys?

As FAT has no concept of ownership they are mounted as if belonging to root by default.

Try:

```
/dev/fd0  /media/floppy  auto auto,user,rw,sync,gid=25,umask=003 0 0
```

...which will mount the floppy as belonging to the group "floppy", gid 25 and give write and execute permissions to the owner and group.

To make sure you are a member of "floppy" do:

```
sudo adduser <your_username> floppy
```

It will either say you are already a member, in which case the floppy should now work, or it will say you've been added, in which case you'll need to logout then log back in.

If you are the only user requiring floppy access you could add "uid=1000" to the fstab options. (assuming you are the default user setup ant installation)

You should strictly speaking still umount the floppy before removing - right click menu on desktop icon in Gnome - even though the "sync" option should ensure that data is written directly to disk rather than hanging around the VFS uncommited.

You may find "man fstab" and "man mount", especially the FAT specific options, of interest.

---

