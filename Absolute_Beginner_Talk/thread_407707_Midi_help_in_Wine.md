---
title: "Midi help in Wine"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by BraggPxnk on 2007-04-12
I recently bought Tabit (a music writing software that uses midi), and ran it on Wine.  I can put notes in the window, but it won't play any songs.  It says that there are no midi devices installed on the machine.  

I insatlled Timidy, but that doesn't seem to work either.  

Any help?

---

### Post by ajmorris on 2007-04-14
> **BraggPxnk said:**
> I recently bought Tabit (a music writing software that uses midi), and ran it on Wine.  I can put notes in the window, but it won't play any songs.  It says that there are no midi devices installed on the machine.  

I insatlled Timidy, but that doesn't seem to work either.  

Any help?

Do you have sound at all with wine?
in a terminal (Applications >> Accessories >> Terminal) type : ```
winecfg
```

Go to the sound tab in the dialog box that appears, and see if you have sound

---

