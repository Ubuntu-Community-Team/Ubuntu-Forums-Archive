---
title: "wget question"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by reza81 on 2007-01-31
hello,

I just read 'man wget' but didnt found or understood what I was looking for. 

What is the option to use for getting a complete content of a webspace & not just the index file? I need the *.zip's & *.rar's of an adres

& is it posible to do this on scripted sites like e.g. [http://www.geocities.com/anti_dcss/](http://www.geocities.com/anti_dcss/)

wget -x ??? [http://www.geocities.com/anti_dcss/](http://www.geocities.com/anti_dcss/)

---

### Post by energiya on 2007-01-31
You could include wget in a bash script. It worked for me, but I knew how the files will be named (file1.zip, file2.zip, ... ).

---

### Post by reza81 on 2007-01-31
> **energiya said:**
> You could include wget in a bash script. It worked for me, but I knew how the files will be named (file1.zip, file2.zip, ... ).

thats the thing ... i want to download the complete content without ever knowing which files actually are present on a specific webspace... in outer words; a command that sucks the whole space dry "everything". files, scripts,,, everything!

---

### Post by randiroo76073 on 2007-01-31
Look in synaptic for "HTTWebsite copier", its what I use to get whole site :)  I think it's it's also in Automatix2.

---

### Post by punx45 on 2007-01-31
yeah... the wget man page is pretty long. the section dealing with recursive options starts around line 1100
once in the man page, type '1109g' and it should take you there.

you are looking for option -r which gets recursively, which basically means 'go into subdirectories'
so therefore: ```
wget -r http://website.com
```
would get everything in 
website.com/
website.com/dir1/
website.com/dir1/dir1.a/
website.com/dir1/dir1.a/dir1.b/
website.com/dir2/
website.com/dir2/dir2.a/

you get the picture...

there are other options that are helpful too, like limiting the depth of subdirectories, and telling wget to dump everything in all the directories into just one directory locally ('-nd' directory options starts at line 587)(rather than recreating the remote file structure) and so on.
go ahead and give that man page another look :)

---

