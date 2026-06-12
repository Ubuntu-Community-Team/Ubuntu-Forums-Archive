---
title: "Path to MPlayer"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by MarkoGT3 on 2008-04-17
The program I'm using opens my file browser and tells me to "select the path to MPlayer". Where is this? :confused:

Any help would be much appreciated.
Thanks,
Marko

---

### Post by otrojake on 2008-04-17
In the terminal type this:

```
whereis mplayer
```

That should tell you where it is.  My guess is it's "/etc/mplayer"  If it doesn't show you a path, it's not installed.

---

### Post by unutbu on 2008-04-17
```

% which mplayer
/usr/bin/mplayer

```

---

### Post by MarkoGT3 on 2008-04-17
I installed it and have located the path at /usr/bin/mplayer
However, it's not letting me select it. Note mplayer's the one at the top of the window:

[IMG]http://i268.photobucket.com/albums/jj3/marko4x4/Screenshot-MPlayerPath-1.png[/IMG]

Edit: I don't get this. It's not letting me select any files but folders... So how am I supposed to select the path?? I'm using iriverter btw.

Hmm, perhaps I can't select it because it's only accessable by root. How do I de-rootify a program?

---

