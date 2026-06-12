---
title: "How do i delete locked folder in desktop"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-22
I accidentally created a couple of folders that are somehow locked and i can't delete them or move them to the trash. there is nothing in them. how do i get rid of them?

---

### Post by neji on 2007-02-22
open nautilus as root, then you can delete:

$ gksudo nautilus

---

### Post by rapattack1 on 2007-02-23
um that command opens a desktop file browser. what now? I opened the desktop folder but i can't see anything relevent. in the terminal there is an error which says:
(nautilus:4639): libgnomeevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did now send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by mcduck on 2007-02-23
then just browse to where you have the directories you want to remove, delete them and close the root nautilus window.

---

### Post by rapattack1 on 2007-02-23
i can't find or see the folders anywhere in the browser. i looked around in the different folders.

---

### Post by The Seeker on 2007-02-23
First cd to the directory in question then,

> sudo rm -rf foldername

---

### Post by rapattack1 on 2007-02-24
it says that it is a directory so i can't delete it.

---

### Post by highneko on 2007-02-24
> **rapattack1 said:**
> it says that it is a directory so i can't delete it.
```
cd ~/Desktop; ls -al
sudo rmdir directoryname
man rmdir
```

---

### Post by rapattack1 on 2007-02-24
says no such file or directory. i really don't understand the manual things yet. i have tried but they are beyond me at the moment.

---

### Post by highneko on 2007-02-24
Ah. That's because you're not using quotes. It's a common mistake. Files or folders with spaces you must use quotes or escapes. n_n
```

[COLOR="DimGray"]# You can figure out what the directory is like this:[/COLOR]
file "delete this also"
[COLOR="DimGray"]# Then delete it if you want like this:[/COLOR]
sudo rmdir "delete this also"

```

---

### Post by rapattack1 on 2007-02-24
thanks so much that worked!!!!
hey you can probably see by that screenshot that i have a few folders on the desktop. where am i supposed to put them. sorry i am an ignorant from microshaft and am trying to be a good linux user.

---

### Post by Maestro23 on 2007-02-24
> **rapattack1 said:**
> thanks so much that worked!!!!
hey you can probably see by that screenshot that i have a few folders on the desktop. where am i supposed to put them. sorry i am an ignorant from microshaft and am trying to be a good linux user.

Throw all the junk you download in your home directory.

---

### Post by nhandler on 2007-02-24
> **rapattack1 said:**
> i can't find or see the folders anywhere in the browser. i looked around in the different folders.

Your desktop should be at /home/YOURNAME/Desktop
In the root nautilus, browse to that location and delete the folder


If you want to do it from a terminal:
cd /home/YOURNAME/Desktop
sudo rmdir --ignore-fail-on-non-empty DIRECTORYNAME


That should delete the folder and anything inside it


Edit: I guess I'm too late. I forgot to refresh this thread before posting.



About the the junk, toss it in your home directory. I have my home directory set up with sub folders for images, music, movies, documents, scripts. That keeps it organized. I also hide folders (Either add a period before the filename, or use the .hidden file) that I rarely use. That way, they're still there for when I need them, but don't clutter up the folder.

---

### Post by rapattack1 on 2007-02-24
thanks so much it looks a lot better now!:)

---

