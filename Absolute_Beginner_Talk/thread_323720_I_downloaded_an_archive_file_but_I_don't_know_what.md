---
title: "I downloaded an archive file but I don't know what kind of archive it is"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by tee2 on 2006-12-22
I downloaded an archive file but I don't know what kind of archive it is. Is there any program or command I could run that could tell me what kind of file it is?

---

### Post by meng on 2006-12-22
Open Nautilus and right-click Properties, might tell you there. Or you could try opening it with Archive Manager (file-roller).

---

### Post by tee2 on 2006-12-22
When I open it in archive manager it says, "archive type not supported."

---

### Post by meng on 2006-12-22
So there's no file extension at all? Can you tell us the name of the file, and where you got it from, or is this some personal thing that isn't in the public domain?

---

### Post by Adramelech on 2006-12-22
file filename
example:
$ file .emacs
.emacs: Lisp/Scheme program text

---

### Post by tee2 on 2006-12-22
It's supposedly an ace file but when I try to use the unace program/command I get an error saying "File compressed with unknown method. Decompression not possible."

---

### Post by meng on 2006-12-22
I've noticed that unace in linux does not uncompress all ace files. Sorry to say Windows might be your best bet there!

---

### Post by Adramelech on 2006-12-22
Whats 'file' command output?
what decompressor are you using?

---

### Post by bluej100 on 2007-02-27
unace-nonfree in feisty universe utilities solved this for me. (Age of Empires II: Conquerors, here we come. :D )

---

