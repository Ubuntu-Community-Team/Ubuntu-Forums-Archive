---
title: "ogg file type?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-09
I've captured some video from my desktop with the program gtk-recordmydesktop, but the filetype it makes is called ogg and i can't play them. Is there a way to convert them or a better program for doing this?

---

### Post by sailor2001 on 2007-07-09
download a VLC player........this player can be downloaded in windows also

---

### Post by czepluch on 2007-07-09
> **sailor2001 said:**
> download a VLC player........this player can be downloaded in windows also

I've got VLC but it doesn't play the  ogg file?

---

### Post by Malibu Illusion on 2007-07-09
```
sudo aptitude install libtheora0
```

Will play just fine in Totem.  OGG is a fully open standard.

---

### Post by czepluch on 2007-07-09
> **Malibu Illusion said:**
> ```
sudo aptitude install libtheora0
```

Will play just fine in Totem.  OGG is a fully open standard.

Still can't play any? I want to capture video of my screen as it is, because i'm trying to make a guide for one of my friends.

---

### Post by czepluch on 2007-07-09
> **czepluch said:**
> Still can't play any? I want to capture video of my screen as it is, because i'm trying to make a guide for one of my friends.

Is there another and better program for doing that ?

---

### Post by czepluch on 2007-07-09
> **czepluch said:**
> Is there another and better program for doing that ?

bump

---

### Post by scxtt on 2007-07-09
totem (2.16) has a bug that doesn't allow it to play ogg (audio) files w/ xine-lib 1.1.3/1.1.4 -- even tho other xine-based players can ...

[http://bugs.gentoo.org/show_bug.cgi?id=161372](http://bugs.gentoo.org/show_bug.cgi?id=161372)

try: **sudo aptitude install xine-ui**

---

