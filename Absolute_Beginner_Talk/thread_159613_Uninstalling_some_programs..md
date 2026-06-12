---
title: "Uninstalling some programs."
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-13
I need help to uninstall Firefox, Thunderbird and Opera with ALL their plugins. i.e. all of Macromedia Flash, Shockwave, Adobe Reader, etc. And then install them again one by one.

I think that's the problem that caused my system to freeze in: [http://ubuntuforums.org/showthread.php?p=908385&mode=linear#post908385](http://ubuntuforums.org/showthread.php?p=908385&mode=linear#post908385)

I watched an XVID movie on this PC, listened to many MP3s, nothing happened, then I tried to browse the internet... the system freezed again!

Help please.

---

### Post by Ferri on 2006-04-13
If you installed from the repositories:
```
sudo apt-get remove mozilla-firefox mozilla-thunderbird flashplugin-nonfree mozilla-acroread opera
```
Should do it.
Incidentally, there's no Shockwave for linux.

---

### Post by Amorphous_Snake on 2006-04-13
I installed them from Automatix.

Would it be the same?

---

