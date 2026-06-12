---
title: "creating symbolic link"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by visionset on 2006-08-28
Trying the simple task of creating a symbolic link on my desktop to the index page of my java api docs

me@mypc:home/me/Desktop$ sudo ln -s /usr/java/jdk1.6.0/docs/api/index.html

creates the link 'index.html'.

Double click presents dialog:

Do you want to run "index.html", or display its contents?
"index.html" is an executable text file.

with options to 'run in terminal', 'display' or 'run'

none of these pull up a browser and I don't want to go through a dialog anyway.

It does by all appearences to be a valid symlink by virtue of its properties:

Link Target: /usr/java/jdk1.6.0/docs/api/index.html

Any clues?

---

### Post by kaamos on 2006-08-28
right click - open with - firefox

---

### Post by visionset on 2006-08-28
Okay it opens firefox but the wrong url opens:

file:///home/me/Desktop/index.html

this is not the path in the symlinks properties

---

### Post by visionset on 2006-08-29
I realise I can just create a bookmark from firefox, so perhaps this wasn't a great example. But more my point is a generic method of creating symlinks that work as if they were created and used from the terminal. Maybe my understanding of how symlinks are used is at fault? I tried at the command line ./index.html and it just parsed it to the terminal, perhaps unsuprisingly.  Anyhow I'll get there in this new crazy world.

---

