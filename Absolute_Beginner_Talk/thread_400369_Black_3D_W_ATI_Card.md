---
title: "Black 3D W/ ATI Card"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-04-03
I was recently having trouble installing the ATI Driver for my computer, but JUST got it to install correct. Now when I type
```
~$ fglrxinfo
```
I get all the correct info
```
display: :0.0 screen:0
OpenGL venfor string: ATI Technologies Inc.
OpenGL renderer string: Generic
OpenGL version string: 2.0.6011 (8.28.8)
```
I have an ATI Radeon X600 card. My computer has a 3.4 GHZ Pentium4 HT. 1GB ram. The problem I have now is that all of my 3D screensavers/games come back black. All I see when I load or try to load one is a black screen/window where the picture should be. Any suggestions?

---

### Post by xopher on 2007-04-03
Not really, does this happen with the open-source driver?

And have you tried to update the proprietary driver?

---

### Post by Zuuswa on 2007-04-03
when you do
```
glxgears
```
does it show three spinning gears?  And for fun what is your fps?
```
glxgears -printfps
```

---

