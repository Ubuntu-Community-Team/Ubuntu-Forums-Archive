---
title: "Help with compiling/etc ?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Leeghoofd on 2006-03-21
Okay, First of all: I'm a complete and utter Linux Noob so if I ask something that might appear totally stupid please feel free to mock me...
If, for some reason the answer to my question is posted somewhere else in this forum please forgive me. I've been looking on the internet for some time now and do not have an inclination to look through ALL the threads. Any redirections will be appreciated.

Now for the real question:

I've been trying to install mplayer, which seems to give an error message
" no GCC found " Or something simular. From what I've read on this board and found out by playing with Ubuntu there indeed seems to be no GCC application included with a standard install.

I downloaded GCC 3.2 as recommended in the manual for Mplayer, however when I run ./configure the following message appears:
"the command 'cc -o conftest - g conftest.c failed"

This seems to be caused by the fact that the command CC does not work in my terminalscreen. 

I've ( briefly ) browsed for a cc application, however is this not supposed to be installed already? If so is this a path related error message ? What can I do to make GCC run? 

( I suppose I'll need to look into the basics of GCC aswell since it appears to be needed for installing other applications aswell )

---

### Post by LordBug on 2006-03-21
in a terminal:```
sudo apt-get install build-essential
```Should take care of the problem.

Actually, why are you compiling Mplayer?  It's in Synaptic.

---

### Post by Leeghoofd on 2006-03-21
well, as stated I've just installed Ubuntu and have no clue as to what I'm doing... :) ( rest assured I'm Playing with a clean computer, used for no other purpose than some system testing ) 

As for Synaptic, I have NO idea how to work with that. :confused: 

It seems to me that you need GCC for installing most applications tho, so it should be usefull to figure out how it works, shouldn't it ?

---

### Post by Bagnaj97 on 2006-03-21
Most applications (including mplayer and gcc) are in the ubuntu repositories. You can enable the repositories and install software from them using a program called synaptic. Details are here: [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

The repositories contain a lot of applications and they are enough for most people. If you do need a program that isn't in the repositories then you may need to compile it yourself. For this you will have to install the build-essential package. Then you should be able to compile the program using ./configure && make && sudo make install. If that doesn't work try reading the documentation that comes with the program.

---

### Post by meborc on 2006-03-21
i suggest you read this peace of nice writing: [https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto) ... then you will understand, that you don't need to compile anything... well almost anything, as there are more than 17000 programs in repositories, just for **sudo apt-get install** :mrgreen:

---

### Post by Leeghoofd on 2006-03-22
:rolleyes: THanks for the replies and patience guys :) 

BTW so far i've been really impressed with the performance of ubantu.
Where I've dropped earlier attempts to install linux ( mandrake, Knopix etc ) since it took me to much time to set up standard pc settings like
network settings, Display settings etc etc, Ubantu actually manages to get it working out of the box ( on my laptop anyway ). 

Now if I could just get to install programms on it i would be a very happy person. :rolleyes: For now I'm blaming my lack of unix/linux knowledge for not being able to do so. I'll try the repositories and Saraphine app mentioned by u people later. 

THx again

---

### Post by Leeghoofd on 2006-03-22
O.k. I've been playing with the -apt commands and the Synaptic package manager. 

I've managed to get several applications/games/etc that are now displayed in The SPM. I can get them to install aswell.

However, I do not seem to be able to import Mplayer into the Synaptic package manager. Any help on this is very welcome.

I added several software sources for SPM to get its updates from.
I also downloaded the Mplayer to a local folder. Is there any way of manually importing it in the SPM?

---

### Post by GreyFox503 on 2006-03-22
The idea behind the package manager is that you don't have to manually download and install software yourself.  Mplayer is probably in the repositories (I'm not on Ubuntu right now).  Just try opening Synaptic and searching for "mplayer".  You might get several entries.  Choose the one that seems most appropriate and put a check mark next to it to install it.  Then hit apply.  It should download and install the package for you.

Anytime something is in the repo's, get it with Synaptic or apt-get.  Only if you need other software or want the very latest version of something do you need to download it manually.

---

### Post by Leeghoofd on 2006-03-22
The problem is, I'm not getting any mplayer finds in synaptic. I'm pretty sure it has been updating from the internet since there are some 16.000 entries in the repository that are not installed and the program said it was downloading new applications without any failure message.

---

### Post by GreyFox503 on 2006-03-23
Hmm, that's odd.  I'm in Ubuntu right now and I have mplayer showing up in Synaptic.  It says it's in the multiverse.

Make sure you have enabled the extra repositories, like here:  [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

The one you want is probably mplayer-386.

---

### Post by Leeghoofd on 2006-03-23
Thx greyfox, i've now managed to get Mplayer functional.

Ofcourse I got a new bug:
The movies are being played but I get an error message> 

" new_face Failed. Maybe the font path is wrong. Please supply the text font file ( mplayer/subfont.ttf )

The movie is being played in a somewhat awfull small window. 

Even so, this is the first time I've made Linux functionally usable on a laptop.
( sound, internet, mp3 player and movie player are all working ) jeeej for me  :P

and thx to you all :)

---

### Post by GreyFox503 on 2006-03-24
I've actually never used mplayer, so I don't know about that.  A quick Google looks like it you need to make a symbolic link to a fonts directory.  This is taken from the [mplayer guide for Fedora Core]("http://www.mjmwired.net/resources/mplayer-fedora.html") (but may still be relevant):

> **3.3.4. OSD / Fonts**

  The OSD (On Screen Display) and Subtitles you need fonts properly installed. You should set this up regardless of whether or not you use the GUI.
  If you use FreeType (all recent RH/Fedora releases have it by default). You should have the XFree86-truetype-fonts RPM in FC1, or xorg-x11-truetype-fonts RPM if FC2, or fonts-xorg-truetype RPM if FC3/FC4. In FC5: xorg-x11-fonts-truetype. You need [msttcorefonts package]("http://www.mjmwired.net/resources/mjm-fedora-fc5.html#ttf") for the last option below.
  [**user@charon user**]# mkdir ~/.mplayer/
FC5:
[**user@charon user**]# ln -s /usr/share/X11/fonts/TTF ~/.mplayer/subfont.ttf
-OR- (FC1,2,3,4)
[**user@charon user**]# ln -s /usr/X11R6/lib/X11/fonts/TTF/luxisri.ttf ~/.mplayer/subfont.ttf
-OR-
[**user@charon user**]# ln -s /usr/share/fonts/msttcorefonts/arial.ttf ~/.mplayer/subfont.ttf
 
And here is a link to the [relevant page on mplayer's website]("http://www.mplayerhq.hu/DOCS/HTML/en/subosd.html") (search for "subfont.ttf").

If that doesn't work, I'm using the totem-xine package, and that does it for me.

Good luck!

---

