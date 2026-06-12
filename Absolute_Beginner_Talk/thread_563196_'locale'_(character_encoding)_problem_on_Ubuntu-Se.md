---
title: "'locale' (character encoding) problem on Ubuntu-Server"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-29
I'm not really sure how to start and explain this. There are a lot of posts on this forum about this issue, however, I haven't managed to find a solution that works for me.

[SIZE="4"]The Scenario:[/SIZE]
I have a file server running Ubuntu server edition to hold backups of my /home directory. I sync them using rsync and ssh (everything is ext3) - The server folders are shared using samba and mounted on my main machine using smbfs.

[SIZE="4"]The problem:[/SIZE]
The server has no support for Danish characters like ÆØÅ. When i sync a folder from the main pc over to the server, these characters gets replaced by question marks or simply other strange characters.

It is especially irritating when it renames my music collection. And Björk is being called Bj|-@rk

First I thought this was because I used samba to share the folders but when I saw the problem also occurs when using rsync and ssh, I now know it has something to do with the encoding on my server.

Why is it the server edition hasn't got support for these characters all though I set the language to Daniish when installing?

**How Do I change the encoding?**

I have read a few posts of adamkane which are dealing with the same kind of problems, but it hasn't been working for me.

---

### Post by Hossie on 2007-09-29
You can specify a locale-option in smbfs/fstab/mount.

---

### Post by kasperbs on 2007-09-29
Will that have any impact on rsync and ssh

I should also mention that if I do a 'mkdir låst' on the server - it doesn't work either. That folder will be named l?st

---

### Post by Hossie on 2007-09-30
Do you mkdir with ssh or with a locally connected keyboard?

---

### Post by kasperbs on 2007-09-30
I mkdir with a danish keyboard connected to my pc, not a keyboard connected to the server. But that shouldn't mean anything when I use rsync should it?

---

