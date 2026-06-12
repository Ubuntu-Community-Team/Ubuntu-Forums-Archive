---
title: "Trouble with installing repository list."
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by mon_m on 2006-10-09
I recently downloaded EasyUbuntu (god, I wish I knew it was there a few weeks ago when I first installed Ubuntu), but I've come across an issue when I attempt to download and install the 'repository list' packages.

I don't have any trouble installing the others, it's just this one.  I receive an error that reads,

[INDENT]
Warning

The following problems were found on your system:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
[/INDENT]


I'm pretty lost on what any of this means, any help would be greatly appreciated.  Apparently I suck enough even to break EasyUbuntu. :-k

---

### Post by bruenig on 2006-10-09
saw this question popping up in the forum, looks like a problem with easy ubuntu when they are adding the repos, they are either not giving the right gpg key or aren't giving one at all and therefore the authentication is failing.
What are you trying to use easyubuntu to acheive, I am sure someone could help you get that done.

---

### Post by mon_m on 2006-10-09
I just really wanted the lists installed so that I could find some packages more easily.

---

### Post by Bigbluecat on 2006-10-09
I have the same error but Easyubuntu still seems to install stuff. I ahve only used it to install a few items though.

For those still learning "stuff" is a highly technical and flexible term describing the actions of "things". In this cas Easyubuntu is the thing and it does stuff.:rolleyes:

---

### Post by norco on 2006-10-09
run these commands in terminal:
```

sudo gpg --keyserver subkeys.pgp.net --recv F120156012B83718
sudo gpg --export --armor F120156012B83718 | sudo apt-key add -

```

---

### Post by girlfreddy on 2006-10-10
Thank you for this. It worked great.

---

### Post by TigPT on 2006-10-10
thks.. keep going helping newbies like me ;)

---

