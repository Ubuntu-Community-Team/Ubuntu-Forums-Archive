---
title: "Cant write to mp3player"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Arwen on 2007-07-20
Hello everyone!
When I plugged in my usb mp3player device it opened automatically with Rythmbox and everything seemed ok.The problem is that I cannot add songs because "this disc is read-only",however I can delete files in the mplayer without problem..I still have the same problem even with root priveleges..Does anyone know what's going on?

---

### Post by VoiceOvGod on 2007-07-20
Sounds like permissions.

You may need to chmod it.

Assuming you are in the directory above the mp3 player, what does this show?

```


$ ls -l


```

---

