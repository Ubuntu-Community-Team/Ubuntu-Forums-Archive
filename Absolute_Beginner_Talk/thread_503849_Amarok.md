---
title: "Amarok"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Leonin on 2007-07-18
I have searched to forums but I dont seem to find what im looking for. 
I have tried to install Amarok several times now but I always get the "cannot talk to Klauncher" message.
What KDE packages do I need to run Amarok?

---

### Post by Hobo Joe on 2007-07-18
Completely remove and clean out your current install of Amarok:

```

sudo aptitude purge amarok

```

Then to do a re-install with better dependencies:

```

sudo aptitude install amarok

```

Let us know if you still have problems.

---

### Post by Leonin on 2007-07-18
That doesnt work. I bet it some odd and evil little package that doesnt want to install.

---

### Post by Hobo Joe on 2007-07-18
type 'amarok' in the console and post whatever it says.

---

### Post by forestpixie on 2007-07-18
I don't profess to understand why it's doing it - I found this thread which suggests it's caused by kdeinit.

Post 12 and seperately 14 appears to have solved it for him/her

[http://ubuntuforums.org/showthread.php?t=251325](http://ubuntuforums.org/showthread.php?t=251325)

That at least is one problem I've not had running amarok ::D

---

### Post by Leonin on 2007-07-18
Things are getting more confusing. From to time when I start Amarok it works.......

Anyway, here's my log from when I start it in terminal.
> mikael@wahlin:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099208 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099208 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

Thank you for your help :)

---

### Post by Hobo Joe on 2007-07-18
I assume you're running Kubuntu.

First, try 'amarokapp', see what happens. Then, find your keyboard shortcuts(not sure where they are in Kubuntu), and disable all the multimedia functions.

---

### Post by Leonin on 2007-07-18
Oh sorry, Im using Ubuntu Festy fawn. :)
 Heres the log that was created when I tried Amarokapp:
> mikael@wahlin:~$ amarokapp
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099208 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099208 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP



---

### Post by AlexenderReez on 2007-07-18
> **Leonin said:**
> I have searched to forums but I dont seem to find what im looking for. 
I have tried to install Amarok several times now but I always get the "cannot talk to Klauncher" message.
What KDE packages do I need to run Amarok?

it is not amarok package ....it is ** Klauncher** .....hm...i think it is better you try to be familiar with rhythmbox or if you really like amarok style...how about give a try exile ...

---

### Post by Leonin on 2007-07-18
> it is not amarok package ....it is  Klauncher .....hm...i think it is better you try to be familiar with rhythmbox or if you really like amarok style...how about give a try exile ...

Over the last days I think I've tried all the musicplayer that are out there. I really liked Songbird but since it doesnt work that well with Compiz atm I decided to let it go. 
I have been using Amarok for awhile now (on KDE) and I have grown to like it very much, so if there is a possibility to run it under Gnome I might as well try as hard as I can to make it work.

---

### Post by AlexenderReez on 2007-07-18
> **Leonin said:**
> Over the last days I think I've tried all the musicplayer that are out there. I really liked Songbird but since it doesnt work that well with Compiz atm I decided to let it go. 
I have been using Amarok for awhile now (on KDE) and I have grown to like it very much, so if there is a possibility to run it under Gnome I might as well try as hard as I can to make it work.

the problem is amarok is not gtk application ....so because many people use amarok...the is a fork for it --> exile ....hm...i'm running amarok right now...got no problem....i have both kde and gnome session ....so make sure you have kde-libs and few other libs installed...and ofcourse klauncher ...

---

### Post by Depressed Man on 2007-07-19
It should work (I have it running under gnome myself) if you install its KDE's dependencies.

---

### Post by forestpixie on 2007-07-19
I have it running under gnome - but I can't say it's ever been problem free :(  tried to get to the botom of it through amarok forum - but it doesn't seem to very fast there....but I persevere 

I assumed the dependencies got sorted when you installed - is that not the case?

---

### Post by rickycodie on 2007-07-19
this is the problem with running kde apps in gnome, they use different dependencies.
like it was stated earlier install the dependancies.

---

### Post by forestpixie on 2007-07-19
Yes completely understand that - but it's knowing which dependencies, but then if I go with installing kub desktop - I assume they'll be sorted then

---

### Post by dptxp on 2007-07-19
Amarok is in add/remove. You just add it. It will install whatever is needed

I installed kde-core. Amarok did not find correct mp3 decoder.

Here is a thread where I got solutions, I had removed Amarok by then. Did not try again.
[http://ubuntuforums.org/showthread.php?t=445828](http://ubuntuforums.org/showthread.php?t=445828)

---

### Post by forestpixie on 2007-07-19
I installed it ok through apt-get - just wondering if there was something missing - thanks for reply

---

### Post by jnorthr on 2007-07-19
Well guys, I gave up trying to use amarok under ubuntu 7.0.4 gnome, i just could not face having to install kde first and possible problems that would bring...

Now i have started to look at trying xmms but the list of dependencies there is breath-taking and they have further dependencies as well. I do NOT have an internet connection, so the best i can do is to download .deb's on a friend's windows xp machine and hope to catch all their requirements in one go, but it's never that easy. So far i have devoted 3 weeks to trying to get something to play either from disk resident .mp3's or from music CD's, ditto for any movies. I will not go back to using windows but it's a pain to use so far. Have installed (i think) w32codecs and various gstreamer bits to make rythemplayer work ditto for movieplayer - no luck so far.:confused:

---

### Post by Depressed Man on 2007-07-19
You don't have to install KDE to get Amarok to work though..you just need some of its dependencies. But yeah, it is hard to install without an internet connection.

---

