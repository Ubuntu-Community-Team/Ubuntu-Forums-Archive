---
title: "Sound for other programs will not work if Rhythmbox is open"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by Nyeh on 2008-04-26
Running Hardy on a 2nd gen 15" MBP. If i open Rhythmbox up and start something playing, other running programs will not have functioning sound i.e. notifications in Kopete, youtube videos.

If I run a different program before Rhythmbox, when I do decide to play music, I cannot and get an invalid stream error.

---

### Post by Rog-Mahal on 2008-04-26
I've had a similar problem. I think it has something to do with alsa and gstreamer, perhaps you can only have one pipe open at a time? I will do some research.

---

### Post by cyberdork33 on 2008-04-26
it sounds like a conflict with whatever sound daemon is used.

---

### Post by Nyeh on 2008-04-27
> **cyberdork33 said:**
> it sounds like a conflict with whatever sound daemon is used.
Forgive me, but I am relatively new and don't quite understand how I could diagnose and/or fix this.

---

### Post by cyberdork33 on 2008-04-27
> **Nyeh said:**
> Forgive me, but I am relatively new and don't quite understand how I could diagnose and/or fix this.
nor i really... It sounds like a bug though, so I would file a bug report for Ubuntu in launchpad against rhythmbox. Hopefully someone there with more technical knowledge can guide you.

---

