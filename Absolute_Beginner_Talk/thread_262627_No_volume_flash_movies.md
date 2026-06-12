---
title: "No volume: flash movies"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by braheem on 2006-09-21
anyone have any ideas, volume works for everything except google and youtube movies.

---

### Post by Qrk on 2006-09-22
The linux version of flashplayer uses the outdated OSS sound daemon. Just about every other sound uses the ASLA sound daemon now, as it actually works. 

One of OSS's problems is that it cannot play multiple sounds at once. Perhaps you have a program that uses OSS for sound that is blocking flashplayer? XMMS can do this. You may want to see if the system-monitor shows any open applications that might be using the OSS sound daemon. mplayer likes to run after you have closed it. 

If nothing sticks out at you, logging out and then logging back in again.

---

### Post by dmichaels on 2006-09-22
what about sound being off? my sound is way off. how do i fix that?

---

### Post by Qrk on 2006-09-22
I'd just make sure that no other app that uses OSS is running. That  is an easy fix, if it works. 

Of course, the problem might lie elsewhere. If you configure a program to run using OSS, do you get sound on it?

---

### Post by liquilife on 2006-09-25
I am having the same issue as well. All I've got running is Swiftfox and no volume for any flash application works.

---

### Post by xpod on 2006-09-25
Try this mabey?

[http://ubuntuforums.org/showthread.php?p=311733#post311733](http://ubuntuforums.org/showthread.php?p=311733#post311733)

---

