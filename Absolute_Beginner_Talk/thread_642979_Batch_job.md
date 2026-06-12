---
title: "Batch job"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Bingo Jesus on 2007-12-17
I'm busying myself with converting a folder full of AIFF files into Flac. The folder structure is organised as so, /Music/Artist/Album/song.aif. 

The conversion is easy enough using "flac *aif --delete-input-file" inside each folder. However, is there a way to recursively run the command inside every folder without doing it manually?

Thanks,
Bingo Jesus

---

### Post by HermanAB on 2007-12-17
Yes, you probably noticed that Bash doesn't have a proper loop command.  The reason is 'find'.

Do something like this:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

Read the find man page for details.

Cheers,

Herman

---

### Post by mozetti on 2007-12-17
Check out my post here: [http://ubuntuforums.org/showthread.php?t=642861](http://ubuntuforums.org/showthread.php?t=642861)

It's a BASH script for decoding flac and encoding to mp3 that I found online. You could probably adapt it for your needs.

---

### Post by Bingo Jesus on 2007-12-17
Super, it's chugging away now.

---

