---
title: "Finally...sound Problem Solution Found!!!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Ricky Yong on 2007-02-14
Go ->Application->Accessories->Terminal
Type "man alsamixer"

This is the manual for alsamixer

Summary
Typed "m" to toggle headphone 
Typed left or right button to select option
or typed Up or Down button to adjust sound level

And there you have it...FRIEND

---

### Post by Crooksey on 2007-02-14
Heh, nice to see when people find a solution for a problem, but was this not fixable through the gnome-volume-mixer ?

You can also run "alsaconf" to configure the sound cards.

---

### Post by Ricky Yong on 2007-02-14
Oh. My God....Something terrible just happened

Now, when i typed "alsamixer" thru the terminal

It returned this error msg

alsamixer: function snd_mixer_load failed: Invalid argument

Pls help....my friend

---

### Post by Crooksey on 2007-02-14
man alsactl

Thats a howto on more advanced options.

---

