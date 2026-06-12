---
title: "Using filed from OS X partition"
date: 2009-01-28
forum: Apple Hardware Users
---

### Post by MasterCylinder on 2009-01-28
Would it be possible to connect to my OS X partiton (named Logic) so that I can "share" the music and pictures I have saved there? Duplicating my music, documents, and picture folders simply is not an option... I don't have enough space on my linux partition to copy 40 gigs worth of music and another 5 odd gigs of pictures and documents.

I can mount 'Logic' but I cannot access the folders that I am interested in.

Any advice?

---

### Post by ssorc on 2009-01-28
Can you provide us with some more information to help us help you?

What filesystem is the partition using? (eg. HFS+, with journalling?)

How are you mounting the partition? What tool(s), what options?

Thanks!

---

### Post by MasterCylinder on 2009-01-29
The OS X partition (Logic) is HFS+
I'm mounting it with the the default Ubuntu mounting by going to Places, and then right clicking on 'Logic'

I can mount it and view the contents of my OS X user folder, and I can access some files in it, for example NetBeans Projects opens fine. But I cannot access any of my music of pictures.

Edit: Probably a better question to ask: How do I get the permissions necessary to access the files that I want?

---

### Post by cyberdork33 on 2009-01-29
Linux respects the file permissions on your OSX partition...

You can boot into OSX, and change the permissions to allow 'others' to have read permission on those folders.

---

