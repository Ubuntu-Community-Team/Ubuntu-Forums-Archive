---
title: "Moving files from subdirectories to one parent directory"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by GavinZac on 2008-01-13
I have many, many stock photos built up over the years. I'd like to gather them all into one folder since the directories they are in are pretty arbitrary.

They are structured like so:
~/photos/backup1/*.jpg
~/photos/backup2/*.jpg
~/photos/backup3/*.jpg
~/photos/backup4/*.jpg
~/photos/backup5/stuff/*.jpg
~/photos/backup5/stuff2/*.jpg
~/photos/backup6/stuff/*.jpg
~/photos/christmas/*.jpg
~/photos/christmas/stuff/*.jpg
...

and so on for about 75 upper level directories; no real naming structure except that all the files I want end in .jpg

What command can I run, to move all these files to a specified directory? I have mmv installed but can't figure it out for the life of me.

---

### Post by Joeb454 on 2008-01-13
I'm not sure about recursively going through each folder until it's done, but to move all files from one directory to the parent (assuming you've used **cd** to get to the correct place) simply run

```
mv ./* ../
```

---

### Post by GavinZac on 2008-01-13
> **Joeb454 said:**
> I'm not sure about recursively going through each folder until it's done, but to move all files from one directory to the parent (assuming you've used **cd** to get to the correct place) simply run

```
mv ./* ../
```

There are quite a lot of directories, but I'll start doing that now until someone figures out recursively :) ty

---

