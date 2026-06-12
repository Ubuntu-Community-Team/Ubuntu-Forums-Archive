---
title: "Synaptic broken!?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by whistle on 2007-06-14
So today i tried to install keytouch to get my multimedia keys to work... seems like the package on sourceforge is corrupted.  I downloaded it four times and each time the .deb installer has given me "Could not open 'keytouch_2.3.0-0ubuntu1_i386.deb' The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file. "

So that's one of the problems... the other one is that this also screwed up my synaptic.  I tried to install the same thing from source, and ./configure told me I was missing some headers.  So I went into synaptic to get those, and it spits out "E: The package keytouch needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." so I can't use synaptic to do anything.

Then I try sudo aptitude remove keytouch, and it tells me ```
dpkg: error processing keytouch (--remove): Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.
``` and ```
E: Sub-process /usr/bin/dpkg returned an error code (1) A package failed to install.  Trying to recover:
```

Right now both aptitude and synaptic are broken, plus what I tried to get done before doesn't work (keytouch).  Any ideas?

---

### Post by wormser on 2007-06-14
I am not sure how to solve this but give the following a shot.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

I had an issues with updates once and the update command fixed it.

---

### Post by whistle on 2007-06-14
I tried those two as well as sudo aptitude clean - clean and update worked, but upgrade gave me the same errors of ```
E: I wasn't able to locate a file for the keytouch package. This might mean you need to manually fix this package. (due to missing arch)
``` and ```
E: Couldn't lock list directory..are you root?
``` and I am sudo-ing, and it's prompting me for the password

Is there any way to tell my system that the package isn't actually installed?  That would take care of at least one of the problems, maybe both.

---

### Post by whistle on 2007-06-14
Woo! I did a ```
sudo dpkg --purge --force-remove-reinstreq keytouch
``` and all seems to be well... for now...

---

