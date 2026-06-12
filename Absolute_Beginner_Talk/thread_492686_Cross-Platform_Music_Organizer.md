---
title: "Cross-Platform Music Organizer"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-07-05
I'm looking for a way I can share music between Windows and Ubuntu. Doesn't necessarily have to be the same program, but I do want to be able to sync the ratings information. Does such a thing exist?

---

### Post by cleverselfreferentialname on 2007-07-05
Easiest way I can think of off the top of my head is to use the same program in both OSes and have a symlink to the Windows profile where the Linux profile should be. By that I mean if you had, for example, firefox, you would symlink .mozilla to /media/windows/Documents and Settings/Username/Application Data/Mozilla/Firefox (I think, I don't remember the windows path).

Like this:

ln -s "/media/windows/Documents and Settings/Username/Application Data/Mozilla/Firefox" .mozilla

and .mozilla becomes a redirect to that file on the windows drive, assuming your windows partition is mounted as /media/windows.

Only issue is that I cannot think of a good cross-platform music player. Songbird looks beautiful but isn't quite there yet. Amarok only works beneath Cygwin as far as I know, and I'm not sure if that's an acceptable solution for you.

---

### Post by Raptor45 on 2007-07-05
Its not a matter of sharing the files themselves, its a matter of sharing the ratings information.

Has no one come up with a way of doing this?

---

### Post by Raptor45 on 2007-07-06
bump

---

