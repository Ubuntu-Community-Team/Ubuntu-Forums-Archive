---
title: "Howto Turn on Video Preview into KDE?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by La_Frenezo on 2006-07-10
Hi

Does anyone know howto turn on the video preview in Konquerer?

---

### Post by fluffington on 2006-07-10
> **La_Frenezo said:**
> Hi

Does anyone know howto turn on the video preview in Konquerer?

[list=1]
[*]Install libarts1-xine (search for it in Adept or *sudo apt-get install libarts1-xine* in the terminal).
[*]In Konqueror, View -> Preview -> Video Files (I had to log out and back in for the option to show up).
[*]Still in Konqueror, Settings -> Configure Konqueror... -> Previews & Meta-Data, change Maximum file size to something bigger than the default of 5MB
[/list]

Note that the Maximum file size slider only goes up to 100MB, which is smaller than most of the video files I have on my machine. If anybody knows a workaround for that one, tell me.

---

### Post by La_Frenezo on 2006-07-11
The 100MB limit is the problem; mainly cause I need it for my movie-previews. Does noone know a workaround?

---

