---
title: "Removing tags off audio files"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-01
Is it possible to remove the tags off an existing audio file permanantly?

Or will I have to create a new file with tags removed?

---

### Post by HenrikAn on 2007-02-01
Yes, you can remove and/or  edit information in the id3 tags.
easytag and exfalso are two of many id3tag editors you could try.

---

### Post by Brunellus on 2007-02-01
if you want simply to strip id3 tags from a whole directory of files, and don't mind a bit of command-line-fu:

first, install id3v2.  This is a command-line id3 tag editor.

```

sudo aptitude install id3vt

```

then, once that's installed, change to the directory where you want to strip tags.  so if your stuff is in /foo/bar then its

```

cd /foo/bar

```

If you only want to strip the tags from one file, then it's

```

id3v2 -D file.mp3

```

However, if you need to strip id3 tags from *everything* in that directory *and* its subdirectories, you can

```

find .  -print0 | xargs -i -0 id3v2 -D &#8220;{}&#8221;

```

---

