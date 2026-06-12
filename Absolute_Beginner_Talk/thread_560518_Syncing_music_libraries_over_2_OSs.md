---
title: "Syncing music libraries over 2 OSs?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by StevenX on 2007-09-26
I know this probably isn't possible, but is there any way to sync my music library across 2 operating systems? I use both WinXP and Ubuntu on a regular basis, so every time I get a new song I need to add it to my music libraries in both OSs (Banshee on Ubuntu, and iTunes on XP).

Is there any way that if I added it in one program, it would automatically add to the other next time it ran? Sort of like using Foxmarks in Firefox to sync bookmarks across XP and Ubuntu?

---

### Post by darc on 2007-09-26
You can store all your music on a partition that is shared between both OS's (so probably VFAT) and set your media player to monitor that folder/partition for changes and automagically update your library when a change occurs.

I know Amarok can do the automagic updates in Linux, not sure about Banshee.  Also, not sure if iTunes can do that in windows,  I think MediaMonkey can though.  

EDIT:  You could also consider storing all your media on an external hard drive, same concept as above except using an external instead of an internal drive.  My friend does that to keep all his media available on both OS's.
-darc

---

### Post by notwen on 2007-09-26
I'd create a FAT32 partition and simply point iTunes and Amarok to this location.  I believe Amarok has the option to constantly check for new content, not sure on iTunes.

---EDIT---

darc beat me to it. =p

---

### Post by reckless2k2 on 2007-09-26
itunes does not auto refresh. that is correct.

---

### Post by darc on 2007-09-26
> **reckless2k2 said:**
> itunes does not auto refresh. that is correct.

Well, that busts our idea if you continue to use iTunes.  Personally, I absolutely hate iTunes, but this isn't about me : D

I double checked and you *can* make this work with MediaMonkey, it has a built in file monitor so it will pick up file changes and incorporate them into your library.

Note that the generic version of MediaMonkey is free.
-darc

---

### Post by StevenX on 2007-10-03
Thanks for the suggestions - I'm gonna try those out! :)

---

### Post by Depressed Man on 2007-10-03
What I do is use ntfs-3g and have all my media on the NTFS drive. And simply have Linux read media from there (and write if necessary). Any changes to the media library will be reflected in both OS.

---

