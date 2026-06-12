---
title: "zip utility"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-17
Ok, I need to know the best zip utility for linux the built in one wont unrar a rar file.

I look through the search and found that 7zip was available so I went to my trusty synaptic and installed the one marked p7zip full.  Now it is no where to be found I even tried a run command for 7zip.  Also it didn't automatically take over the file associations.

Help please
Kezz

---

### Post by Joeb454 on 2008-01-17
Open up Add/Remove and search for "rar" (no quotes)

And there's a program called rar, which means you can right click .rar files and choose extract here.

I've always been able to open them with that installed

---

### Post by linux phreak on 2008-01-17
Type this in terminal.
sudo apt-get install rar

---

### Post by Sef on 2008-01-17
> Type this in terminal.
sudo apt-get install rar

Applications > Accessories > Terminal

Before doing that command, do this one:

```
sudo apt-get update
``` (That makes sure you repositories are the latest ones.)

then do

```
sudo apt-get install rar
```

---

### Post by KezzerDrix on 2008-01-17
ok thanks I did that, but how do I get the graphical 7zip to work.  I have used it before and it will do for most tasks.

Thanks

---

### Post by Steveway on 2008-01-17
Just use the included archive-manager.
If you have unrar installed then you can also open .rar files.
If you got the 7zip packages then you can open them, too.
I'm not even sure if there is a 7zip GUI like in Windows.

---

### Post by stchman on 2008-01-17
> **KezzerDrix said:**
> Ok, I need to know the best zip utility for linux the built in one wont unrar a rar file.

I look through the search and found that 7zip was available so I went to my trusty synaptic and installed the one marked p7zip full.  Now it is no where to be found I even tried a run command for 7zip.  Also it didn't automatically take over the file associations.

Help please
Kezz

Use the included File Roller(Archive manager).

Install these packages.

```

sudo apt-get -y install rar unrar p7zip p7zip-full
```

This will install the rar and 7zip packages.

When these are installed they allow File Roller to unpack or pack these archives.  Think of them as plugins.

---

### Post by bone2006 on 2008-01-22
I use 7-zip, because 7z seem to have the best compression out there.  I type in 7z and the command, so I'd assume it would be the same for extracting the rar files.

If you've already done sudo apt-get install p7zip-full

then do man 7z and it should give you some info and examples of how to use it.

I just recently compressed a 2GB file into 1.5GB using 7z

---

