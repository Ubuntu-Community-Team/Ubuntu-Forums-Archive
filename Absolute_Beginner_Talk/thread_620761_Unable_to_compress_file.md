---
title: "Unable to compress file"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by tiachopvutru on 2007-11-23
I'm trying to create an archive of pictures and avi files that sum up to about 270 MB. When I right-click and Create Archive, then choose tar.bz2, a windows pop up to hint that it's running, but when it's finish, I don't see a file being generated at all.

So right now, I think I'm going to try command line. What do I type to put several files into an archive? Also, what format would utilize the best compression?

---

### Post by LaRoza on 2007-11-23
I know that some formats have issues with files over a certain size, so research the various algorithms.

---

### Post by tiachopvutru on 2007-11-23
> **LaRoza said:**
> I know that some formats have issues with files over a certain size, so research the various algorithms.

Well, I was able to do create archive once using the command line to tar.bz2, but it barely compressed so I deleted it. I don't remember what that command was...

EDIT:

Nvm, creating a .zip file works, but do images do not compress well or something? The filesize barely reduce...

---

### Post by LaRoza on 2007-11-23
It may be that these files are already compressed, and you cannot do much more.

jpegs may already be compressed, as are many movies.

---

### Post by LaRoza on 2007-11-23
> **tiachopvutru said:**
> 
Nvm, creating a .zip file works, but do images do not compress well or something? The filesize barely reduce...
They don't compress well, without losing content.

---

### Post by tiachopvutru on 2007-11-23
> **LaRoza said:**
> It may be that these files are already compressed, and you cannot do much more.

jpegs may already be compressed, as are many movies.

I guess...

But well, it's still strange how I can create tar.bz2 in terminal but not in GUI

EDIT:

On another note, I didn't see the option to create archive of .rar format, how do I do that?

---

### Post by CatKiller on 2007-11-23
> **tiachopvutru said:**
> On another note, I didn't see the option to create archive of .rar format, how do I do that?

```
sudo aptitude install rar
```

---

