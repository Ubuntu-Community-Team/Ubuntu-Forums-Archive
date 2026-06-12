---
title: "No sound!"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-01
Hi, i have an Acer Aspire 9303WSMi with Ubuntu Studio 7.04 and the speakers won't work (the speakers built in the computer) 
No i don't know what sond card i have :(

How do i get sound, it only works if i use head phones

---

### Post by rillip on 2007-06-01
If headphones are working, it's not an OS issue, as it's recognizing your sound card.  Support for the speakers shouldn't be neccessary, they don't have any drivers or anything.  Do you have the volume turned up on the speakers?  Do you have the volume turned up in the OS?  The volume slider is accessable from the mixer, in KDE it's in the lower right with your clock, just like in Windows.

---

### Post by TwistesdTexan on 2007-06-01
Try double clicking the speaker icon and adjusting the different levels in the mixer. On my computer the PCM also acts as a Master volume control.

---

### Post by ajmannen on 2007-06-01
[[img]http://bildr.no/thumb/71452.jpeg[/img]](http://bildr.no/view/71452)

Still not working

---

### Post by zvacet on 2007-06-01
First column is master.

---

### Post by Sparkster185 on 2007-06-01
If you type
```

lspci -v | less

```

You can scroll down until you find your sound card make/model.  If you have an Intel HDA card, I think I might have the fix for you.

---

### Post by ugm6hr on 2007-06-01
Look here:
[http://ubuntuforums.org/showthread.php?t=459360](http://ubuntuforums.org/showthread.php?t=459360)

Hopefully turning on surround will help.  You need to access from alsamixer in Terminal

---

