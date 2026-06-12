---
title: "Ubuntu N00b looking for help- some questions"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ChaosApothecary on 2007-11-15
I am building a new rig (mainly for gaming) and am sick and tired of using XP and Vista, so I'm giving Ubuntu a shot.

I downloaded the .iso and burned it onto a DvD, so the installation should be primed and ready to go as soon as the computer parts arrive in the mail today.

I am trying to figure out how to download/use WINE and having some difficulty however.

As I understand it, I need WINE to run/open .exe programs, is this correct?

The only download I found available ended in ".tar.bz2", which is something I have never seen before.

Did I download the correct program, or am I way off?

I plan to install Ubuntu 7.1 (GG), can anyone direct me to, or help me with a walk through on what I need to between installing Ubuntu and being able to run games (with WINE)?

As an additional question- I'm relatively unsure of what Ubuntu is able to do (if anything), do I need third party programs to do EVERYTHING? (I.E. from opening media to running games).

So far 3rd party programs that I plan to use are:
Mozilla <3
Open Office
WINE (I assume I need this)
Random Media Player (any recommendations? I don't particularly like REAL player)

Any other suggestions on 3rd party programs I will need?

Thank you for any and all help!

---

### Post by Lord_Dicranius on 2007-11-15
> As I understand it, I need WINE to run/open .exe programs, is this correct?
This is one way of using them, yes.

> The only download I found available ended in ".tar.bz2", which is something I have never seen before.
Is this a download for Wine?  If so, I would just install Wine from the Ubuntu repositories rather than compile it that way.  Regarding the ".tar.bz2" file extension, think of it like a .zip file.  It archives files together and compresses them.

As far as actually using Wine, I'm still playing around with it, so I'm gonna leave that for somebody else to answer hehe

As far as "3rd party programs go", Firefox and OpenOffice come pre-installed on Ubuntu.  And for a media player: Rhythmbox for audio and Totem(?) for video is installed by default.  Though you may need to install the correct codecs to play mp3's, .mov's, DVDs, etc.

Hope this helps :)

---

### Post by OldTimeTech on 2007-11-15
In 7.10, under application ->add/remove, make sure you have all available applications in the left hand window, then in search type wine....it is there and that will load automatically for you from the repositories.

Depending on what games your planning on running will depend on whether wine will actually run them.  Cedega is the platform that is used mostly for games, but it is not free.
Check out this url: [http://www.cedega.com/](http://www.cedega.com/)

I have to say I don't know what would be like Random media player.

Also, mozilla (or if you mean firefox) is already in Gnome along with Open Office...again if your using KDE I have no clue.

---

### Post by Lord_Dicranius on 2007-11-15
> Also, mozilla (or if you mean firefox) is already in Gnome along with Open Office...again if your using KDE I have no clue.
I believe Firefox and OpenOffice are installed by default on Kubuntu also (trying to remember from the short period of time I actually used Kubuntu hehe).

**UPDATE**
Thought I might add... if you're looking for a media player that plays everything (audio, video), a couple applications you might wanna try are mplayer and VLC (I believe both of these can be found in the repositories).  I use mplayer and I love it.  There are a lot of other people here who are hooked on VLC though too :)

---

### Post by Mondoman on 2007-11-15
Regarding installing WINE, although you can install software the really "old" manual way or the "old" command-line way using a package manager, you'll find it much easier (and more easily reversible in case of problems), to use the (graphical-interface-based) Synaptic Package Manager that's part of Ubuntu.  It's at (menu) System/Administration/Synaptic Package Manager.  
Before you rush off to try the obstacle-strewn path to running Windows programs under Ubuntu, spend a bit of time learning the basics of Ubuntu, including where files are kept and how to manage adding/removing/updating software using the Synaptic manager (or the command line apt-get manager).  Make sure you are able to get the compiz fusion window manager working with your graphics card, are able to get networking running properly, and are able to get printing to work.
After that, at least chances will be that problems you run into are real Windows-on-Linux problems and not just understanding how Ubuntu works.

---

### Post by Jaco Du Toit on 2007-11-15
I've had quite bit of success with the Wine version that is available from the normal 7.10 repositories - without fiddling too much with config files etc I got World of Warcraft to work pretty well. In my experience most games that can be set to OpenGL works fairly well.

To install, as other's have suggested, just use Synaptic package manager, search for wine, and install.

---

### Post by alwiap on 2007-11-15
For a media player, although Totem Player/Rhythmbox is nice, I prefer using VLC and I'm sure people would agree, if you want to install it you can use Synaptic Package Manager (System > Administration) and search 'vlc' and install the packages.  or add/remove programs in 'Applications', whichever.  If you want to set VLC as your default program for music files, right click a music file (once VLC is installed), and go to the Properties > 'Open With' tab and choose VLC. 

If you listen to music a lot while you compute I would suggest Amarok, which is available the same way. Personally, I have a lot of music but don't listen to it while computing, so I just use VLC player mostly.  But again, if you like playlists and a powerful music program, Amarok is hot.

to my knowledge once you install wine, you can just run .exe files and other related files by just double-clicking; when wine is installed it is default to open those files.

there are many threads here for getting specific games to work (i.e. WoW, CS:S).  a quick search on the forums should help you out.

---

### Post by Lord_Dicranius on 2007-11-15
> If you listen to music a lot while you compute I would suggest Amarok, which is available the same way. Personally, I have a lot of music but don't listen to it while computing, so I just use VLC player mostly. But again, if you like playlists and a powerful music program, Amarok is hot.
Amarok is awesome (loved it when I was using Kubuntu), but it's also KDE-based.  Exaile is said to be a Gnome-friendly version of Amarok.  I've been using it lately and I'm liking it a lot :) (Exaile is also in the repositories).

---

### Post by markharding557 on 2007-11-15
you can get the latest wine  here[http://www.winehq.org/]("http://www.winehq.org/")
you will find some programs work,some require tweaking and some don't work at all.
The wine app database will give you an idea [http://appdb.winehq.org/]("http://appdb.winehq.org/")]
you say you like games here is a list of linux native games 
[http://en.wikipedia.org/wiki/Category:Linux_games]("http://en.wikipedia.org/wiki/Category:Linux_games")
you can install codecs with ubuntu-restricted-xtras from the repository

---

### Post by Dark Hornet on 2007-11-15
Welcome to Ubuntu!  I am a pretty hard core gamer, and I have a number of games running under Ubuntu using WINE.  I will tell you now--not all games play nice with WINE, and quite honestly are better if played under WIndows--this is why I still maintain a Windows box.  I have a nVidia 8800 GTX, and the ONLY way I can take advantage of it "fully" when gaming, is to run it under WIndows.  Anyway, good luck, and hopefully the games you like to play will work with WINE, and as always--just post if you have any questions.

---

