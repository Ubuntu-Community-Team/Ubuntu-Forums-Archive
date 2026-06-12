---
title: "WinRar for Linux?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-05-25
I used WinRar under windows to pack bigger files(like 4,4gig ISO files) into smaller files, so they would fit in a mail or on smaler usb disk. How can I do that in Ubuntu?

Thanks for any help

---

### Post by theicyj on 2007-05-25
Search for unrar in the repositories and install it.  You will then be able to create and extract rar files. 

EDIT: Sorry, I didn't fully read your question.  I'm not sure how to create archives with multiple files.  Anyone else?

---

### Post by Happy_Man on 2007-05-25
You can use the rar utility. Open up Synaptic and search for it.

@theicyj: I think unrar/rar can do that too, and if not, file-roller should definitely do it....

---

### Post by _sAm_ on 2007-05-25
I have tried file-roller now, but I cant make several files with it(only one). I have installed rar from Synaptic, but think it is only for the file-roller program, not a standalone program?

---

### Post by fenian on 2007-05-25
Use [7zip ]("http://www.7-zip.org/")

> sudo apt-get install p7zip p7zip-full

---

### Post by Sparkster185 on 2007-05-25
You could also create on tar file out of your multiple files and then use rar to compress that single file.

---

### Post by _sAm_ on 2007-05-29
Fenian; are 7zip for Linux only a command line tool, or dos it come with GUI? (I cant find it, but have installed it).

I have tried Ark now, but I cant split the file. 

Sparkster185:
No, I have a USB pen that can only take 4 gig. To use this to transport an IMAGE(or ISO) file to another pc that is about 4,4 gig, I need to split the one file into several(in this case two files), and transfer it two times. You cant compress this file to be under 4 gig, but with WinRar(for Windows) I could split it in two.

---

### Post by arloth on 2007-05-29
I've used 7zip archives for a bit, but Ark or Xarchiver don't seem to have support in the gui to set volume sizes..   Looks like you may need to use the command line to do it.

Try the -v option with 7zip.  something like this will give you 2GB volumes: 

```
7z a -v2g archive.7z  dvdimg.iso
```

you may want to check the man pages for 7z and pick a higher compression if you want.  I usually use -mx=7 as the compression setting, otherwise it's a bit slow and memory hog for my liking.

---

