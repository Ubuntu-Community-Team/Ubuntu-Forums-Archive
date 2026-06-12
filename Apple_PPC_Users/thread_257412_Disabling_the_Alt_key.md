---
title: "Disabling the Alt key?"
date: 2006-09-14
forum: Apple PPC Users
---

### Post by Sak on 2006-09-14
Hey all,

I'm trying to modify my keyboard layout using xmodmap.  Specifically I'm trying to get rid of the Alt_L key.  I'm using an Apple keyboard, and since Control_L and Alt_L are right next to one another I keep inadvertently killing the xserver whenever I'm editing text - accidentally mashing both Ctrl and Alt while hitting the Delete key.  What I'm trying to do is replace the Left Apple (command) key with the Alt_L key.  Here's my .xmodmaprc file so far:

```
remove mod1 = Alt_L
keycode 64 = Meta_L
keycode 115 = Alt_L
add mod1 = Alt_L
```

At this point I've left the Meta_L keycode setting for emacs, but I'm not set on it.  The problem that I'm having is that the left Alt key still functions normally, even though my output looks like this:

```
sak@demian:~$ xmodmap -pke | grep Alt
keycode 113 = Alt_R Meta_R
keycode 115 = Alt_L
keycode 125 = NoSymbol Alt_L
```

Keycode 115 is the Apple (command) key on the keyboard, and it works fine as an Alt key with these settings.  But then so does the left Alt key as well.  Any suggestions on how I can completely disable the left Alt key so that the Apple (command) key can take over the responsibility?

---

