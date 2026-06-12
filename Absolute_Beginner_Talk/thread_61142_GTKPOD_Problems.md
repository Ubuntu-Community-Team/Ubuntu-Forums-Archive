---
title: "GTKPOD Problems"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-08-30
Hey Folks!
Been smashing my skull trying to figure this out:

I installed gtkpod via the how to: in the how to: forum.  I formatted my ipod using a windows machine and copied a few tracks to it as instructed (to create the itunes.db file).

Now when I mount my ipod and load gtkpod it pulls up the list of tracks on my ipod no problem!

BUT! When I try to setup new playlist and copy new tracks, I hit the 'sync' button, and it says it's updating itunes .db but it doesn't actually copy over any of the songs... the original two or three show up, the rest do not.

BAFFLED!  :-x

---

### Post by nic2 on 2005-08-30
By default the ntfs file system is used under Windows XP, which is read-only under Linux.  Try changing the file system to fat32 and then perform the steps as explained.

Unfortunately I don't have any experience using an ipod and therefor can only go on my past experiences using flash drives.

---

### Post by the_purulent on 2005-08-30
Yup. I've done that too, the guide I have for installin gtkpod has me do that using fat32 so I can edit the file system.

---

### Post by poofyhairguy on 2005-08-30
[QUOTE=the_purulent]Yup. I've done that too, the guide I have for installin gtkpod has me do that using fat32 so I can edit the file system.[/QUOTE]

What I did was back up all my songs, and start with a clean slate. All gtkpod. Itunes never touched that parition post its last format....and it works great for months.

---

