---
title: "Problem with DVD's and videos"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-19
Everything will play fine, but the colours are sooo bright! I can't really explain it well but it's the contrast is incredibly high, and i don't know how to fix this.

---

### Post by EXCiD3 on 2008-01-19
Can you take a screenshot and post it here? Also what hardware do you have and what video player are you using?

---

### Post by Fraser from Scotland on 2008-01-19
I'm using VLC player and I can't take a screenshot it just goes black sorry :( How do i check the graphics card and video card? I'm not sure how to do it.

---

### Post by Ub1476 on 2008-01-19
```
lspci | grep VGA
```

---

### Post by Fraser from Scotland on 2008-01-19
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Ok, that came up, does that help? Help solve my problem lol.

---

### Post by Ub1476 on 2008-01-19
I haven't heard about any colour issues with that graphic controller. Have you tried to edit VLCs settings?

[http://ubuntuforums.org/showthread.php?t=672411](http://ubuntuforums.org/showthread.php?t=672411)

---

### Post by EXCiD3 on 2008-01-19
Do other video players display too bright?

Here is a thread talking about contrast problems when using the i810 graphics driver: [http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915](http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915)

---

### Post by Fraser from Scotland on 2008-01-19
thats it thanks mate :)

---

