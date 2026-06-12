---
title: "Instant searches"
date: 2010-11-28
forum: Apple Hardware Users
---

### Post by rmcellig on 2010-11-28
I am used to doing very fast searches on the Mac. When I type into the search box in any finder window, the search results present themselves as I type. I am looking for the same functionality in Ubuntu. I tried Catfish but it doesn't have the speed I see on the Mac.

Is there a way for me to index my drives so that searches are instantaneous, or are there any options I haven't explored yet?

---

### Post by conradin on 2010-11-28
Use the loacte command. This command uses an index. if youre looking to find something you made since your last boot, you might have to tell the locate to update. You can use catfish if youre not happy with the terminal. 

ooh and you'll love when BtrFS comes out, it promises any file can be found in 6 steps or less.

---

### Post by chaanakya_chiraag on 2010-11-28
Also, Kupfer is kinda like Quicksilver for Mac.  Check it out at:
[http://kaizer.se/wiki/kupfer/](http://kaizer.se/wiki/kupfer/)

---

### Post by DZ* on 2010-11-29
Google desktop shows results as you type, see an illustration on their site, [http://desktop.google.com/linux/](http://desktop.google.com/linux/)

There are a number of other programs for fast searches inside files. 

Tracker and Beagle show results as you type. Both integrate with Nautilus meaning that you can invoke tracker or beagle search when you type in nautilus search box. AFAIK, Nautilus will use Beagle if it is running, otherwise it will use Tracker. Beagle project seems to be nearly abandoned though.

KDE comes with desktop search preinstalled, accomplished by the the evil trio, strigi/nepomuk/virtuoso. You may have to enable it through "System Settings". Then you can type stuff to search for in the file browser Dolphin. It also works in Konqueror browser, using "nepomuksearch:/SEARCH-STRING" or nepomuksearch:/hasTag=SOME-TAG" interface. Have to hit Enter though (no "as you type" capability).

One really impressive desktop search program is recoll, but again, no "as you type", gotta hit Enter. Among other things, it can search within attachments of locally stored emails (I only tested it with offline IMAP directories of Kmail).

---

### Post by rmcellig on 2010-11-29
What is BtrFS?

---

