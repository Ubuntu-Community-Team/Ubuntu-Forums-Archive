---
title: "commands for running deborphan"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-20
How do I use deborphan? The only commands I can find on here are

deborphan -a and deborphan-config

---

### Post by amastronardi on 2005-08-20
Have you tried *man deborphan*? It is quite explicative.

Cheers, Adrian.

---

### Post by gammyhand on 2005-08-20
Nope I haven't. But I just found out how to set up an orphaned filter in synaptic. Do I need anything more powerful than that? I have attached a screenshot of it's results. Do I NEED to keep any of that lot?

---

### Post by amastronardi on 2005-08-20
From man page:
*"deborphan  finds  packages  that have no packages depending on them. The default operation is to search only within the libs and oldlibs sections to hunt down unused libraries."*

If you are going to compile programs, it'd be better to keep them, otherwise you will be able to delete without any problem.

Cheers, Adrian.

---

### Post by gammyhand on 2005-08-20
[QUOTE=amastronardi]From man page:
*"deborphan  finds  packages  that have no packages depending on them. The default operation is to search only within the libs and oldlibs sections to hunt down unused libraries."*

If you are going to compile programs, it'd be better to keep them, otherwise you will be able to delete without any problem.

Cheers, Adrian.[/QUOTE]
 Cool thanks. I will delete all them. I could have read that myself but I am a bit edgy about doing stuff like that still and it's better to hear it from someone that has more linux experience :)

---

### Post by gammyhand on 2005-08-20
I don't understand why 

gstreamer0.8-ffmpeg
libdivx4linux
liblame0

would be in the orphaned list? They are used for streaming mpegs and playing back divx...any thoughts?

---

