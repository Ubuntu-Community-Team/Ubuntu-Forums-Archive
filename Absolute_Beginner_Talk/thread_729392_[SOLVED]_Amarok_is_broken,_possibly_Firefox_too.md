---
title: "[SOLVED] Amarok is broken, possibly Firefox too"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by thedaylights on 2008-03-19
Hi! I recently tried to add support for my Creative Zen mp3 player to Amarok by following the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=662567](http://ubuntuforums.org/showthread.php?t=662567)
Well, Amarok is broken now. It has no collection (i.e. no song library), and as with many others on that thread I think I'm in "dependency hell". Needless to say, it doesn't work with my Zen either. I've also noticed Firefox started to misbehave after this experiment - some pictures do not display, and some pages require a reload to load up.

How do I get back to a normally functioning Amarok and Firefox? Surely I don't have to reinstall my entire OS? I was hoping I left that brute force attack behind with Windows.

Help? :confused:

---

### Post by spiderbatdad on 2008-03-19
It doesnt look like it would be too hard to work your way back out. The files you were instructed to install are contained in your home/username/libmtp directory.
seems like you could start by deleting that stuff.
remove amarok, amarok-xine, and amork-gstreamer,
then reinstall them, using sudo apt-get install ...
the dependencies should be installed automatically.
just to make sure, after you're done, try to
sudo apt-get install libmtp6
"                         "   libmtp-dev

good luck.

---

### Post by thedaylights on 2008-04-02
So after several days of letting my system magically regenerate following the reinstall, things have started to work again. I can even use my Creative Zen V mp3 player with Amarok, which is really surprising. Ah, the magic of updates. Thanks for the responses everyone!

---

