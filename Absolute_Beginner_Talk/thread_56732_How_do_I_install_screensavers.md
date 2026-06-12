---
title: "How do I install screensavers?"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-08-13
This may seem like a dumb question, but I really have Googled for this, and I haven't found much. I'm not that big a fan of screensavers in general, but I think if I had a really cool one, I might actually use it.

I noticed that in System > Preferences > Screensaver there 

1. are a bunch of screensavers listed but blanked out. How do I add those?
2. is no way to add or install screensavers.

I did download a screensaver called xpenguins as an .rpm, and I tried using alien to install it. It appeared to install correctly, but now I don't know how to invoke it.

I also went to Synaptic (and I have all the extra repositories enabled) and searched for *saver* in both name and description, and I have everything installed that isn't KDE.

Any ideas?

---

### Post by wvslkr on 2005-08-13
See if this helps.   [http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/)       Doc and Faq page.

---

### Post by aysiu on 2005-08-13
[QUOTE=wvslkr]See if this helps.   [http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/)       Doc and Faq page.[/QUOTE] No. That was one of my first stops on my Google search, believe me. It says nothing about installing new screen savers. Any other ideas?

This isn't a big deal, since--as I said before--I don't even really like screensavers, but it's probably not a bad idea to know how to install a new one if I find one that's good...

One thing I did discover is GLSlideshow, which is nice... I don't mind cycling through some photos of family and friends as a screensaver.

---

### Post by wvslkr on 2005-08-13
I really don't know either.  What i gathered from skimming through some of the docs any new  ones would be added to the others.  I believe the location is /usr/share/xscreensaver/config.  

Then again I may be totally wrong.  I am only guessing.  Hope someone jumps in.

---

### Post by aysiu on 2005-08-13
[QUOTE=wvslkr]Then again I may be totally wrong.  I am only guessing.  Hope someone jumps in.[/QUOTE] Thanks for trying to help. If no one else jumps in, that's fine. This isn't an operation-critical task. It would just be cool to know how to do.

---

### Post by Sam on 2005-08-14
I don't know if there is a command line or something else to do it, but you can edit the file ~/.xscreensaver to do it.

In the program section add a line like this:
```
-	  "Name displayed" 	command --arguments			    \n\
```

---

### Post by DiscoKiller on 2006-02-06
just had a look around myself.

i found a couple of screensaver i wanted to install. went about simply installing it like u would any other downloaded, archived file. i had noticed that the name of the screensaver (electricsheep) is in the screensaver list greyed out. so once i fathom out how to install it then i`ll be sorted. sadly when i`m using the make install command it is throwing up too many rerors which i`m too tired to read. maybe not that important hehe...


DK

---

