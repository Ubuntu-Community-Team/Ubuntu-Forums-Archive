---
title: "Files in OSX can only be opened by root in Ubuntu"
date: 2008-05-16
forum: Apple Hardware Users
---

### Post by PaulFXH on 2008-05-16
I had almost exactly the same problem some months ago that was solved thanks to this [thread]("http://ubuntuforums.org/showthread.php?t=584752").
I have a large OSX partition on my MacBook (C2D) where I store my music folders and files. On the rest of the HDD, I have various partitions for a number of Linux OSes.
To enable me to play music in Ubuntu Hardy, I disabled journaling in OSX, and then changed the permissions on the My Music folder to Read&Write for me, group and everyone.
So, back into Ubuntu and, after mounting the OSX disk, I tried to open the music files. But, unlike before (in Gutsy) where I had no problem, now although I could open the Users/paul/Music folders, I could go no further.
This turned out to be because the underlying folders and files were owned by root (and yes, I could open and play any music file as root -- but that's not what I want).
So, as root, I changed the ownership of the /Users/paul/Music/My Music folder to me and then it opened fine. While doing this I clicked the "Apply Permissions to enclosed files" button.
However, the enclosed folders and files STILL retained root as the owner.
Now, obviously, I could go through each folder and file to change it's ownership to me but that would be quite a task.
Strangely, in Forecast Linux, which I also have on the MacBook (and this distro is quite Ubuntu-ish) without doing anything extra after making the permission changes in OSX, I have ready access to all of the very same music files.
I hope somebody can suggest where I might be messing up here.

---

### Post by cyberdork33 on 2008-05-16
> **PaulFXH said:**
> Strangely, in Forecast Linux, which I also have on the MacBook (and this distro is quite Ubuntu-ish) without doing anything extra after making the permission changes in OSX, I have ready access to all of the very same music files.
I hope somebody can suggest where I might be messing up here.

Changing the permissions/owner in OSX usually goes over better...

What kernel is Forecast using? that can mean all the difference.

---

### Post by PaulFXH on 2008-05-16
Thanks for your reply.
> **cyberdork33 said:**
> Changing the permissions/owner in OSX usually goes over better...
Went back to OSX and made sure both Me and Everyone were set to Read&Write for the /Users/paul/Music folder.
Back to Hardy, but now couldn't open the /media/osx/Users/paul/Music folder. Error message says I don't have permission.
So, change owner here to Me (as root). Now I can open the underlying folders as far as the individual music files.
However, still can't open/play the music files. Permissions for Group and Others were both Read & Write but for Me the permission was No Read & Write.
Very strange.
So went back to /media/osx/paul/Music/My Music and changed the File Access setting for Me/Group/Others from Blank to Read & Write (Folder Access for all was already Create & Delete) and then clicked the Apply Permissions to enclosed files button.
This did the trick and now all my music files from OSX are accessible from Hardy.
Don't remember it being this complicated the last time.


> **cyberdork33 said:**
> What kernel is Forecast using? that can mean all the difference.
The version of Foresight linux I am using (2.0.1) has a 2.6.23.16 kernel

---

