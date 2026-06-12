---
title: "Serious media/mp3 issues."
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Zully Quirke on 2006-09-23
Since I've had Ubuntu, I haven't been able to figure out a way to make my mp3's play on anything besides VLC. Every other media player tells me that it doesn't recognize my mp3's as mp3's. Okay, so I try to use the VLC playlist -- for some reason every time I try to edit the playlist in VLC, VLC freezes. The music will keep playing, on repeat, but the window is frozen. And won't close. I have to actually reboot my entire PC to try again.

Also, I'm having difficulty with my CD/DVD drives. It doesn't even recognize that I have a second CD-ROM drive, and for some reason Ubuntu will only recognize my DVD-RW as a DVD-ROM. It'll play a DVD that's been burned and closed but it won't open anything that's on a DVD-RW.

---

### Post by PPAAUULL on 2006-09-23
OK for mp3s you can use Automatix to get the codecs. or you can get them manualy. that should fix that problem.

---

### Post by benuski on 2006-09-23
Have you gone to the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page and installed all the necessary codecs for mp3s and the w32codecs?

---

### Post by happy-and-lost on 2006-09-23
You might need some codecs.

```
sudo apt-get install w32codecs
```

---

