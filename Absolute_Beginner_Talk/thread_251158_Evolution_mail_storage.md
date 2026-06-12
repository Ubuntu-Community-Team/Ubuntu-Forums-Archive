---
title: "Evolution mail storage"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-09-05
Hey guys,

I'm tryiing to setup evolution fro email. Does anyone know where to change the default storage location or where it stores email by default? I can't seem to find anything in the Evolution documentation and I need to know so I can creat backups every now and then.

Thanks a lot,
David K

---

### Post by hw-tph on 2006-09-05
Evolution stores its mail in ~/.evolution/mail/ by default.


Håkan

---

### Post by rck on 2006-09-05
i believe the question was 'how to change' the mail storage location.
I have been searching everywhere for this too. ](*,) 
[B]If anyone can help please do.
[/B]


> **hw-tph said:**
> Evolution stores its mail in ~/.evolution/mail/ by default.


Håkan

---

### Post by p_vestjens on 2007-12-09
> **rck said:**
> i believe the question was 'how to change' the mail storage location.
I have been searching everywhere for this too. ](*,) 
[B]If anyone can help please do.
[/B]

I simply moved the .evolution folder to the desired location and created a soft-link to it from my home folder using e.g. "ln -s /media/data/home/patrick". Evolution doesn't seem to mind. :guitar:

Regards, Patrick.

---

