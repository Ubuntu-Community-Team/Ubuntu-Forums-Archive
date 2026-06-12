---
title: "music filenames with accented letters don't play"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by bsmith1051 on 2007-02-14
I have a huge collection of CDs that I've converted to MP3s and I've also created .M3U files for each.  Many of my latin CDs have song titles with accented letters, e.g. "Rosario - Estoy Aquí.mp3".  I usually load these .M3U files into the default Movie Player but I've also tried VLC, and the result is always the same -- "file not found".

Why don't these programs 'see' the files with accents in the filename?

---

### Post by annda on 2007-02-14
because their names haven't been saved using the utf coding standard. i assume you did not rip them under linux?

you need to convert the filenames to utf. i can' t think of any programs now - but there are some. i hope someone here knows more and can help you.

---

### Post by sympeltun on 2007-02-14
I took a song and changed the file name to the one you specified, it worked in amarok, and xmms music players.. 
hopefully you wont have to change the filenames of all the songs, it's really a pain if you have a huge library
i hope that helps you out a bit too..

---

### Post by bsmith1051 on 2007-02-14
> **annda said:**
> because their names haven't been saved using the utf coding standard. i assume you did not rip them under linux?
That is correct, they were mostly all ripped on my old Windows machine. 

EDIT:
I found a workaround!  The problem is the .M3U file rather than the .MP3 filename.  If I open the .M3U in Text Editor and re-save it in UTF (rather than the default "Western") than it works.

I still don't understand why this is an issue, though.  I mean, the .M3U file clearly contains the accented letter(s) so why Movie Player (or Ubuntu OS?) recognize it as the same?  It just seems like there's an obvious translation 'matrix' missing.

---

