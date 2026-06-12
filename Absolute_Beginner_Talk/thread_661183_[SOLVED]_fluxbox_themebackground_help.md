---
title: "[SOLVED] fluxbox theme/background help"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-07
Hi, I do not understand how to install themes in fluxbox, feeling a itte overwhelmed I decided to start on just changing my background but everywhere I look online it says to edit ~/.fluxbox/startup but I don't have that file. In that directory I only have fburn_history init keys menu and slitlist 

can someone help me eaither learn how to install a theme or background or both. Oh yea I'm using fluxbox 1.0.0

---

### Post by bodhi.zazen on 2008-01-07
There are several ways to set the background. 

You can use 

fbsetbg /path/to/image

See also here : [http://community.fluxbuntu.org/index.php?&topic=98.0](http://community.fluxbuntu.org/index.php?&topic=98.0)

There is a thread here on setting a style : [http://ubuntuforums.org/showthread.php?t=659806](http://ubuntuforums.org/showthread.php?t=659806)

And a thread here on Menu : [http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

And How to style : [http://www.tenr.de/howtos/style_fbox/style_fbox.html](http://www.tenr.de/howtos/style_fbox/style_fbox.html)

---

### Post by vrillusions on 2008-02-22
Wanted to add something since I found this in a search.  I was having a problem with the theme overriding the background.  So here's how to get around that.  In short you copy the theme to your ~/.fluxbox/styles folder and remove the line changing the background.

In more detail, using the "operation" theme since that's what I'm using at the moment :)
```
mkdir ~/.fluxbox/styles
cp -R /usr/share/fluxbox/styles/Operation ~/.fluxbox/styles/Operation-nobg
```

Use your preferred editor and go down to where you see a line that starts with rootCommand and place a # in front of it.  Restart fluxbox and the new style should be there.  Then use your preferred way of setting the background (i used ~/.fluxbox/startup file) and it will be set.

---

