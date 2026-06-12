---
title: "question about chmod"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by NobleSavage on 2006-02-06
I have a directory with a bunch of subdirecterories and and each with a bunch of files.

If I want them all of them to be 755,  is there a way to change all files and subirectories with one command?

---

### Post by Gcool on 2006-02-06
chmod -R 755 /directoryname

---

### Post by cwaldbieser on 2006-02-06
[QUOTE=NobleSavage]I have a directory with a bunch of subdirecterories and and each with a bunch of files.

If I want them all of them to be 755,  is there a way to change all files and subirectories with one command?[/QUOTE]
```

$ chmod -R 755 folder

```
This will recursively apply to the permissions to folder and all files and folders inside it.

---

### Post by NobleSavage on 2006-02-06
Thank you both so very much!!!

I kept trying chmod -r 755 directory  and it just wouldn't work.

---

### Post by GTvulse on 2006-02-06
[QUOTE=NobleSavage]Thank you both so very much!!!

I kept trying chmod -r 755 directory  and it just wouldn't work.[/QUOTE]
But that's not what you want! At least reading your requirements. This **will** do what you want:
```

find directory -type d -exec chmod 755 {} ';'
find directory -type f -exec chmod 644 {} ';'

```
The second command is to fix your files permissions. You don't want executable files laying around unless they are truly executable files (and those should be in proper and known places in general; namely, places such as [font=monospace]/usr/local/bin[/font] or [font=monospace]/home/your_dir_/bin[/font]).

---

