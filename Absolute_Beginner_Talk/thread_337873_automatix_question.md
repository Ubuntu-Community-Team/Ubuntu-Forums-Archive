---
title: "automatix question"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by thom314 on 2007-01-13
When using automatix, at the end it asks a question along the lines of "should automatix replace the source lists with its own - you may not want to do this". 

Well, do I want to do this or not? I don't know? Suggestions/explanations?

---

### Post by peebly on 2007-01-13
Hi

Which version of automatix are you using ?.

---

### Post by The Mekon on 2007-01-13
This will modify your permanent software sources  (System/Administration/Software Sources) to include the automatix list.

I believe that this will automatically update any software specific to automatix along with the normal Ubuntu updates.

It is up to you what you want.  I nmy case I just go along with automatix.

Brian

---

### Post by thom314 on 2007-01-13
I was using the one for Dapper but I just upgraded and downloaded the one for Edgy. I was always confused when using it with Dapper so before I started with a clean Edgy install I wanted to ask this before I hit that part of Automatix.

---

### Post by deadgobby on 2007-01-13
if you want to keep Automatix in the sources list. If you keep it on your sources/ repositories. When Automatix does an up date. It will update your system. If you do not want to keep Automatix on the source list. It will delete it self from the repos list and you will not get any updates for Automatix. 
Gobby

---

### Post by peebly on 2007-01-13
Hi

I use automatix 2, both on dapper and edgy, automatix 2 no longer asks this question.

---

### Post by thom314 on 2007-01-13
OK, thanks. I will plunge ahead.

---

### Post by arnieboy on 2007-01-15
```
sudo apt-get remove automatix
sudo apt-get install automatix2
```

---

