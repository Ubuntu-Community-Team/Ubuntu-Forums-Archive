---
title: "Tracker + Deskbar not working"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by nandotron on 2007-11-07
Hi,

I've just done a fresh install of ubuntustudio 7.10.  I am missing the spotlight-like functionality that is said to some as default in this release.  I added the deskbar applet to the panel myself, but when I try to search for something, I only get a list of web-searches, as my hard drive is not indexed.  I don't know how to run or configure tracker.  can anyone help?  also i am missing the ability to preview sound files by rolling over them that was present in feisty... anyone know how to activate it?

any help is greatly appreciated!

Nando

---

### Post by andrewsomething on 2007-11-09
I was missing sound preview as well. Apparently it's a known issue having to do with a change in the audio backend. Installing these packages seems to get it working again.

```
sudo apt-get install mpg123-esd esound
```

I'm also having tracker issues, but don't have any answers. You might want to look here: [http://ubuntuforums.org/showthread.php?t=583134&highlight=tracker](http://ubuntuforums.org/showthread.php?t=583134&highlight=tracker)

---

### Post by nandotron on 2007-11-09
thanks a lot for that, hopefully it'll get the preview working again, it was a really useful feature!

---

