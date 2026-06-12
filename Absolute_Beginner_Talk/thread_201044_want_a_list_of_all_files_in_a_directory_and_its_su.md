---
title: "want a list of all files in a directory and its subdirectories"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-21
how can i get a printout of all files in a directory and its subdirectories, arranged accoding to what subdirectory the file is in? I just need; filename and filesize and directory location.


i want to get a listing of all the mp3s in my "audio" directory. this is why i ask.

---

### Post by kombipom on 2006-06-21
Open a terminal (Applications->Accessories->Terminal)

Go to the top directory you wish to start from (eg. "cd music" where music is the name of the directory)

type "ls -R > musiclist.txt" (without quotation marks)

This will produce a text file (named musiclist.txt) containing all the files in every directory under music.

Is that what you were after?

---

### Post by sas on 2006-06-21
[QUOTE=kombipom]Open a terminal (Applications->Accessories->Terminal)

Go to the top directory you wish to start from (eg. "cd music" where music is the name of the directory)

type "ls -R > musiclist.txt" (without quotation marks)

This will produce a text file (named musiclist.txt) containing all the files in every directory under music.

Is that what you were after?[/QUOTE]

you need the -s option for filesizes.
So do "ls -sR > musiclist.txt"

---

### Post by hanzj on 2006-06-21
sas and kombipom,
thanks for helping a nubu (new + ubuntu).

filesize is in plain format. For example "116300". 

Can i have the file size in this kind of format: "11.6 MB".

Thank you berry much.

---

### Post by zvezdogled on 2006-06-21
[QUOTE=hanzj]

Can i have the file size in this kind of format: "11.6 MB".

[/QUOTE]
add h...

ls -sRh

---

### Post by hanzj on 2006-06-21
zvezdogled,
Thank you berry macho!

---

