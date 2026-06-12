---
title: "Newbie question about &quot;Search for Files&quot; feature..."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by sonnychee on 2008-02-08
Hey Guys,

I used the 'Places->Search for Files' feature to look for the any files with the word 'ruby' in it.  The file I'm looking for lives in /usr/bin and when I start my search at /usr/bin or at /usr, the search result is as expected.  However, if I start the search from the 'File System', the search ends prematurely and misses the files in /usr/bin ..... Is the 'File System' place special in some way and doesn't allow depth searchs?  Very often I don't have a clue where a file resides and it would be super to search the entire file system...

Any hints would be appreciated.

Sonny.

---

### Post by jan quark on 2008-02-08
try the terminal command

```
locate bla bla
```

to search for files

the search has never worked for me

---

### Post by kellemes on 2008-02-08
Previous poster is right..
```
sudo updatedb
sudo locate blabla
```

"updatedb" generates the locate pathname database that is used by "locate" so you know all files on your system are in this database.

---

### Post by hyper_ch on 2008-02-08
or if you wanna have an advanced search, use "find".

---

### Post by sonnychee on 2008-02-08
Thanks Guys,

Should I infer that few peeps use the weenie GUI tool 'Places->Search for Files' and most prefer the locate and find commands?

Sonny.

---

### Post by klemens on 2008-02-08
kinda funny how many thinks you can learn by reading this part of the forum. thanks for the tip.

---

