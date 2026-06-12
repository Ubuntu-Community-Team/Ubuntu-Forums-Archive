---
title: "/mnt or /media ?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-02
Just a short question while reading my documentation.

It seems like general Linux documentation suggests creating mount points (don't know if I am using the right terms) in /mnt, while Ubuntu documentation talks about /media. I believe the Ubuntu installer defaults to /media.  I see there is both a /mnt and a /media folder, and I understand it's up to the user to do as he pleases.

I could not find any documentation on this difference.  What is the idea behind mounting stuff in /media instead of in /mnt?

Thanks, Peter

---

### Post by drfalkor on 2006-01-02
/media

EDIT: err, I misspelled your question !

---

### Post by pbb on 2006-01-02
[QUOTE=drfalkor]/media[/QUOTE]

Yeah, but *why*?

---

### Post by kaamos on 2006-01-02
The only difference I can quickly think of is that mounts in /media appear by default on your desktop and mounts in /mnt do not. Which is why I chose to mount my windows partition (a whopping 5gb of 60) to /mnt/win.

---

### Post by steve.horsley on 2006-01-02
[QUOTE=kaamos]The only difference I can quickly think of is that mounts in /media appear by default on your desktop and mounts in /mnt do not. Which is why I chose to mount my windows partition (a whopping 5gb of 60) to /mnt/win.[/QUOTE]
Yikes! Six months with Ubuntu, and I hadn't realised that one! Thank you.

---

### Post by Susana on 2006-01-02
[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT)

[https://www.redhat.com/archives/fedora-list/2004-November/msg03116.html](https://www.redhat.com/archives/fedora-list/2004-November/msg03116.html)

---

### Post by pbb on 2006-01-02
Thanks! That FHS document is a very interesting reference.

---

