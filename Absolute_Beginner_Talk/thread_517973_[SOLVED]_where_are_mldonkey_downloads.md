---
title: "[SOLVED] where are mldonkey downloads?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-08-05
I posted in other places, but got no satisfactory responses, so here goes again: where on earth do downloaded files go?? I didn't change any of the default settings, I've looked in all likely (and some unlikely) places and I've searched for the files but I can't find the files I download using mldonkey. They just disappear from downloads and appear in uploads when they're finished.
Also, given that mldonkey is supposed to be connected to so many networks, it doesn't give that many search results. Am I missing something?

---

### Post by tprzepiorka on 2007-08-05
I have never used mldonkey, but I suggest you check in the /home/<USER>/.mldonkey folder if there is one. Also go through the settings in mldonkey and you should be able to find where they are saved too. Good Luck.

---

### Post by kleo skywalker on 2007-08-05
> **tprzepiorka said:**
> I have never used mldonkey, but I suggest you check in the /home/<USER>/.mldonkey folder if there is one. Also go through the settings in mldonkey and you should be able to find where they are saved too. Good Luck.

I (obviously) looked in all those places before posting. They're nowhere to be found!

---

### Post by tprzepiorka on 2007-08-05
> **kleo skywalker said:**
> I (obviously) looked in all those places before posting. They're nowhere to be found!

Hmmmm...Sorry. I have no idea where to look :confused:

---

### Post by vadania on 2007-08-05
Main menu (Applications) >> Accessories >> File search
OR 
in File Browser (Nautilus/Konqueror) go to View menu, choose Show hidden files.
On the Main toolbar in File browser window the last button (from left to right) should be "Search". Click it and in the address bar type the name of the file you're looking for.

Do not type the whole name. It is much better to type a fragment of the file name if you type it correctly.
If you have not found anything yet, change search location to /. 
mldonkey could have hidden temporary directories in /tmp, /opt, /var

---

### Post by kleo skywalker on 2007-08-07
> **vadania said:**
> Main menu (Applications) >> Accessories >> File search
OR 
in File Browser (Nautilus/Konqueror) go to View menu, choose Show hidden files.
On the Main toolbar in File browser window the last button (from left to right) should be "Search". Click it and in the address bar type the name of the file you're looking for.

Do not type the whole name. It is much better to type a fragment of the file name if you type it correctly.
If you have not found anything yet, change search location to /. 
mldonkey could have hidden temporary directories in /tmp, /opt, /var

I've done all these things - looked in hidden folders in my home folder, searched the home folder as well as the entire filesystem, - but still no luck! Very frustrating.

---

### Post by kleo skywalker on 2007-08-07
**Places-->Search for files** and found them hiding in a folder in /var/lib.
Thanks.

---

