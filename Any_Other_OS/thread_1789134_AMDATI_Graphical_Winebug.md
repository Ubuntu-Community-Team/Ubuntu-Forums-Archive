---
title: "AMD/ATI Graphical Winebug?"
date: 2011-06-23
forum: Any Other OS
---

### Post by 8bitpalace on 2011-06-23
Hey Peeps!

First of all, I'm using Linux Mint. All though, since ubuntu and mint are very alike, I thought a post on either forum wouldn't hurt.

I don't know if my problem is more suited for WineHQ, but anyways;
I've recently been trying to install and get Hitman Blood Money working through wine 1.3.22. I got the game working properly, it runs smooth when overriding some .dll files and also emulating sound through wine. The problem is that there's no characters in the game itself, no player models. They're all invisible, including Hitman. After fiddling around with different versions of Hitman Blood Money, wine and several graphical settings I've not yet found a solution to the problem. 

I would be glad if anyone has some ideas regarding the problem, I think it all lies in my ATI Radeon graphic card.

---

### Post by Perfect Storm on 2011-06-23
Moved to Other OS/Distro Talk.

---

### Post by 8bitpalace on 2011-07-03
Problem solved. 

The ATI's GLSL was doing this "invisible bug" to several games running through wine. For me those games were Hitman Blood Money, Counter-Strike Source and Left 4 Dead. All moving objects/characters were invisible until I disabled GLSL.

For those encountering the same issue, or are interested in how to disable GLSL overall:

1. Type "wine regedit" in a terminal (without the quotes) to open up wine regedit. 

2. Now go to HKEY_CURRENT_USER\Software\Wine\Direct3D

3. Add the string "UseGLSL" (Without the quotes, and remember, it is case sensitive). The value of the string should be "disabled".

Thanks to this document at WineHQ for helping me figure this all out: [http://wiki.winehq.org/DirectX-Shaders](http://wiki.winehq.org/DirectX-Shaders)

---

