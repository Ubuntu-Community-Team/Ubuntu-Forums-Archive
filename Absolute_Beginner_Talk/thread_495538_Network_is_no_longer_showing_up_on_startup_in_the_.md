---
title: "Network is no longer showing up on startup in the tray area"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Dennis123 on 2007-07-08
Yesterday, I've just-for-fun-clicked on the network icon(KDE) to see, what is there all around, but then I've seen something with ...on startup, where I've clicked at, too. What happend then, is that anfter the next reeboot this icon is no longer there where it should be. Don't misunderstand me, I'm not addicted to a tray icon, but another impact of the absence of this icon is, that the internet is no longer working at all. I'm currently writing from outside my (K)Ubuntu VM and would really like to use the internet again. I think I hae to correct some startup settings. But I don't now where!
Has anybody any suggestion of any kind for improving my overall internet experience on the system?

---

### Post by walkerk on 2007-07-08
```
nm-applet --sm-disable
```

that fix it?

---

### Post by Dennis123 on 2007-07-08
Oh obviously yes,
thanks for that fast response

---

### Post by walkerk on 2007-07-08
no problem.. make sure to run it using alt-f2 ..otherwise it'll close when you close the terminal window..

---

### Post by Dennis123 on 2007-07-08
Oh that happened just one minute ago...

---

