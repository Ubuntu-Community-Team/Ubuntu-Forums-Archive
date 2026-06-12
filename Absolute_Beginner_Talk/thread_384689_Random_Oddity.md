---
title: "Random Oddity"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-03-14
Ever since I began testing Edgy on my laptop it always bothered me that the Windows shortcuts in FireFox didn't work in Ubuntu. Well sure enough today I finally got around to poking around at it. Seems as though they should work (e.g. alt+back arrow = 'back'). On my laptop there are two alt keys, one on either side of the spacebar. Usually I use the one on the right since it is closer to the arrow keys. I tried the one on the left. It worked! They all worked. In a similar way that I have two alt keys, I have two ctrl keys (again, either side of the space bar). I tested some things with them, and they both seem to work the same. But here's what gets me: both alt keys work when I boot into Windows!

Anyone else have this particular oddity? (Or other random things they may have noticed along the way)

---

### Post by Belyel on 2007-03-14
I think this is due to the way keyboards are actually recognized by an OS.  In windows, an Alt key is an Alt key, but when you push the right alt, it sends a different number code than a left alt.  Linux recognizes this and, probably due to some convention, does not by default do the same action for both alt keys in some cases.  This does allow a greater number of shortcuts, but if you're used to the windows way of "an alt for an alt," you may have to relearn some of them. 

You can look at what they keycodes are (if you are interested) by typing xev into a terminal window.  Then press buttons and look at the output.  I think on my comp (and US keyboards), right control is key 107 and left control is 34  or something.  YOu can use these to map different commands to those keys if you so choose, but that's a more advanced topic.

---

### Post by annda on 2007-03-14
as a not-exlusively-English-language person, i rely on the "right Alt key" to be a medium that alllows entering non-standard characters with a standard (US/English) keyboard. in case you are interested in the background, here it is:
[http://en.wikipedia.org/wiki/Alt_Gr](http://en.wikipedia.org/wiki/Alt_Gr)

---

### Post by nonpareilpearl on 2007-03-14
concerning xev: THAT IS SO COOL!
concerning non-English characters: I've never seen that before, when I was younger (12-13) and we finally upgraded from our Apple IIgs to a Windows 98 Gateway PC I discovered ASCII codes quite by accident and then noticed a trend. I made a word document (which I still have) that is about 5 - 8 pages (I can no longer remember: the most commonly used ones I just do without referencing) long. Mostly for Spanish and Latin though ^.^

---

### Post by H.E. Pennypacker on 2007-03-14
I have this same problem, and it drives me nuts.  Ah, I'll have to fix it some other time.

---

