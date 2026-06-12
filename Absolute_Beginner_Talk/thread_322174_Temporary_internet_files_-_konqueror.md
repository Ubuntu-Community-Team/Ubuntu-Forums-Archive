---
title: "Temporary internet files - konqueror"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mulligan.can on 2006-12-20
Is is possible to recover temporary files from Konquerors cache in kubuntu? Come to think of it where exactly is the cache located? I haven't been able to find any mention of it anywhere...

---

### Post by kpkeerthi on 2006-12-20
A couple of location I could think of:
1. /tmp folder
2. .konqueror (or a similar hidden folder) in your $HOME folder. I use gnome.. so not sure what the hidden folder for konqueror is.

---

### Post by jpkotta on 2006-12-20
It's somewhere in ~/.kde.  I think it's ~/.kde/share/cache.

---

### Post by mulligan.can on 2006-12-20
Thanks for the help. However I had already checked all of the above options and none are correct. On looking through the KDE homepage and documentation I found that it is supposed to be in ~/.kde/share/cache but when I went looking that folder doesn't even exist (using Kubuntu 6.10).

I even did a system wide search for some stuff that should have been in the temporary files (I searched by extension btw) and I couldn't find anything that looked helpful.

---

### Post by msak007 on 2006-12-20
First I'd say make sure you have cache enabled:
Settings --> Configure Konqueror... --> Cache --> "Use cache"

If you do, I believe the file location is actually **~/.kde/cache-<computer name>/http/**.

---

### Post by mulligan.can on 2006-12-24
Thanks, the cache was indeed located at ~/.kde/cache-<computer name>/http/ (its a symbolic link to somewhere in tmp).

Thanks for the help guys :)

---

