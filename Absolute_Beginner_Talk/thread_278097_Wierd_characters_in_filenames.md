---
title: "Wierd characters in filenames"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Futile on 2006-10-15
Here's a screenshot of my problem:
[[IMG]http://img261.imageshack.us/img261/6603/aumletslj2.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=aumletslj2.jpg)
That folder should be *Gelatin i Botaniska **Trädgården***

I seem to have problems with displaying å, ä, ö (I'm swedish as it were). It's an EXT3 filesystem, and the files were put there via FTP from Win XP (NTFS). I did select Swedish keyboardlayout and language during install.

Is there an easy way to set the correct encoding in the File Browser?

---

### Post by Futile on 2006-10-18
bump.

I can't possible be the only one having this issue?

---

### Post by kalle314 on 2006-10-18
The filenames in windows are encoded in some windows encoding system, which does not contain any information about whether it is supposed to be written in english, swedish or russian (I think). So ubuntu can only guess that it is  standard ASCII characters. Perhaps there is some way to tell ubuntu explicitly how to interpret the filenames from windows?

Otherwise, you cam change the filename by right-clicking the icon and changing the file name manually.

(By the way, this is the wrong forum. I came only here by chance to see what this forum was about. It is "Accessibility refers to software used primarily by people who are deaf, are mobility impaired, or have sight problems including colour blindness or dyslexia." This should rather be in  the general help forum.)

---

### Post by Futile on 2006-10-20
Perhaps some kind admin could move this thread to a more apropriate forum?

---

