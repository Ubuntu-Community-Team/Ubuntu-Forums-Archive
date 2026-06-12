---
title: "problems copying files from cd"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by chimps49 on 2007-01-16
ive looked around the forum and none of the threads seem to be specific for my problem. i've been trying to copy ".java" files from a cd to my desktop but i get an error saying that i don't have permission to read it.

i havent done much with the files but i'm assuming that they are needed when im using them in BlueJ to create objects; im very new to this, taking a class..

anyways, is there a way i can get 'permission' to read the files so i can copy them to my desktop from the cd? and how would i go about doing that?

---

### Post by NeoLithium on 2007-01-16
Are you using command line, or nautilus?

If you're using the file manager, you can go ALT+F2, type 

gksudo nautilus

and that'll give you the window with root permissions,

---

### Post by chimps49 on 2007-01-16
ok, i tried that and i was able to copy the files, but now when i tried opening them with bluej it tells me they are read only and that i have to have the files on my hard disk..which they are now that ive copied them onto root right?

---

### Post by meng on 2007-01-16
sudo chown [username]:[username] [name of file]

---

