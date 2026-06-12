---
title: "Is it possible to &quot;lock&quot; a directory ...?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-26
... so that you can only access it after having entered a keyword?  In Ubuntu / Xubuntu, I mean, of course.
BTW I wouldn't consider putting the files into a password-protected archive an alternative because I don't want to pack and unpack it if I want to use or add a file.
Thanks.

---

### Post by netkid91 on 2007-02-26
The only way I know of is owning it by a different user, pass-protecting that user, and using su/sudo to act as that user to get at the files.

---

### Post by Blofeld on 2007-02-27
There's an idea, thanks.
PS:  I would STILL like to lock that directory!

---

### Post by steve.horsley on 2007-02-27
It is possible to create a file and use it as an encrypted partition. Then you have to mount the partition and give a password to the mount command - mount it wherever you want it of course. 

Here is a tutorial - I've done it this way - it works:
[http://news.softpedia.com/news/How-to-Setup-an-Encrypted-Filesystem-42248.shtml](http://news.softpedia.com/news/How-to-Setup-an-Encrypted-Filesystem-42248.shtml)

I also found these but haven't tried them
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=encrypted&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=encrypted&titlesearch=Titles)

---

### Post by Blofeld on 2007-02-28
Sweet!  Thanks.

---

