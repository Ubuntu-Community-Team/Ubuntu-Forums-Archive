---
title: "partitioning a hard drive"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by r3st on 2006-06-06
i made a new computer and i have a 200GB hard drive im gonna partition.
what do you guys think of this?

btw its windows XP

[IMG]http://img129.imageshack.us/img129/7263/newbitmapimage1vx.png[/IMG]

---

### Post by hw-tph on 2006-06-06
I think you might get better response if you asked that in a Windows forum instead of in a Ubuntu GNU/Linux forum...

Håkan

---

### Post by r3st on 2006-06-06
ok
lets pretend its ubuntu

---

### Post by hw-tph on 2006-06-06
[QUOTE=r3st]ok
lets pretend its ubuntu[/QUOTE]
That depends almost 100% to what you're going to do with the computer. Also your own preferences of course.

Is it a personal desktop? Then personal files make up by far the largest amount of data.

swap :: (twice your RAM size)
/ :: 1GB
/boot  :: 100MB (that's more than enough unless you're planning on keeping a lot of old kernel images)
/var :: 2GB (for system logs, mail, apt cache, perhaps a database or two, web pages)
/usr :: 10GB (here is what most software lives - executables, libraries, images and so on)
/home :: (the rest - this is where all your documents, settings and so on go)

Perhaps add an /opt partition if you install some software there.

Håkan

---

### Post by aysiu on 2006-06-06
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by r3st on 2006-06-08
rifk aysiu, i actually came across you site when i was using google. that same page.

i use no swap file.  i have 2GB of ram. swap just slows it down.

---

### Post by hw-tph on 2006-06-08
[QUOTE=r3st]i use no swap file.  i have 2GB of ram. swap just slows it down.[/QUOTE]

Right...


Håkan

---

