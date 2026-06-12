---
title: "Kde"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-23
How do I change my desk Ubuntu desk top from GNOME to KDE?

---

### Post by arochester on 2006-09-23
See [http://ubuntuguide.org/wiki/Dapper#How_to_install_KDE](http://ubuntuguide.org/wiki/Dapper#How_to_install_KDE)

---

### Post by aysiu on 2006-09-23
> **arochester said:**
> See [http://ubuntuguide.org/wiki/Dapper#How_to_install_KDE](http://ubuntuguide.org/wiki/Dapper#How_to_install_KDE)
Please do not follow those instructions.

If you *apt-get* KDE, you'll have a really hard time getting rid of it.

Follow these instructions instead:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by haxer on 2006-09-23
OMFG i posted this yesterday please take notice and search!!! [-X

---

### Post by aysiu on 2006-09-23
> **haxer said:**
> OMFG i posted this yesterday please take notice and search!!! [-X
You posted this two days ago: > Ok now i tried Kde finally its really nice i must say but ... how do i make so i can have firefox from Gnome is that possible? You could have easily [searched for the answer to that question, too.](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+install+firefox+kde&btnG=Google+Search)

Stop judging other people for things you're guilty of.

---

### Post by BLTicklemonster on 2006-09-23
Searching these forums isn't the easiest thing to do. One is confronted with hundreds of hits one must go through before one can find an answer (sometimes it's easier, but still, it's a bear).

---

### Post by xpod on 2006-09-23
> Stop judging other people for things you're guilty of.

Well said!

---

### Post by aysiu on 2006-09-23
> **BLTicklemonster said:**
> Searching these forums isn't the easiest thing to do. One is confronted with hundreds of hits one must go through before one can find an answer (sometimes it's easier, but still, it's a bear). In fact, if you search on these forums for the phrase *install kde*, none of the results on the first page are at all helpful.

---

### Post by BLTicklemonster on 2006-09-23
lmao, I was suspecting that thumbnail to bust me, and all the replies to be how to install kde. Sorry I didn't trust you...


but yeah, it's tough. You just got to hang in there. One thing to do for sure is go to advance search and look in the topic title for what you are looking for, then search the how to forums.

BUT, there's another thing. Search ought to have a "specific" button you can click to narrow things down even further. I can post some some reference to kde in ever thread on the forum and really screw things up for average surfing if I took a mind to do it.

---

### Post by aysiu on 2006-09-23
My advice for searching is not to use the Ubuntu Forums built-in search at all.

If you want to find something quickly, just do a Google search of this kind: ```
site:ubuntuforums.org *what I'm looking for*
```

---

### Post by BLTicklemonster on 2006-09-23
For example:

I want a custom icon for a launcher I'm creating. It's not in /urs/share/pixmaps so I figure I can add it, but I don't have permission. So I try chowning it. Chowning, to me, never works the same way twice. I did a How To on creating a desktop launcher with custom icons, and the method for chowning doesn't work any more. Something has changed. Instead, my pixmaps folder has a lock on it, and when I rebooted, my launcher for firefox and streamtuner or whatever don't have icons anymore because they can't be found. So search for anything relating to specifially how to use chown, and see what happens. [http://www.ubuntuforums.org/search.php?searchid=8369790](http://www.ubuntuforums.org/search.php?searchid=8369790) predictably, the first page has no thread dealing with how to use chown, but one of the threads listed might tell me how, but will it tell me how to take over permissions? (I wonder if I can take over persimmons? Nah, rather have greps) anyway, therein lies one of the major problems confronting people who are either first timers or season lurkers.

Yes, I know, someone will invariably state that blah blah blah you gotta blah blah blah because nothing is handed to you on a silver blah blah blah so keep trying and quit blah blah blah whatever.

So go ahead, have at it.

So anyway, here's what you might find, though it wasn't here in the forums: [http://www.ss64.com/bash/chown.html](http://www.ss64.com/bash/chown.html)

what the heck good does that do for the average person who never heard of chown before yesterday? 

rant over, proceed with life. lol

---

### Post by aysiu on 2006-09-23
As a general rule, I don't scold people for not searching. If I think they're being lazy asses, I'll just ignore them and help someone else.

P.S. Never *chown* the /usr/share/pixmaps folder.

---

### Post by BLTicklemonster on 2006-09-23
lol I did  sudo chmod 755 -R /usr/share/pixmaps and got it back to normal, but still, if I do a launcher and try to put an .xpm or .png file as the icon, I can't find them, no matter where I go... unless, hang on, this is probably stupidly easy... Dang. when you go to chose an icon, and browse from /pixmaps, I was expecting to see the icon. doh. you browse to the folder the icon is in, then click on open, and it opens the folder. I feel stupider than normal now.

---

