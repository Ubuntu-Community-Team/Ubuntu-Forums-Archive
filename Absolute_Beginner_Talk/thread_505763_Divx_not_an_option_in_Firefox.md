---
title: "Divx not an option in Firefox"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-20
I've got videos playing in firefox for stage6, but other sites that link to divx movies won't play.  I found a few posts saying that I need to associate my player (mplayer) with the divx extension in Firefox -> Prefs -> Content -> Manage

How do I get divx to be an option here?

---

### Post by ddrichardson on 2007-07-21
totem-mozilla with all the gstreamer-ugly plugins should sort this out.

---

### Post by dmorand on 2007-07-21
Hmm, I have those installed, but still no divx shown in the content -> manage

---

### Post by dfreer on 2007-07-21
I'm not exactly sure if there is a way to add new file types in there, since the only options are to "Remove" or "Change", which really sucks :( I'm no firefox expert, but you may want to try the Media Player Connectivity Extension for firefox, it has an Divx option. Although getting it configured right can be a pain, it sometimes causes more problems than it is worth. Good luck!

---

### Post by ddrichardson on 2007-07-21
You need the gstreamer-plugins-ugly for divx support. The quickest thing to do is open a divx file in totem from the desktop and the rquired plugins will be offered and downloaded. I did this found only when totem is running as a stand alone application does it ask to download codecs.

---

### Post by Majorix on 2007-07-21
divx is not an extension hence it WON'T show up in that menu.

---

### Post by ddrichardson on 2007-07-21
Very true - I'd forgotten that its wrapped in the avi container format.

---

### Post by dfreer on 2007-07-21
I have several movies with a .divx extension, not .avi (although a vast majority are divx encoded with the .avi extension). That is what I assume the OP is talking about. If it is simply an issue with playing divx encoded movies, than you will just need to install the proper codecs. 
If you are trying to get a plugin to handle playing .divx extensions, that is what I was talking about.

---

### Post by ddrichardson on 2007-07-21
This is a common misconception - although a little mute as the user seldom sees a difference, but avi and divx are two different container formats. However divx containers are partly backwards compatable with avi.

divx can carry a lot of other information that avi cannot.

---

