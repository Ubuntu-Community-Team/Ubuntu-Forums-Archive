---
title: "totem movie player"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Strongbad on 2005-07-24
I'm having a little trouble with totem player. every time I try to open the program I get this message: "Totem could not start. Resource busy or not available." I'm no sure what that means, but it started right after I installed a new graphics card.

-Strongbad-

---

### Post by poofyhairguy on 2005-07-24
[QUOTE=Strongbad]I'm having a little trouble with totem player. every time I try to open the program I get this message: "Totem could not start. Resource busy or not available." I'm no sure what that means, but it started right after I installed a new graphics card.

-Strongbad-[/QUOTE]

Try gxine. My fav.

> sudo apt-get install gxine

---

### Post by Jason-X on 2005-07-24
I can never get Totem to work properly.

Try VLC. this works well for me.

**sudo apt-get install vlc**

I use Gxine as well. Both are good.

---

### Post by Strongbad on 2005-07-24
Where can I get ether of those?

-Strongbad-

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Strongbad]Where can I get ether of those?

-Strongbad-[/QUOTE]

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Do that. Then enter these commands in the not root terminal:

> sudo apt-get update

> sudo apt-get install w32codecs gxine vlc

---

### Post by Strongbad on 2005-07-25
I got this error message

E: Couldn't find package w32codecs

-Strongbad-

---

### Post by Mr. Electric Wizard on 2005-07-25
I started using VLC instead of MPlayer or Totem (for files on my box, or my network), and I am much happier...

---

