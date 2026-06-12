---
title: "Restoring Original Repository list"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-10-05
Basically, as the title suggests, I need to restore my repositories to their original state. I used Automatix after installing Ubuntu, and chose to keep the repository list which it used to install all the programs etc, which I think was a mistake since I can't find programs that I know exist (and I've seen when using the other repository lists/servers).

So how can I resore them back to what they were originally, please ?

Doug

---

### Post by bulldog on 2006-10-05
Look in /etc/apt/ if there is a copy made and ifso,how it's named.

I think Automatix made a copy of the original.

If you found the copy type in your terminal,
```
sudo cp /etc/apt/sources.list-backup? /etc/apt/sources.list
```

---

### Post by Sweet Spot on 2006-10-05
Ok, thanks. I found the backup file, but when I enter that command (of course I'm entering the number associated with the file) I get

" sudo: cp/etc/apt: command not found"

I've tried several variations with spacing too.

---

### Post by calvinthomas on 2006-10-05
Type ```
sudo nautilus /etc/apt
```

Go to the sources.list file and rename it to something else (say sourcesback.list by right clicking and renaming)

Go to the backup file and rename that as sources.list by right clicking and renaming.

Then go to the terminal and type: ```
sudo apt-get update
```

Calv

---

### Post by Sweet Spot on 2006-10-05
Thank you Calv, should've thought of that ! 

Doug

---

### Post by Sweet Spot on 2006-10-05
Here's a stupid question: I seem to remember certain programs existing in the "add/remove" application, particularly one programe named something like, or exactly like, "Frostwire". It's a peer to peer downloading program, which now, no longer shows up in the add/remove programs list under the internet category. 

I managed to fix the repository source list, which I initially thought was part of why it didn't show up anymore, but it's still not there despite fixing it. Is it just that the program its self is no longer in existence ? Or is it something else ?

Doug

---

### Post by SailingWoodwind on 2007-01-28
Hm, by this time you propably have found frostwire....if not, it's included in automatix.

---

