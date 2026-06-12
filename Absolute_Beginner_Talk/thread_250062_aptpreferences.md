---
title: "apt/preferences"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by miyumi on 2006-09-03
Okay, so I'm not exactly an absolute beginer, but since it's been a long while, it's close enough. I need to know how to create the preferences file for apt. I can't seem to get past the permissions. I vaguely remember that I created it in terminal, but I can't remember how, and I can't find whatever site I had found last time to tell me how... so any help would be appreciated.

---

### Post by ciscosurfer on 2006-09-03
The man page: [COLOR=Red]man apt_preferences[/COLOR]

---

### Post by miyumi on 2006-09-03
How does that create apt/preferences? If it's not already there, how can it tell me about it?

---

### Post by msak007 on 2006-09-03
> **miyumi said:**
> How does that create apt/preferences? If it's not already there, how can it tell me about it?

To create it, simply open up a text editor, type what you want in it, and save the file with the name "preferences". For example, from a terminal:

```
sudo nano /etc/apt/preferences
```

Then you can type what you want in it, then hit CTRL+X to exit and save it. If you prefer using a graphical editor, in the terminal type this (I assume you're using Ubuntu):
```
gksudo gedit /etc/apt/preferences
```
Then type what you want, hit the Save button, and your file should be there.

---

### Post by miyumi on 2006-09-03
Thank you.

---

