---
title: "Stiching together m4b files"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2007-12-10
So, i ripped an audio book off 5 CD's to 53 VBR mp3's. Then I converted them all to m4b with iTunes. This was back when I used Windows and I was a dumbass. I want to combine them all into one file. I tried to import them all into audacity, but it puts them as 53 different tracks instead of all on one. Does anyone know how to do what I want to do?

---

### Post by Rhubarb on 2007-12-10
Ok, there's a chance this will work (it works for stitching up multiple mp3's, and mpeg videos).
Copy all 53 m4b files to a separate directory, to a new temporary directory.
For example let's call it temp, and put it into your home folder, then copy all the m4b files to the temp directory.

In a terminal, change directory to the temp directory:
```
cd ~/temp/
```

Then use the cat command to concatenate all the files into one big file named audio_book.m4b:
```
cat * >> audio_book.m4b
```

audio_book.m4b should / might work for you.

The alternative is to re-rip the audio book if you've still got it to an ogg / mp3 file.

---

### Post by Dapilot1 on 2007-12-11
Where as that worked, I need to remove the tags from them beforehand. And I do not know how to do that.

---

### Post by Rhubarb on 2007-12-12
I don't know how to strip / edit tags in m4b files.
You might be able to convert all the m4b files to a more compatible format (such as mp3 or ogg), then cat them all into one big file.
Transcoding to another format will make your audio book have poorer sound quality.
As I don't have any m4b files around at all, I can't help you that much more.

Best of luck  ;)

---

