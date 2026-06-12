---
title: "where in Linux file system hierarchy am I to store my files?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-08-05
I have music, video and some text files. Where in Linux filesystem hierarchy would be logically to store them? In my home directory? But Opera and probably some other apps save there their settings, so the home folder became system-dependant. Also, media-files are for all users, not just for me

In Windows I had one partition for system, one for media-files and one for documents, but how to organize it here?

---

### Post by xpod on 2007-08-05
The only place you want to be storing stuff is your home directory probably:)

Hidden "."files in the home directory are the users configuration files & settings etc and they stay hidden & out your way unless you actually need to view/use them.....ctrl-h.:)
Just make a video,docs,pictures folder in your home for each of the different types of data you want to store. 

You can also have your home on a separate partition if you want and i`m sure you could make things as elaborate as you wanted but the above does the job for most i think...even with the separate partitions.

Anything more complicated than that and you`ll need to get reading i think:)

---

### Post by fimbulvetr on 2007-08-05
> **netimen said:**
> I have music, video and some text files. Where in Linux filesystem hierarchy would be logically to store them? In my home directory? But Opera and probably some other apps save there their settings, so the home folder became system-dependant. Also, media-files are for all users, not just for me

In Windows I had one partition for system, one for media-files and one for documents, but how to organize it here?

netmin,

All settings, etc. should be saved in your home directory. If an application is not doing this, they are breaking the rules of LSB and "Good application development".

As far as shared files, that's up to you, but I generally do something like make a directory /files and under there make my own heirarchy such as

/files
->music/
->videos
-->movies/
->audiobooks

and so on.

Once these dirs are setup you can change permissions for them so more than one person can access them. Come back to the forum if you need help with that setup.

---

### Post by netimen on 2007-08-05
Thank you, guys.

But the only question remains - in Windows when my system gets messy I simply format system partition, and install new windows (it's safe because system partition stores new data). But here settings and data are mixed in my home directory, so what if i'll want to reinstall my system?

---

### Post by Eddy Dean on 2007-08-05
Just keep your /home/ partition (Yes, you can set up /home/ on a separate partition, and it's wise to do so).
You will also be able to keep all your settings, like bookmarks, themes etc. These config files won't bother you, because they're usually hidden.

If you somehow manage to ruin a config file, sometimes it's enough to delete it, and the application will create an new one. Else you can copy an example from somewhere on the internet.

---

