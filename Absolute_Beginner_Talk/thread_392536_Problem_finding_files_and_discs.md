---
title: "Problem finding files and discs"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by svea on 2007-03-24
I've just started up Kubuntu 6.10 for the first time and can't find any files on my disc. I can't find the kubuntu files nor the other hard discs.  The discs are formatted and partitioned in different filesystems.

All I can see in Konqueror is:
/home where the desktop and some examples is
/media where I have my CD ROM and floppy (which is the drive where Kubuntu is installed)

Appreciate all help.

---

### Post by zekopeko on 2007-03-24
i don't use KDE but in GNOME everything is hidden by default except home & media (even when you open file browser with root rights).

 try enabling hidden folders and files.

be warned that you can't write to the rest of the disk as a normal user.

---

### Post by Bachstelze on 2007-03-24
This is a "feature" of Kubuntu Edgy :

[https://wiki.ubuntu.com/KubuntuHiddenFiles](https://wiki.ubuntu.com/KubuntuHiddenFiles)

Those kind of M$-like "features" are the main reson why I quit using Ubuntu...

---

### Post by hansoffate on 2007-03-24
try using the terminal to find files.

cd .. 
is to go back a folder
cd <foldername> is to go into that folder
ls  is to list the contents in whatever foldr your in.

If you get something about permissions. type sudo infront of the command.

Hope this helps.
-Hans

---

### Post by sad_iq on 2007-03-24
Open konqueror and press View -> Show hidden files (they are hidden by default)!
 To see the partitions of your disk type in konsole **sudo fdisk -l**

---

### Post by zekopeko on 2007-03-24
> **HymnToLife said:**
> This is a "feature" of Kubuntu Edgy :

[https://wiki.ubuntu.com/KubuntuHiddenFiles](https://wiki.ubuntu.com/KubuntuHiddenFiles)

Those kind of M$-like "features" are the main reson why I quit using Ubuntu...

i think that is a good thing. you shouldn't be poking there  if you don't know what you are doing.

and if you do then enabling hidden folders isn't a problem because you DO know what you are doing.

---

### Post by freebird54 on 2007-03-24
It might be a better idea to have the 'hidden' files show up in bold, or a colour not otherwise used - rather than hiding system stuff.  Showing hidden files was the first option I used - and I'm not sure *I* know what I'm doing  :D

To tell the truth I didn't even notice that system files were hidden - I just wanted to see where the 'dot' files like .wine and .bashrc were!

---

### Post by svea on 2007-03-25
Thanks for all the replies!

I've now found the files and discs i both Konqueror and Konsole but I can't access the other discs. I don't have permission to read them.

I've tried typing sudo cd /dev/disk/by-id/<discname> but without success.

All files I can access i on the same disc as the systemfiles.

---

