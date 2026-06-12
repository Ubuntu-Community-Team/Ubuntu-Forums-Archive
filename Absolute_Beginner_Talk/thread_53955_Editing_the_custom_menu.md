---
title: "Editing the custom menu"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2005-08-02
I figured out how to add stuff to panels and whatnot, now I just need to figure out how to edit the custom menu? I want to replace Rhythmbox with XMMS, and remove some other things I will probably never use to clean up the menu a bit, but I can't find  how to do this

---

### Post by bored2k on 2005-08-02
[QUOTE=OttoDestruct]I figured out how to add stuff to panels and whatnot, now I just need to figure out how to edit the custom menu? I want to replace Rhythmbox with XMMS, and remove some other things I will probably never use to clean up the menu a bit, but I can't find  how to do this[/QUOTE]
 You need SMEG
[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by OttoDestruct on 2005-08-03
Ok... heres what I get...

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg
```

I did the thing in the Ubuntu guide about adding the other repositories, as well as doing a sudo apt-get update

---

### Post by KingBahamut on 2005-08-03
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Check your repository listing, and retry. 

Backports has Smeg on it.

---

### Post by OttoDestruct on 2005-08-03
Aha that worked. Turned out I had everything but backports.

---

### Post by Gnobody on 2005-08-03
[QUOTE=OttoDestruct]Aha that worked. Turned out I had everything but backports.[/QUOTE]
 I'd recommend beep-media-player instead it is a newer fork of XMMS that has gtk2 support.

---

### Post by OttoDestruct on 2005-08-03
[QUOTE=Gnobody]I'd recommend beep-media-player instead it is a newer fork of XMMS that has gtk2 support.[/QUOTE]

I just might do that. Do XMMS skins still work on it?

---

### Post by bored2k on 2005-08-03
[QUOTE=OttoDestruct]I just might do that. Do XMMS skins still work on it?[/QUOTE]
 Yes.

---

