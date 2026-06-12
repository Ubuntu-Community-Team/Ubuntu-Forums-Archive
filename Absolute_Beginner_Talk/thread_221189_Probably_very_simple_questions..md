---
title: "Probably very simple questions."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-22
Where do files such as pictures, music and videos go? In Windows each one had it's own preset folder, I know this isn't Windows but are there such presets or do I need to make them myself? If I do need to make them, how and where would they go?

Sorry for being such a bother.

---

### Post by taurus on 2006-07-22
They can go anywhere you in your home directory but personally, I would seperate them.  Open a terminal and create those directories as

```

mkdir ~/movies ~/music ~/pictures

```
Then, store your movies in ~/movies, your music in ~/music, and your pictures in ~/pictures...  You can move around with the cd command as

```

cd movies <-- from home directory
cd ../music <-- while you are in ~/movies directory
cd ../pictures <-- while you are in ~/music directory

```

---

### Post by Scintillement on 2006-07-22
> **taurus said:**
> They can go anywhere you in your home directory but personally, I would seperate them.  Open a terminal and create those directories as

```

mkdir ~/movies ~/music ~/pictures

```
Then, store your movies in ~/movies, your music in ~/music, and your pictures in ~/pictures...

Good idea. At first I was baffled by what the "~/" was so I put it in a terminal and saw it was a shortcut to my home. ^_^. This place is indeed very helpful.

Thanks.

---

### Post by SteveHoffmanUK on 2006-07-22
Taurus is right, of course.

From one newbie to another, if you'd rather do it as you would in Windows - with the graphical tools - just click on Places, Home Folder, then File, Create Folder, give it a name (eg My Pictures) and you're in business.

Easy!

I never liked the nannyish way that Windows comes with some folders already set up: a bit like buying a filing cabinet and discovering that the manufacturer had already labeled the drawers.:evil:

---

### Post by arkangel on 2006-07-22
with some time you will love linux   :)   

very welcome

---

### Post by taurus on 2006-07-22
so, I almost got you with the ~/ thing, eh!!!  :cool:

---

### Post by Scintillement on 2006-07-22
> **taurus said:**
> so, I almost got you with the ~/ thing, eh!!!  :cool:

Almost, but I read somewhere before I started with all this that it was a shortcut. I just forgot to where.

Thanks all.

---

