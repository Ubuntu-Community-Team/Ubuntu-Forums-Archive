---
title: "shortcut of a folder"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by tkoutso on 2007-05-21
I want to make a shortcut of a folder on the desktop. I right-click the folder, I chose "make link", but I receive an error message. What should I do?

---

### Post by Hobo Joe on 2007-05-21
What does the error say?

---

### Post by Kobalt on 2007-05-21
Right click on your desktop and create a launcher. As a command, enter the path to your folder with *nautilus* just before. Then give it the name/icon you'd like

---

### Post by Malibu Illusion on 2007-05-21
You could use the command line.  Open a terminal:

```
cd Desktop
ln -s /path/to/folder
```

Take care.

---

### Post by tkoutso on 2007-05-21
I created a launcher. At command line I write: nautilus/media/disc. A launcher is created, but isn' t working

---

### Post by Hobo Joe on 2007-05-21
What happens when you try to open it?

Also, is there some sort of permission conflict or something?

Try doing it with root permissions. 
If you don't know how to do that, alt+F2 then type:
```

gksudo nautilus

```

---

### Post by tkoutso on 2007-05-21
When I try to open the launcher, the error message says that there is no such directory. Maybe not nautilus/media/disc. Should I rewrite it? 

With the sudo command, I still have problem to "make link" by right clicking the folder.

---

### Post by freebeer on 2007-05-21
> **tkoutso said:**
> I created a launcher. At command line I write: nautilus/media/disc. A launcher is created, but isn' t working

I think you need a space between nautilus and /media/disc (assuming that /media/disc is a legitimate directory).

```

nautilus /media/disc

```

---

### Post by Kobalt on 2007-05-22
You do need to write the command down like this : ```
nautilus /folder
```

PS: please do not PM members in order to get answers, you have just been proven it's useless.

---

