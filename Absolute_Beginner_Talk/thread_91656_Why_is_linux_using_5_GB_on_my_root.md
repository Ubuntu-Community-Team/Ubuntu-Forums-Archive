---
title: "Why is linux using 5 GB on my root?"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by kapetanski on 2005-11-17
When downloading a torrent file I realised that the free space left on my root partition was almost gone. The root partition is 10 GB and if I select everything except /media and /home I get 2.2GB, but in my home folder I only have 4 GB, so where is the rest 3.8 GB? By the way I have both ubuntu and kubuntu desktops on the same root, maybe the gnome files are hidden in my home folder when I'm in konqueror? hmm...

---

### Post by kingsidy on 2005-11-17
Maybe there are items in your trash created by root, or under root, that were not emptied

---

### Post by kapetanski on 2005-11-17
If I look in the trash, or check it's preferences, I get 0 B. How do I open the trash in sudo mode?

---

### Post by kingsidy on 2005-11-17
type: gksu nautilus

then enter your root password. 

THen in your Home directory, press ctrl+H in order to view hidden files, 

then check the folder named .trash. See whether there is anything inside. If yes then delete it. Also check your temp directory while you're at it.

---

### Post by kapetanski on 2005-11-17
Thanx, I have a folder .kde/share/apps/ktorrent with tor* files that uses 2.5 GB in my home folder, is this the current downloads, or is it safe to delete this? I didn't find any temp directory, is it supposed to be .tmp in the home directory, or where else?

---

### Post by kapetanski on 2005-11-17
It was only some old cache I figured out, so now I have 2.5 GB more, thanx a lot! But I got some strange error messages when I deleted the stuff:


(nautilus:18317): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table st
ill has 13 elements at quit time (keys above)

(nautilus:18457): Eel-CRITICAL **: wrap_table_get_num_fitting: assertion `max_ch
ild_size > 0' failed

(nautilus:18457): Eel-CRITICAL **: wrap_table_get_num_fitting: assertion `max_ch
ild_size > 0' failed

(nautilus:18457): Eel-WARNING **: "nautilus-directory.c: directories" hash table                                             still has 11 elements at quit time (keys above)

---

### Post by kingsidy on 2005-11-17
I would not say tp delete the folder, but check and see what is inside the folder. Ktorrent is is bitorrent downloader for kde, when you installed the program, it creates a directory in your home directory. The default download directory for most torrent programs, is insisde the folder in the home partition  (.kde/share/apps/ktorrent in your case). Unless you change that default directory to something else, whatever you download goes in there. My guess would be that there might be something you downloaded that got stored inside that directory. Check what is inside the ktorrent folder and see if it something you recognize having downloaded. If so then you can delete. although  I think that deleting the folder would not harm you system. But see whether what is inside the ktorrent folder is deletable.

At least you pin-pointed where the space went.

---

### Post by kingsidy on 2005-11-17
the post came too late sorry. As far as the error messages are concerned, although i am not an expert, if yo deleted cache file then it is no big deal.

---

### Post by kapetanski on 2005-11-18
There are a few problems left though, when I select preferences on my home folder I get 4.4 GB instead of 9.6 GB that I got before I deleted the cache, but the free space has not changed, it's only 400 KB, although it should be several GB:s. Is there something i can do to change this, defragment or recount hashtables or something?

---

### Post by teaker1s on 2005-11-18
look in root home trash and delete contents

---

### Post by kapetanski on 2005-11-18
.Trash in my home folder is empty.

---

### Post by megamania on 2005-11-18
Looks like system-reserved disk space. I had this problem too and it was discussed on this thread:

[http://ubuntuforums.org/showthread.php?t=78333](http://ubuntuforums.org/showthread.php?t=78333)

---

