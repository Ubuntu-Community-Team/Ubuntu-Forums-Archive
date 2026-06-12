---
title: "A few questions about amarok"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-11-11
I have a couple of questions regarding amarok.

1)Amarok is set to automatically update my collection. When i add new albums the context menu recognizes them but the list of songs in the collection does not. How do i fix this?

2) I want to know whether or not I have the latest version of amarok. how do i know what version i have and, if it isnot the newest one, how do i update? also, will I lose all my moodbar data, etc. if i update?

Thanks in advance.

---

### Post by jasmuz on 2007-11-11
1- Tools-->Update collection

2- To check the version you are using, go to Help-->About Amarok
(im running the 1.4.7 version, wich is the latest)

Upgrading wont remove your personal information.

---

### Post by intense.ego on 2007-11-11
Turns out I am also running Amarok 1.4.7.

I tried "Update Collection" and "Rescan Collection" but the number of songs in the bottom remains the same even though I have added at least a few hundred songs.

---

### Post by rahimveron on 2007-11-11
Have you entered the folder path to be watched by Amarok?

---

### Post by forestpixie on 2007-11-11
I've needed to get rid of the database in the past with amarok to deal with not updating, though I didn't use moodbar - I'm fairly sure the moodbar info is kept separate.

You could delete the database, check in the same directory for moods I think - it's in a hidden folder - open nautilus (assume you're ubuntu) and do Ctrl+H 

the folder is in

> /home/*user*/.kde/share/apps/amarok

delete the collection.db or cut and paste to somewhere - then restart amarok and let it redo the database - 

have to say I'm not sure where the moodbar info gets put - I looked once but it was taking forever so I uninstalled

---

### Post by intense.ego on 2007-11-11
thanks forestpixie, i think i will do that. my moodbar data is stored with the songs themselves so it will be fine.

---

