---
title: "Help with ls creating directory listing"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2007-01-10
Can't seem to find the right combo for ls read man page which is like all man pages vague.

I want to create a tesxt file with listing of Directories only recursively and not the actual mp3's file 
names.

When I 

ls -r >MusicLib2.txt I only get the folders for Genre Only
if I 
ls -R >MusicLib2.txt I get Genre>Artists>Albums> then also get file1.p3,file2.mp3,file3.mp3,etc..

I don't want the tracks in the listing only Genre>Artists>Albums> without the mp3's listing.

Can anybody give me a clue ? Would be appreciated.

---

### Post by Bachstelze on 2007-01-10
Just look at all the lines in *ls -R*, you'll see that the lines corresponding to a dir start with ./ so you just have to do

```
ls -R | grep ./
```

---

### Post by orb9220 on 2007-01-10
Thanks as my ex-girlfriends use to say "That was Quick!".

Worked like a champ

---

