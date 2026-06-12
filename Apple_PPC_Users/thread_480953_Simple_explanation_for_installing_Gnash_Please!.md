---
title: "Simple explanation for installing Gnash? Please?!"
date: 2007-06-22
forum: Apple PPC Users
---

### Post by TonySmash on 2007-06-22
I've tried installing gnash many times, and each time I apparently fail, because Firefox NEVER recognizes it. I've followed the instructions on the PPC FAQ and in other places, and finally I've just given up and come back here. So please, if someone could give me SIMPLE step-by-step instructions for installing gnash (preferably the new one with YouTube support), that would be AMAZING.

ALSO - how do I remove any old or bungled up versions of gnash? I want to do this as cleanly as possible...

THANKS IN ADVANCE!!!

---

### Post by stmiller on 2007-06-22
Install these gutsy packages:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by TonySmash on 2007-06-22
EDITED:: ignore everything that was previously here about me being dumb and not knowing how to install packages.

NEW MESSAGE:: aight, so i've downloaded the PPC versions of each of the packages (except the konqueror one, i dont use konqueror). however, when i open them, i get this message in the package installer:

ERROR: Dependency is not satisfiable: libc6

so...thats a bad thing right? is this just because i have feisty and its trying to install a gutsy package?

help?

---

### Post by stmiller on 2007-06-23
Okay, just edit the file

/etc/apt/sources.list

sudo gedit /etc/apt/sources.list

and change every 'feisty' word to gutsy

Then type

sudo apt-get update

then

sudo apt-get install gnash

Then change the apt source list file back to feisty as it was, and do a

sudo apt-get update

---

### Post by TonySmash on 2007-06-25
thanks stmiller! this worked well. youtube playback is kinda buggy (theres lines across one side of the video) but otherwise its good.

---

### Post by stmiller on 2007-06-25
Looks like gnash 0.8.0 is going to be in Feisty backports soon. So easy install for everyone very shortly. :)

---

### Post by aantn on 2007-06-27
> **stmiller said:**
> Looks like gnash 0.8.0 is going to be in Feisty backports soon. So easy install for everyone very shortly. :)

Nice!:p

---

### Post by Mark76 on 2007-07-01
I followed the instructions and all I get is a grey youtube screen :(

---

### Post by joninkrakow on 2007-07-02
Ha ha...

I did that, and guess what I forgot to do after? Yup, switch everything back to feisty... and then, on the next boot, forgetting I had done that, let the system update 600 files! Now my install is hosed. I'm currently booted using the "old" option at boot, which seems to be an older version of Ubuntu, but I don't know what! My fonts are messed up, and some other things, but oddly enough, my theme is fine, as are my other prefs. the downside is, of course, booted this way, I cannot update my system, and I can't figure out if there's a way to "undo" the update!

So.... for now, at least, I'm downloading the gutsy CD, and will try updating to that. If that fails, a reinstall--saving what I can from my home directory first--and trying to "save" my current user on install. Obviously, the "gutsy" update would be preferred, but I don't know if that will work.

If anybody has any ideas before I do so, I eagerly await your replies. ;-)

-Jon

---

