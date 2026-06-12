---
title: "Annoying newbi questions"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-02-23
I just installed Xubuntu 7.10 on my computer, I've never used anything but Windows in my life, and I'm having some--probably annoying--newbi questions.

First: I installed the Sun Java and Macromedia Flash from the add/remove programs, went to youtube and it promted me to download "codex", which I did. Now the videos stream fine, but when I got to other places, like links from alluc.org to watch shows or whatever, they don't stream.

Second: I downloaded rhythumbox, and I want to play mp3s, but it doesn't. Let alone wav files. Weird thing: The totem movie player will play wav sound files, but not wav video... ?

Sorry if these questions have already been asked and answere. If they have, please point me in the right direction.

Thanks,
Frustrated Newbi

---

### Post by (((X))) on 2008-02-23
What I did, is:
I clicked on mp3 file to open with totem, totem asked to download some codecs, that´s what I did, now I am able to play mp3´s in both rythmbox and totem(gstreamer).

---

### Post by northern lights on 2008-02-23
Install ubuntu-restricted-extras:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by terry_gardener on 2008-02-23
try this link 

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by wolfen69 on 2008-02-23
```
sudo apt-get remove totem-mozilla
```
```
sudo apt-get install mozilla-mplayer
```
this will give you streaming media on the web.

---

