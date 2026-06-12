---
title: "I am on the verge of just giving up.  How do I remove xpti.dat to install flash?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by mthmchris on 2007-12-14
I've tried almost everything I've seen in these forums.  I use Opera, which I by far prefer over Firefox.  However, Flash just plain does not work.  I still like using Opera, but it was a real pain that Youtube videos wouldn't work.  But I downloaded the next Flash the other week and hooray!  It worked.

For some reason though, Flash came up on my automatic updates, and when I updated it, it reverted back to form.  I tried to download it again, but whenever I try to install it it tells me to remove xpti.dat from the components directory.  Here's the rub: there is no xpti.dat.  I went to the components directory, nothing.  I did the sudo updatedb, then locate xpti.dat, nothing.  It's just plain not there, but it keeps on telling me to remove it!  Is there something that I'm not understanding in the installer?  Maybe I'm just screwing up the path for the plugins for Opera? (I went to the helk forums for Opera and they should be correct).

Help!  I've spent the last 2 hours to try to figure this out, I can't.

---

### Post by kelvin spratt on 2007-12-14
sudo apt-get remove --purge flashplugin-nonfree

try this first

---

### Post by Irony on 2007-12-14
To get rid of xpti.dat go to;

```
~/.mozilla/firefox/xvjfje5yd.default
```

and locate the file and delete it (note the number xvjfje5yd is different for you).

Before you actually install go to;

```
~/.mozilla
```

and delete the plugins folder.

On installing flash it will be recreated as will the xpti.dat file - delete the xpti.dat file after installing. It will be re-created again after this but you can just leave it then.

Now go here;

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download option 1 and follow the instructions.

---

### Post by fiskking on 2008-03-02
wow thanks! this helped big time.  was having problems with choppy video (e.g. youtube etc) now running flawlessly so far! thanks again:popcorn:

---

