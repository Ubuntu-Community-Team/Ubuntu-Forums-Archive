---
title: "Questions about how apt-get works/where stuff goes"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-02
Okay, the situation is this:
I have (finally, I swear to god) successfully compiled gDesklets 0.35.3.  To avoid conflicts, I removed the 0.35.2 deb package.  Unwittingly, I also removed *gdesklets-data* (the sensors and displays package).

What I want to do is download the *gdesklets-data* package.  The problem is that *gdesklets-data* depends on *gdesklets*, which I do not want to reinstall.

1. How can I download only the data package?
2. How do I find out where it installs to so I can put it in the right directories?

thx, all- pete

---

### Post by audax321 on 2006-02-02
The gdesklets-data package was specifically put together to provide some desklets for the gdesklets version available through the repositories. If you can run your compiled version of gdesklets, installing desklets is quite easy (and the desklets from the package can be found on the website as well - and in possibly newer versions). All you have to do is go here: [http://www.gdesklets.org/](http://www.gdesklets.org/) (that's their new website... you also check here for gdesklets that they might not have moved over yet: [http://gdesklets.gnomedesktop.org](http://gdesklets.gnomedesktop.org))

Find a desklet you like then either:

1. Download the package.
2. Go to File > Install Package in gdesklets and install it after finding it on your hard disk.

OR

1. Copy the link to the package.
2. Go to File > Install Remote Package in gdesklets and paste the URL in there and gDesklets will download and install the desklet.

All of the desklets end up in /home/yourusername/.gdesklets (assuming your NOT running gDesklets as root - using sudo).......... so if you ever want to get back to a fresh install, just remove this folder and your settings will reset.

---

### Post by TeeAhr1 on 2006-02-02
[QUOTE=audax321]The gdesklets-data package was specifically put together to provide some desklets for the gdesklets version available through the repositories.[/QUOTE]
Interesting.  Didn't know that.
>  If you can run your compiled version of gdesklets, installing desklets is quite easy...
I did know that.  I'm having some problems with a couple of specific desklets that worked in 0.35.2.  OTOH, SideCandy works now...

---

