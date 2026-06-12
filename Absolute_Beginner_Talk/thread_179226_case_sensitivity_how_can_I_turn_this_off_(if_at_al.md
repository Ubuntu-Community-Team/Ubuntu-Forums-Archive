---
title: "case sensitivity: how can I turn this off (if at all?)"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by dr.drake on 2006-05-19
I know that linux is case sensitive, and that by default everything is lowercase (or undercast), but I also notice that there is a **Desktop** and a **X11**, so it is possible to have capitals.

why I want the possibility for capitals, is because with downloading bittorrents, the program sometimes creates folders and some of these folders have names with capitals, like "VIDEO_TS". ubuntu automatically changes these to undercast, so the file won't load because it can't create said folder.

so...

is there a way HOWTO allow certain acts to create capital lettered folders?

thanks,

---

### Post by skinnygmg on 2006-05-19
is there an option in your bittorrent client to set defaults for folder names in your save directory?

---

### Post by jorn on 2006-05-19
I just want to say that linux manages files and folders with both lower and upper case letters. You can create folders with capital letters as much as you want.

Why Ubuntu changes the letters has maybe something to do with the application as #2 suggests.

---

### Post by steve.horsley on 2006-05-19
Are you saving files on a FAT partition? If so I can understand possible upper/lower case confusion - in fact nautilus gets its knickers really badly twisted when creating folders on FAT partitions. All I can suggest in this case is to use a proper linux partition - ext2/3 or reiser maybe.

If you are saving files on a linux partition (ext2/3, reiser etc) then any confusion over upper/lower case directory names is entirely due to either the BT client program you are using, or whatever it is trying to save. So if the directory is created in lower case, that's because the BT client told linux to create the directory in lower case. And if the application then wants to access the directory as though it were upper case, then the application is in error. I can imagine this might happen if a windows person wrote some python scripts for instance, and didn't pay proper attention to the filenames.

So there is nothing you can do to enable upper case directory names, because they are already enabled, except for FAT drives. And there's nothong you can do to disable case sensitivity, other than using FAT drives.

---

### Post by Klaidas on 2006-05-19
It seems to let me create folders which have capitalized name.
[QUOTE=Klaidas's terminal]klaidas@ubuntu:~/Desktop$ mkdir -v TEST
mkdir: created directory `TEST'
klaidas@ubuntu:~/Desktop$ ls | grep TEST
TEST
klaidas@ubuntu:~/Desktop$[/QUOTE]

---

### Post by dr.drake on 2006-05-20
ok, thank you all for replying
I *was* trying to safe file on my windows fat32 partition, and I couldn't create capital letter files.
the client I use is azureus, and I couldn't find an option to change captation.
after my other downloads finished, I set my download folder to a linux ext3 one, and now it works like a charm.
the only problem now is that my linux partition is relatively small, surely not big enough to store more than one complete 4GB DVD on it, but I'll deal with that one later.

thanks again!

---

### Post by catlett on 2006-05-20
I don't use azureus but when I use my bittorrent client I make a folder ahead of time.  For instance I would go to the windows partition and make a bitsaved folder. Then in the preferences box I would change the default download folder to my newly created bitsaved. Can't you do something like this or am I misunderstanding something?

---

