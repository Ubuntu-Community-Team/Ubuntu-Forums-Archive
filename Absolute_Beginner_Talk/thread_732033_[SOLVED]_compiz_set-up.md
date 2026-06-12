---
title: "[SOLVED] compiz set-up"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Wolfan on 2008-03-22
I hope that someone can help me.  I think I'm confused about setting up compiz.  I want to set up screen zooming.  I found that compiz was already installed and then installed the compiz settings menu.  I've clicked a few of the options and then looked at what should start screen zooming,  According to the Action tab it's Super(which I'm told means WinKey)+the third mouse button, then you should be able to just do Super+MouseScroll to zoom.  This is not working for me, neither are another of the other options that I set up.  (Like desktop effects, such as the infamous cube).  I have tried restarting as well. So is there something I'm supposed to enable that is not apparent in order to have these settings take effect.

Thanks in advance

P.S. I followed the steps along with [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

---

### Post by jan quark on 2008-03-22
what is your graphic card?
are you able to enable the effects going to 
system > preferences > appearance > visual effects > extra ?

---

### Post by Wolfan on 2008-03-22
I have an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] according to lspci, 

when I go to the menu you mentioned (which I didn't know about before) I get the error "The Composite extension is not available"

---

### Post by jan quark on 2008-03-22
this should work ( it worked for me)

install this package
```

sudo apt-get install xserver-xgl
```

and then during the login change the session to xclient
now you should be able to activate the effects

---

### Post by Wolfan on 2008-03-22
A million thanks, that did the trick.  Now I set it to extra screen effects and all things are working well. Could you possibly explain what I did, for eample what is a session?

---

### Post by jan quark on 2008-03-22
good to hear :)

 Each time you logon to Ubuntu you are creating a "session."
this is a set of applications which are loaded.

compiz needs a platform to perform the graphical stuff it does :) (I have no idea )
and the xclient is this platform

as I said I know it works but why... that is another question

---

### Post by Wolfan on 2008-03-22
:-) thanks much

---

