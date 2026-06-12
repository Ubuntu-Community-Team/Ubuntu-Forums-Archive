---
title: "How to search for files?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by technikalKP on 2007-07-06
I can't figure out how to find files located on the hard drive.  For example, I know I have a file out there called 'userChrome.css' but I'm not sure where it's at.

If I try google desktop, it doesn't find it.

if I try the places|Search for Files and set the 'Look in Folder' option to 'File System', it doesn't find it.

If I go to the terminal and go to the root directory and type something like:

sudo  dir -R userchrome.css 

it still doesn't find it.

How do I search through all of the files in Ubuntu, regardless of owner/hidden status/etc, and find the location of the file?  ex - the equivalent of 'dir userChrome.css /s'?

Thanks!

---

### Post by steveneddy on 2007-07-06
locate name-of-file

---

### Post by por100pre1 on 2007-07-06
```


locate *filename-or-part-of-filename*


```

EDIT: Excuse me, steveneddy. I didn't see your post.

---

### Post by technikalKP on 2007-07-06
Awesome - thanks!

---

### Post by macogw on 2007-07-07
You may also want to add the Deskbar applet to your panel.  It's like Spotlight on OS X, if you're familiar with that.  It can search the internet, your hard drive, del.icio.us, the dictionary, and I think Amazon.com plus a bunch more that I don't recall.

---

