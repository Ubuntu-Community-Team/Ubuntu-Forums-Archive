---
title: "Help! Can't remove / fix alien"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-18
Some time ago, I installed alien, to try and get Win4Lin to work in Ubuntu.

However, this came to nothing, so I tried to uninstall it the other day. Thought nothing more of it. Tried to upgrade to Gutsy tonight, got message:

> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Tried that, and it's clear that alien is the problem:

```
Removing alien ...
dpkg: error processing alien (--remove):
 cannot remove `/var/lib/alien': Permission denied
Errors were encountered while processing:
 alien
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So, tried apt-get autoremove (both as sudo and su), got this:

```
Removing alien ...
dpkg: error processing alien (--remove):
 cannot remove `/var/lib/alien': Permission denied
Errors were encountered while processing:
 alien
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Trying to reinstall alien in Synaptic doesn't work:

> E: /var/cache/apt/archives/alien_8.65_all.deb: unable to stat `./var/lib/alien' (which I was about to install)

I've looked for var/lib/alien. It's a file of "unknown type" and 0b!

So, how do I get out of this loop?!

Thanks in advance

---

### Post by forestpixie on 2007-10-18
you could try to purge it

```
sudo apt-get remove --purge alien
```

---

### Post by qprfact on 2007-10-18
Would you believe, I get the same error message!

It obviously doesn't like the "alien" file, or it's of an unexpected type

---

### Post by forestpixie on 2007-10-18
nasty nasty little green men :D

I guess you could try this 

```
sudo dpkg --configure -a
```

but not sure it'll do anything, I'll check back - but I've got an intermittent internet fault that's driving me up the wall :(

---

### Post by qprfact on 2007-10-18
Nope, that didn't seem to do anything,

I contacted the person who looks after alien now, and he said I should delete /var/lib/alien, but I get permission denied for that (even as root).

He said it could be "anything from SE Linux to a corrupt filesystem on your machine."

Hmm... could be looking at a fresh install of 7.10 here!

---

### Post by forestpixie on 2007-10-18
try this

```
sudo dpkg --remove --force-remove-reinstreq alien
```

---

### Post by qprfact on 2007-10-18
Nope

```
(Reading database ... 129712 files and directories currently installed.)
Removing alien ...
dpkg: error processing alien (--remove):
 cannot remove `/var/lib/alien': Permission denied
Errors were encountered while processing:
 alien
```

---

### Post by forestpixie on 2007-10-18
emmm  - absolutely no idea then except if you can't delete as suggested by your contact even with nautilus as root, you could try booting with the livecd - and try in there with root nautilus

otherwise I'm sorry :(

---

### Post by qprfact on 2007-10-20
It's been suggested to me by a work colleague that I can try fsck to clear the errors, but this involves mounting as read only?

This sounds a little daunting, though I'm willing to give it a try! Can anyone help?

Thanks!

---

