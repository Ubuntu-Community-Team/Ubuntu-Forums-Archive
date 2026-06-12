---
title: "Realplayer"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by mlemily on 2007-07-20
Since BBC radio still streams with RealPlayer, I'm looking to install it on Feisty.
I've read the other threads on the subject and can't understand why I'm still not showing it as an option in my Add/Remove package manager.

In:
 System --> Software Sources

I've checked multiverse in the Ubuntu Software tab

and also added:
**[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial** main
**[http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty** free non-free

to the Third Party Software tab....

But searching for realplayer and RealPlayer with the Add/Remove package manager. 
Applications --> Add/Remove
give nothing.

sudo apt-get install realplay

gives

E: Couldn't find package realplay

sudo apt-get install realplayer

gives

E: Package realplayer has no installation candidate

which would all lead me to believe the package is not available, but I seem to have done a few things that should have made available

obviously I've missed something........

Thanks for your help!
E.

---

### Post by por100pre1 on 2007-07-20
Install [Automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29"). Then install realplay as you intended.

---

### Post by mlemily on 2007-07-23
Sorry to be pain, but I have to ask.....

Why?

You seem to be suggesting I install another graphical package manager (from what I can tell about Automatix).  
Is the assumption that Synaptic just isn't working in this instance?

Ta,
Emily

---

### Post by candtalan on 2007-07-23
> **mlemily said:**
> Since BBC radio still streams with RealPlayer, I'm looking to install it on Feisty.

realplayer is not essential, but can be downloaded from the real.com site and installed independently.
However, you might prefer to use the following(from a a UK list)

==========
Add the medibuntu repo as per these instructions - this is so you can
install the necessary codecs.
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

sudo apt-get update
sudo apt-get remove totem-mozilla
sudo apt-get install mozilla-mplayer w32codecs

You should then find that opening firefox and going to any of the bbc
realplayer pages you can click "play in realplayer" and it should work
in the browser.
==========


good luck

---

### Post by wpshooter on 2007-07-23
Do a google search on Realplayer for Linux and make sure you pick the link that will take you to the "REAL" real site and then download and install.

Good luck.

---

### Post by por100pre1 on 2007-07-23
> **mlemily said:**
> Sorry to be pain, but I have to ask.....

Why?

You seem to be suggesting I install another graphical package manager (from what I can tell about Automatix).  
Is the assumption that Synaptic just isn't working in this instance?

Ta,
Emily

Automatix adds another repos and it can help you to add realplayer if don't get to add it with Synaptic and the already added repos... but it's up to you to try it. After all, it is only a suggestion. Of course, you can always go to the real site and download the program from there...

---

### Post by mlemily on 2007-07-25
Hey guys,

Thanks for all your replies!

I've been successful installing RealPlayer using Automatix - yay!
And it behaves exactly the way I have come to expect from using Suse.

I tried installing the w32codecs, from what candtalan posted, and it did suceed in playing the BBC stream, but also suceeded in totally mucking up Firefox.  On multiple tries Firefox stopped responding when asked to switch windows or perform functions in another window and I had to restart the system to end the stream.  hah!

I also downloaded RealPlayer for linux from the Real site, but I'm not very experienced with .bin files and lacking any clear installation instructions I eventually gave up tinkering and tried Automatix.

As wpshooter said, it seems to add a repos and then provides a graphical installer to manage it.
But what do I know, I'm just a hopeless newbie!

Thanks all!
E.

---

### Post by por100pre1 on 2007-07-25
Good to know Automatix worked for you. Just keep in mind that many posters don't recommend Automatix because some drivers and programs available in Automatix can cause problems on some PCs... just be careful when installing drivers and other software :KS.

---

