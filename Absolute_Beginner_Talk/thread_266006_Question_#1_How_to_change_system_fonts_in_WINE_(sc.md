---
title: "Question #1 How to change system fonts in WINE (screenshot for clarification)"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by uncreative on 2006-09-26
HI, I want to set up the fonts in WINE to be exactly like windows (I'm lame) and I need to know how.  I have the MS fonts in the windows/fonts folder but it doesn't seem to be working.  I have made a screenshot

[http://www.spoozer.com/ubuntu/Screenshot.gif](http://www.spoozer.com/ubuntu/Screenshot.gif)

---

### Post by uncreative on 2006-09-27
Maybe this should be in a more advanced forum?  Any takers here?

---

### Post by uncreative on 2006-09-27
Solved my own issue and here's the answer for any future forum searched

To change the system fonts in wine download tahoma32.exe from [here]("http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe")

Open up terminal and type 

```
wine tahoma32.exe
```

And no more ugly font, you get the windows tahoma font for all your WINE needs

---

### Post by bodhi.zazen on 2006-09-27
Nice.

Copy Font from Windows to ~/.fonts or ~/.wine/fake_c_drive/fonts

also see here:

[[color=blue]Make Wine Look Better[/color]](http://ubuntuforums.org/showthread.php?t=142741)

Enjoy.

---

