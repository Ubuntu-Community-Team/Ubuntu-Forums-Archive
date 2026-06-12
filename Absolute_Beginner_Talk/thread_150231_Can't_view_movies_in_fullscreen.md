---
title: "Can't view movies in fullscreen"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Bishop Hill on 2006-03-25
When i start Mplayer, everything is just fine until I prees "F" for fullscreen. Everything around the clip/movie turns black, and the size of the movie remains unchanged.

Why, and how do I fix this?

---

### Post by bored2k on 2006-03-25
[list=1][*] preferences --> video
[*] select xv output
[*] restart mplayer
[/list]

---

### Post by Bishop Hill on 2006-03-25
"Error opening/initializing the selected video_out (-vo) device"

Why>_<?

---

### Post by taurus on 2006-03-25
Try
```

echo "zoom=yes" >> ~/.mplayer/config

```

---

### Post by Bishop Hill on 2006-03-25
Hmm, nothing happends. And I litteraly mean NOTHING, it just shows the daniel@-xxx-xxx-xxx-xxx:~$

---

### Post by taurus on 2006-03-25
[QUOTE=Bishop Hill]Hmm, nothing happends. And I litteraly mean NOTHING, it just shows the daniel@-xxx-xxx-xxx-xxx:~$[/QUOTE]
What you mean nothing?  You just added "zoome=yes" to your ~/.mplayer/config so what do you expect to happen!!!  Now, fire up gmplayer and see if you can play it in fullscreen...

---

### Post by Bishop Hill on 2006-03-25
Will you marry me?

(yes, it worked when I chose the "right" output. Sorry for me being a n00b, but I'm used to that when you type something that works in the terminal, it says something back:P)

---

### Post by taurus on 2006-03-25
[QUOTE=Bishop Hill]Will you marry me?[/QUOTE]
Easy there, tiger...  :oops:

---

