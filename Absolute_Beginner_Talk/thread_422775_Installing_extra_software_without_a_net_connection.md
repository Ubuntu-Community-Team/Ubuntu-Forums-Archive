---
title: "Installing extra software without a net connection"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by starbase1 on 2007-04-25
I want to install some extra stuff, buyt I do not have a working internet connection under Ubuntu (yet!). 

Is it possible to download something installable using my old Windows system, then install the package from my memory stick (or something like that).

I'm particularly thinking of getting the required codecs to play MP3 music, and DVD video.

Thanks,
Nick

---

### Post by Cypher on 2007-04-25
Absolutely, if what you are looking for is avaialble as .DEB files, then you can download them and do a manual install on Ubuntu. However, you might find that instead of going back and forth you might want to get your Internet connection running..it will definitely make installing/upgrading packages a breeze..

---

### Post by starbase1 on 2007-04-25
Thanks Cypher, I intend to! I want to switch everything over to wireless, (network, and Internet), which might be quite a bit of work, and if I can just install something to givve me music while I work on it, that would be a great start!

What do I do with the DEB file when I get it? Can I just double click it, or do I need to feed in into some other program?

Nick

---

### Post by Cypher on 2007-04-25
Double-clicking should work, it will start up the necessary programs for installation. If that fails, you can always
```

sudo dpkg -i <file>.deb

```

---

### Post by starbase1 on 2007-04-25
OK, I found the file I wanted, Automatix for Ubuntu 7.04, and saw it was a .DEB file. Downloaded it, tried to run it, got the message it needed Python 2.4

I decided the sensible thing to do was search for 'python' on the drive, in the hope of spotting what version I had, and maybe installing an upgrade. What I had not bargained on was finding references to 2.3 and 2.5 but not 2.4!

I'm not sure which one is active - it would seem silly to include the latest one and not use it though... Mind you, I would have guessed that 2.5 would do everything 2.4 did...

So, how do I tell what version is active?
And how to I go about getting the Automatix package to work?

Thanks,
Nick

---

### Post by mikewhatever on 2007-04-25
Automatix is a nice program to download and install stuff for you over the web, but has no use if no internet connection is available. Going back to your initial post, you can solve the multimedia problems by installing VLC player from its deb file.
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by starbase1 on 2007-04-25
Well, that makes sense - but when I go to the VLC link you kindly provided, I can't see a DEB file I can download and run, just lots of references to online libraries.

Is there a DEB vcersion out there, or something equivalently easy for a newbie with not net on the Ununtu box?

Thanks,
Nick

---

### Post by mikewhatever on 2007-04-25
Yes, no deb file for Ubuntu there. I don't know why they do it, but there seems to be no easy way of installing vlc for you. Sorry for misleading info.

---

### Post by starbase1 on 2007-04-25
Ah well, at least I wasn't missing something obvious!!!
Any other players with built in MP3 support that are eaisly installed?

Nick

---

