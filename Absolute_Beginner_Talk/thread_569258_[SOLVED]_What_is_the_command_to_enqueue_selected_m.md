---
title: "[SOLVED] What is the command to enqueue selected media files to totem?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-10-06
I would like to enqueue media files to totem. 
I use gtkpod to read the music from my iPod. According to [http://linuxreviews.org/man/totem/](http://linuxreviews.org/man/totem/), the command for my need is 

**totem --enqueue **[I]filename|URI.

[/I]So in the preferences dialog window in gtkpod, I have

```
totem -enqueue %s
```, but nothing happens.&#12288;I tried this command in terminal, but it says > Unknown option -enqueue

[COLOR=Magenta]
SOLVED:
I needed 2 dashes.[/COLOR]



Please help.

---

### Post by ryanVickers on 2007-10-06
Do you _absolutely_* have* to have a terminal command, or can you do it the other way, which is to select files and right-click and pick "open in totem media player"

---

### Post by hanzj on 2007-10-06
Ryan,
I've solved my own thread before I read your message.

Anyway, your idea will play in totem player, erasing the current playlist.

---

