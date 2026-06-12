---
title: "[fluxbox] Slit questions"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2008-03-02
First off WHAT is it, WHERE is it and how do I get it/make it visible?

I installed Fluxbox, all I have is the right-click menu and the bar.   Everyone talks of the "slit" and all the things that it's supposed to do but I SEE NOTHING.

I keep hearing "minimize this to slit, dock this with the slit, configure the slit to do this/that the other thing" yet I seem to be missing something essential here.

Help?  :D

---

### Post by kerry_s on 2008-03-02
the slit is where the dock app's go.these are dock app's->
[http://www.dockapps.org/](http://www.dockapps.org/)

you'll find most of them in the repo, just look with synaptic.

the slit is usually on the right of the screen, but you can put it where you want, check your fluxbox menu. it doesn't show until you actually install something that uses it.

i rarely if ever used the slit when i used fluxbox. about the only app i liked was wmdrawer which is a application launcher, for click happyness/the kids, they hate right clicking to launch things, so i used that for them. there are much better options though, like rox pinboard for icons or idesk.

---

### Post by scottro on 2008-03-02
The slit is primarily for apps designed for WindowManager.  If you poke around fluxbox's site, you can see various slit apps that are available. 

So, suppose you installed some wm (the usual abbreviation for WindowManger--it might have even changed its name to wm by now--by the way, just for clarity, this is *a* window manager that was called WIndowManger (or something similar, to be honest, I 've forgotten) application like a special clock.  You can use the slit to position the clock where you want it on the desktop.  

I don't use it myself, I disable it.  For me, the strength of fluxbox is the keyboard shortcuts.  I like a fairly minimal desktop that I can use to launch an application or terminal.   I can launch a terminal with, for example, the Windows key and a letter, then move it all around the desktop and even to another workspace without having to touch the mouse or move my fingers too far from the home keys.  (That is, the keys where you normally have your fingers when typing.)

For more info on the slit, you can look at [http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html](http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html)

---

### Post by RedSquirrel on 2008-03-02
[http://fluxbox-wiki.org/index.php/Faqs#What_is_the_slit](http://fluxbox-wiki.org/index.php/Faqs#What_is_the_slit)

@scottro: I think you were referring to Window_Maker_. ;)

---

### Post by Epic Plecostomus on 2008-03-02
Ok this is neat.

Now how do I make them persist?  I don't want to have to load them from terminal every session.

I'm guessing there is a config file somewhere?

---

### Post by RedSquirrel on 2008-03-02
> **Epic Plecostomus said:**
> Ok this is neat.

Now how do I make them persist?  I don't want to have to load them from terminal every session.

I'm guessing there is a config file somewhere?
Right. Put the commands in your ~/.fluxbox/startup file.

Be sure to read through the Fluxbox wiki. There is a lot of useful information there:

[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

and check out the Fluxbox man page

```
man fluxbox
```

---

### Post by Epic Plecostomus on 2008-03-02
Awesome.  Have a thankyou thingy.  :)

---

