---
title: "update flush   what?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by FrankBlourtango on 2007-08-08
There is a command you enter to write all data in memory to hard disk.  I can't remember it and looking at lists of linux commands isn't helping.  Anyone know?

---

### Post by oilchangeguy on 2007-08-08
> **FrankBlourtango said:**
> There is a command you enter to write all data in memory to hard disk.  I can't remember it and looking at lists of linux commands isn't helping.  Anyone know?

all data in what memory? do you mean ram?

---

### Post by tszanon on 2007-08-08
> **oilchangeguy said:**
> all data in what memory? do you mean ram?
Memory dump on demand? It seems possible, but i think it would be very unreliable, since memory content can change a gigazillion times per second.
Anyway, I'm interested in it too...

[SIZE="1"]Edit: quoted the wrong person...[/SIZE] 8-[

---

### Post by FrankBlourtango on 2007-08-08
I'm not explaining myself very well.  

If you decided that you wanted to just yank the power cord out of the back of your PC, you should enter some command before you do so because some of the data is not actually written to hard drive yet.

This command forces the data to be written from what, virtual disk?

---

### Post by schorsch on 2007-08-08
> **FrankBlourtango said:**
> If you decided that you wanted to just yank the power cord out of the back of your PC, you should enter some command before you do so because some of the data is not actually written to hard drive yet. This command forces the data to be written from what, virtual disk?

Just a guess, but are you looking for the command "sync"? The man page says:


NAME
       sync - flush file system buffers

DESCRIPTION
       Force changed blocks to disk, update the super block.

---

### Post by FrankBlourtango on 2007-08-08
That's it.  synch.

thanks

---

### Post by bapoumba on 2007-08-08
Hmm, not sure what you are talking about. Is this the [magic sysreq]("http://www.debian-administration.org/articles/457") keys ?

---

