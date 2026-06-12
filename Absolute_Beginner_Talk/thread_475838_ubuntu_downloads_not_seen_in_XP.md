---
title: "ubuntu downloads not seen in XP"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-16
i downloaded few songs  3-4 days back in ubuntu and i could view them and play tham in XP...today i downloaded some songs from the same site inthe same format and yet i don't see them in XP...but only in ubuntu ???:(:(

---

### Post by starcraft.man on 2007-06-16
> **pardesi said:**
> i downloaded few songs  3-4 days back in ubuntu and i could view them and play tham in XP...today i downloaded some songs from the same site inthe same format and yet i don't see them in XP...but only in ubuntu ???:(:(

Uh, far as I know thats not possible... long as its a standard format it plays and is viewed in both. Can you check the extension is properly assigned at the end of the name. Thats the only thing I can think of...

---

### Post by pardesi on 2007-06-16
hey one minute i change the name of the folder in which i loaded my songs in ....right i get that now ...really foolishg to be bothering ubenteros with these kinda questions...:(

---

### Post by starcraft.man on 2007-06-16
> **pardesi said:**
> hey one minute i change the name of the folder in which i loaded my songs in ....right i get that now ...really foolishg to be bothering ubenteros with these kinda questions...:(

LOL, no problem. No question is silly, long as you got your answer thats what matters. Best of luck with that then, off to answer more q's :)

---

### Post by pardesi on 2007-06-16
:guitar: taht was cheering

---

### Post by alex-desktop79 on 2007-06-16
ubunteros :D:D:D

---

### Post by machoo02 on 2007-06-16
I'm one....[are you?]("https://launchpad.net/codeofconduct")

---

### Post by trak87 on 2007-06-16
If you are ever looking for some file, do this:

```
slocate -i <filename>
```

So you might have done this:

```
slocate -i .mp3
```

And this will find all your .mp3, or .MP3 files. The -i means to ignore upper/lower case. Slocate utilizes a database that runs periodically to index all of your files. So depending on when it was last run, you can manually update the database with this:

```
sudo updatedb
```

One cool thing is regular expressions. Let's say you are looking for a program file somewhere in the binary directories and you know it contains the number 2 in the name:

```
slocate -ir bin.*2
```

On my system this finds a bunch of binaries that may be the one I'm looking for. The .* is the regular expression and it means: match anything between the "bin" and the "2".

---

### Post by pardesi on 2007-06-17
tahnks yet again

---

