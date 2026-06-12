---
title: "Keyboard problems with Apple sli alu keyboard and Mac Mini (3rd gen)"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by lastchancetosee on 2010-01-08
Hi.
I've very successfully installed Ubuntu 9.10 on my MacMini, but continue to have problems with the Apple Keyboard.

I've already solved the problem with switched keys (^ and < in the german layout) and changed the behavior of the F-Keys by setting "options hid_apple fnmode=2" in /etc/modprobe.d/hid_apple.conf . I've also switched the left "cmd" and "alt" keys via keyboard preferences.

What remains is:

- Ctrl does not work (Ctrl+t for new tab results in 't' being typed etc.)
- Alt, Cmd in combination with most non-character keys results mostly in weird characters (like A,B,C,D for alt/cmd+left,right,up,down)

any ideas?

[edit: I just noticed: Sound does not work, either]

---

### Post by linuxopjemac on 2010-01-08
for sound you might want to first have a look if some of your channels are not muted with alsa-mixer. If this is not the case, I suggest you to try the backported alsa-module:

```
aptitude install linux-backports-modules-alsa-karmic-generic
```

If that does not work, we can tweak the alsa configuration file later...

---

### Post by lastchancetosee on 2010-01-12
The sound problem is fixed now, thank you very much.

I found out what caused the problem with the Control key, my .xmodmap for correcting the switched keys was apparently the culprit. There was some left-over stuff from things I tried before in there. I deleted everything that wasn't strictly needed and now it works.

If I have a moment I'll try and figure out what exactly broke it.

---

### Post by linuxopjemac on 2010-01-12
If you like, you can write an installation report about your particular machine on my website [here]("http://mac.linux.be/forum/9").

---

