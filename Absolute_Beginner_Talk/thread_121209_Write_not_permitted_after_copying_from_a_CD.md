---
title: "Write not permitted after copying from a CD"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by barisurum on 2006-01-24
I copy files from a CD, but they are not write-permitted. So I have to change their
permissions manually. Is there a way to make it automatic?
   Thanks

---

### Post by hentaidan on 2006-01-24
Not that I am aware of; the file retains permissions whenever you copy it, and as the you cant write to files on a CD, they retain the no write when they are copied.

I suppose you could write a script to the copy the file and then change the permissions?

Dan

---

### Post by bscbrit on 2006-01-24
hentaidan has provided one solution but it is still easy to right click in gnome, select properties, premissions and select 'write'.  

If you must automate it then a script is fairly easy to produce:

chmod -R +w <filename>

will do the trick.  <filename> can be a directory / folder.  The -R option with chmod makes the command recursive so it will seek out every file and sub-directory and make them all 'writeable'.

---

### Post by Gimbo on 2006-01-24
I came across this problem before, and this is the solution I got from the friendly people on this very forum:

Navigate to the folder containing the files you want permission for (eg /home/andrew/photos) by typing the following in a terminal window (Applications>Accessories>Terminal):

```
cd /home/andrew/photos
```

Then type the following:

```
chmod -R u+rw *
```

-chmod is used to change permissions
-The "-R" flag make the action recursive (applies it to all subfolders eg photos/mongolia)
-The rest means "give the **u**ser **r**ead and **w**rite permissions for everything in the folder (*****)"

[http://ubuntuforums.org/showthread.php?t=109999]("http://ubuntuforums.org/showthread.php?t=109999") is the original thread.

---

