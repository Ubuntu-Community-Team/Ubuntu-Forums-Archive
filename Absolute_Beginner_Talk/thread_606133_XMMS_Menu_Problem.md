---
title: "XMMS Menu Problem"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by RSingh on 2007-11-07
I am having a problem with XMMS. Since i have installed it, whenever I right click, there are no menu labels displayed only the shortcuts are displayed. Have a look attached screenshot to see what i mean.

---

### Post by RSingh on 2007-11-20
bump

---

### Post by stchman on 2007-11-20
I have no idea but try completely removing XMMS.

```
sudo apt-get autoremove xmms
```

Also remove your .xmms folder in your home folder.

```
rm -r -f ~/.xmms
```

Also remove any other xmms packages you may have installed i.e. xmms-flac, etc.

After that remove any of the residual configuration in synaptic.

Then re-install XMMS

```
sudo apt-get install xmms
```

Make sure to save any skins you may have downloaded.  Let me know if this helped.

---

### Post by RSingh on 2007-11-21
still the same problem, its like as if only the shortcuts are shown and nothing else:(

---

### Post by indian_gamer2003 on 2007-12-08
Even i have the same problem, feels like its some problem with the font. I have tried uninstalling it three times, also tried xmms2 as well. Anyone else have ideas how to fix this?

---

### Post by tgalati4 on 2007-12-08
It looks like a native language problem.  Do you have "English" set as the native language.  If you made changes to the native language, XMMS may or may not support it.

---

### Post by RSingh on 2007-12-08
well i use english always as the native language. Its sad as i really like this player.

---

### Post by chettyk on 2007-12-16
RSingh, I was having the same problem with XMMS and, like you, this is a player I like a lot. Having a look  the following thread that I found useful in sorting out the problem:

**[ [SOLVED] ugly XMMS menus?! ]("http://ubuntuforums.org/showthread.php?t=627522")**

Good luck!

---

