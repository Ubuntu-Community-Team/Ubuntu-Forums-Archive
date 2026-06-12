---
title: "I lost repositories!"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-03
I really don't know what I did, but somehow I've messed up in the Synaptic Package Manager.  When I click on Synaptic Package Manager, I get the screen with all the fields in it (in the background), but no programs listed.  I get an error message (that I can't widen the window on) and it says...

The following problems were found on your s

E. Malformed line 41 in source list /etc/apt
sources.list (dist parse)
E. The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by mjm115 on 2006-05-03
Have you ever edited your source.list file?  Do you have a backup of it?  Usually I get this error when I've tinkered with my sources.list file.  Can you copy and paste it in the thread?

---

### Post by cgjones on 2006-05-03
If you could, post the contents of /etc/apt/sources.list so we can see what the problem is.

---

### Post by manicka on 2006-05-03
You'll need to manually edit your sources.list

In a terminal type
```
sudo gedit /etc/apt/sources.list
```

then look for the error at line 41.

If you want a nice simple soucres.list, then I'd suggest aysiu's list here

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by Guns90 on 2006-05-03
Here's what I got...
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free 
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arniewinechanged
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary
CD Ubuntu 5.10 "Breezy Badger"  (Binary)

---

### Post by cgjones on 2006-05-03
It looks like you need this:
```

deb http://wine.sourceforge.net/apt/ binary/

```
You had this:
```

deb http://wine.sourceforge.net/apt/ binary

```

---

### Post by Guns90 on 2006-05-03
In that I don't know what is wrong with line 41 (assuming I'm even counting right), I did the copy/paste thing and its working properly now.  Appreciate the help, guys.  

BTW.  Is each and every line counted, regardless if it has any text, or is it text lines only?

---

### Post by manicka on 2006-05-03
[QUOTE=Guns90]
BTW.  Is each and every line counted, regardless if it has any text[/QUOTE]

yes :)

---

### Post by Guns90 on 2006-05-03
One little hash mark. Thanks manicka.

---

