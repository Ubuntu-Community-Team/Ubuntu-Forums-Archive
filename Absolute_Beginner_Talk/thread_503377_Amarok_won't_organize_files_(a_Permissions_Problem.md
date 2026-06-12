---
title: "Amarok won't organize files (a Permissions Problem?)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by theraj on 2007-07-17
When I try to organize my music files in Amarok (right click >> manage files >> organize) Amarok spits out an error something along the lines of:

"Sorry, Amarok could not organize xx files".

I feel like this may be a permissions issue.  I have tried uninstalling and reinstalling Amarok.  I am very new to Ubuntu and have no idea how permissions work.  I know there is something about being a root user that requires a password when doing terminal operations but beyond that, I am totally lost.  I appreciate the help in advance.

---

### Post by wormser on 2007-07-17
Have you checked who owns the directory where the files are?

```
ls -dal /path/to/directory
```

---

### Post by theraj on 2007-07-17
> **wormser said:**
> Have you checked who owns the directory where the files are?

```
ls -dal /path/to/directory
```

When I did what you told me for the Location I am moving the files FROM, I get:
drwxr-xr-x 17 raj raj 4096 2007-07-16 00:21 Desktop

When I did what you told me for the location I am moving the files TO, I get:
drwxrwxrwx 340 raj raj 16384 2007-07-13 13:57 Music


What should I do?  I have tried downloading EasyTag and that stuff look waaay too confusing, I'd rather just use Amarok to organize my library.

---

### Post by razy8 on 2007-07-18
Q1 Does this happen with just some files or with all of them ?
Q2 Did you import the files into the collection or are they just in the playlist ?
i've had the same problem with some (just some) mp3's, it may not be a permission problem but something related to the file(s) or Amarok

---

### Post by theraj on 2007-07-18
> **razy8 said:**
> Q1 Does this happen with just some files or with all of them ?
Q2 Did you import the files into the collection or are they just in the playlist ?
i've had the same problem with some (just some) mp3's, it may not be a permission problem but something related to the file(s) or Amarok


1) Happens to all files

2) I have tried organizing files in the left pane (the collection files of my library I imported) as well as ones in the current playlist.   Neither works.


Please help!

---

### Post by razy8 on 2007-07-19
Are you sure you set up the collection folder properly ? (Settings -> Configure Amarok -> Collection -> Check on the folder you want to have your music in)

If it is a permission problem you could try the old
```

sudo chown -R *username:username* /path/to/collection
chmod -R +rwx /path/to/collection

```
and```

sudo chmod -R +rwx /path/to/imported/files

```

And one more: Do you have enough space ?

---

