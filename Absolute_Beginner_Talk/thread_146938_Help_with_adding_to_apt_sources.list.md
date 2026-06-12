---
title: "Help with adding to apt sources.list"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-03-19
I am following a guide to installing Opera. At one point the author nonchalantly says  "add the following to your apt sources. list file"...Obviously he didn't intend this walk through to be read by beginners, but here I am. A confused beginner. Where do I find the apt source. list file? How do I add to it? I have no idea where to look for it. I tried to poke around applications<add applications and sudo synaptic but that is about it for my guess. This is a big problem for me with Ubuntu. Every "guide" assumes I have basic knowledge of the os. I know noithing about the terminal, file system,control panel. Most of the time I can't find anything.  There isn't an "address" bar when I'm browsing files. I never know where I am or how to reference that point. With windows it always stated in exploreres' address bar were I was e.g.C:/program files/opera/plugins. Enough rambling, can anyone direct me to the apt sources.list file? Thank You.

---

### Post by egorgry on 2006-03-19
if you are comfortable with vi and the command line you can edit /etc/apt/sources.list. If you want to play it safe lauch synaptic and go to setting > repositories > add > custom then type in the source url you want.

---

### Post by fimbulvetr on 2006-03-19
Go back to synaptic.

Settings->Respositories->Add->Custom

Alternatively, you can edit the file by hand by doing this from the cmd line:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by catlett on 2006-03-19
Thank you. I know it is very simple to regular users but I had no idea what the author was refering to. Thanks again.

---

