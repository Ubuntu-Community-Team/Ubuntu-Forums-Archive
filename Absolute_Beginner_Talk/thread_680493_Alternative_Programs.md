---
title: "Alternative Programs"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Nider on 2008-01-28
Hi, I just install Ubuntu a few hours ago. I really looking forward to see what Ubuntu can do for me, this is my first time using Linux, so you will see a lot of me around here.

First, I would like to know which of the next programs works in Ubuntu a which one don't and what programs can I use for the ones that don't

- eMule
- uTorrent
- Limewire
- Media player classic (I need a video player that has most of the codecs around)
- Winamp
- CDisplay (I reeeeeally like mangas)

And, I installed Ubuntu in spanish but it would be better if it is in english, can I change the language after been installed!?
Also, my keyboard is in spanish, but I need it that way, but I can do the "@" anymore with Ctrl+Alt+Q (or sometimes 2). Which are the commands in a spanish keyboard for the "@"

Thanks everyone.

EDIT: Is Pidgin the best altenative for MSN!? Does iTunes run in Ubuntu!?

---

### Post by mattismyname on 2008-01-28
Winamp: I find amaroK the best winamp/itunes replacement

Media players: You can get all the codecs by following the instructions here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
You can use totem to play the videos.

MSN: Yes, use Pidgin
itunes: No, but amaroK is better than itunes anyway.

---

### Post by santiagoward2000 on 2008-01-28
> **Nider said:**
> Hi, I just install Ubuntu a few hours ago. I really looking forward to see what Ubuntu can do for me, this is my first time using Linux, so you will see a lot of me around here.

First, I would like to know which of the next programs works in Ubuntu a which one don't and what programs can I use for the ones that don't

- eMule
- uTorrent
- Limewire
- Media player classic (I need a video player that has most of the codecs around)
- Winamp
- CDisplay (I reeeeeally like mangas)

And, I installed Ubuntu in spanish but it would be better if it is in english, can I change the language after been installed!?
Also, my keyboard is in spanish, but I need it that way, but I can do the "@" anymore with Ctrl+Alt+Q (or sometimes 2). Which are the commands in a spanish keyboard for the "@"

Thanks everyone.

EDIT: Is Pidgin the best altenative for MSN!? Does iTunes run in Ubuntu!?

Hi Nider! Welcome!
There probably are alternatives for all those programs. I'll tell you the ones I know about.
_ For eMule there's **aMule** (although I haven't tried it). You can install it through Synaptics.
_There's a LimeWire version for Ubuntu, you can get it from LimeWire's page. However, I'd recommend **FrostWire**. It's similar, but has LimeWire Pro's connection. You can get it from [http://www.frostwire.com]("http://www.frostwire.com")
_There are lot's of video player's around. Personally, I use **totem-xine**, and I can run most videos with no problem. You can try **VLC** or **MPlayer** too.
_As an Itunes replacement, I like **Exaile**. **Amarok** is not bad either.
_As Winamp, you have **Audacious** or **XMMS**. But there are lots of other music players. I love **moc**, but that's me ;)
_For msn, **Pidgin** is really good. You could try **amsn** too.

About the keyboard, if you set it in Spanish, the @ is most likely **AltGr+2** (Spanish) or **AltGr+q** (LatinAmerican).
About changing your language, just go to **System/Language Support**, check English, and, after it is installed, select it as default.
I hope you like Ubuntu! Good luck!

---

### Post by ~LoKe on 2008-01-28
> **Nider said:**
> - eMule -- **aMule**
- uTorrent -- **Deluge, KTorrent, Transmission**
- Limewire -- **Frostwire**
- Media player classic -- **VLC**
- Winamp -- **XMMS**

> **Nider said:**
> 
Pidgin the best altenative for MSN!?
Not really.  aMSN is the best alternative; but Pidgin is MSN+More. 

> **Nider said:**
> 
Does iTunes run in Ubuntu!?
No, but you can use other applications if you have an iPod.

---

### Post by RomeReactor on 2008-01-28
Hi. A few alternatives would be:

* eMule -> [aMule]("http://www.amule.org/") (Available in Synaptic)
* uTorrent -> uTorrent with [Wine]("http://www.winehq.org/") (Wine is available in Synaptic) or [Deluge]("http://deluge-torrent.org/") (download [this package]("http://download.deluge-torrent.org/index.php?dir=ubuntu/gutsy/0.5.8.2/&file=deluge-torrent_0.5.8.2-1_i386.gutsy.deb") and double-click on it to install); note that Ubuntu has a BitTorrent client installed by default. You start it by downloading a **.torrent** file and double clicking on it.
* LimeWire -> [LimeWire]("http://www.limewire.com/download/version.php"), [FrostWire]("http://www.frostwire.com/")
* Media player classic -> Totem, [Mplayer]("http://www.mplayerhq.hu/design7/news.html") (Totem is installed by defaul; Mplayer is available in Synaptic)
* Winamp -> RhythmBox, [Audacious]("http://audacious-media-player.org/index.php?title=Main_Page") (RhythmBox is installed by default; Audacious is available in Synaptic)
* CDisplay -> [Comix]("http://comix.sourceforge.net/"), [QComicBook]("http://www.kde-apps.org/content/show.php?content=19509") (both available in Synaptic)

Synaptic is located in 'System->Administration->Synaptic'.

You should give a try to the applications already installed in your system. Note that to run LimeWire or FrostWire you need to install Java; you can find the following packages in Synaptic:

* sun-java6-bin
* sun-java6-jre
* sun-java6-plugin
* sun-java6-fonts

Or, to install them from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Welcome to the community!

---

### Post by SunnyDaze on 2008-01-28
Let's see, here's what I use:

eMule           =     LMule, although you might have to compile from source :-(
uTorrent       =     KTorrent, Azureus/Vuze or many others  (bittorrent was created for Linux)
Limewire      =     Limewire
Media Player =     Totem, Kaffeine, VLC, or many many others
WinAmp        =     Amarok, RythmBox or others (In my opinion Amarok is better than WinAmp or iTunes) 
CDisplay       =     GQview, although there are tons of image viewing programs.  I use GQView because it resembled ACDSee and it has recursive slideshow (includes the subdirectories).

Other good program replacements:

Web browser  =  Firefox
email  =  Thunderbird
CD/DVD Burning  =  K3B
DVDShrink  =  K9Copy
DVD to DivX/XviD = dvd::rip
Office  =  OpenOffice

---

### Post by bodhi.zazen on 2008-01-28
This is a nice link :

[http://linuxappfinder.com/windows](http://linuxappfinder.com/windows)

---

### Post by Nider on 2008-01-28
Thanks guys, you were really really helpful... I still have some doubts... hehehe

What is Synaptics??? It is like terminal were I have to run the programs that I want to use!?

EDIT: Also, if there is a way to change the language of Ubuntu after been installed!?
And is there any website that have a lot of programs made for Linux to download, like [www.download.com](www.download.com) for Win!?

---

### Post by bodhi.zazen on 2008-01-28
> **Nider said:**
> Thanks guys, you were really really helpful... I still have some doubts... hehehe

What is Synaptics??? It is like terminal were I have to run the programs that I want to use!?

EDIT: Also, if there is a way to change the language of Ubuntu after been installed!?
And is there any website that have a lot of programs made for Linux to download, like [www.download.com](www.download.com) for Win!?

synaptic installs programs, called packages.

Package management is different, you use add remove programs or synaptic or the command line (apt-get) to install.

See here : [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by billgoldberg on 2008-01-28
> **Nider said:**
> Hi, I just install Ubuntu a few hours ago. I really looking forward to see what Ubuntu can do for me, this is my first time using Linux, so you will see a lot of me around here.

First, I would like to know which of the next programs works in Ubuntu a which one don't and what programs can I use for the ones that don't

- eMule
- uTorrent
- Limewire
- Media player classic (I need a video player that has most of the codecs around)
- Winamp
- CDisplay (I reeeeeally like mangas)

And, I installed Ubuntu in spanish but it would be better if it is in english, can I change the language after been installed!?
Also, my keyboard is in spanish, but I need it that way, but I can do the "@" anymore with Ctrl+Alt+Q (or sometimes 2). Which are the commands in a spanish keyboard for the "@"

Thanks everyone.

EDIT: Is Pidgin the best altenative for MSN!? Does iTunes run in Ubuntu!?

Limewire -> Use frostwire (a free limewire pro) for p2p, you will need to download it from there website. Installing it is just double clicking. If you can't connect to the internet with frostwire, search the forums or ask in the forums.

Utorrent-> not natively. Use ktorrent, deluge, qtorrent or even bittornado or just plain old bittorrent itself (installed by default)/

Mediaplayer -> one word: vlc

Winamp -> not natively : try exaile, rythmbox or even songbird (not in repo's)

Utorrent and winamp 5 run in wine but I don't see the need since there linux counterparts are almost as good (in utorrents case) or alot better (in winamps case).

Try amsn, it has a more msn like feeling. But I prefer pidgin, once you get used to it, you'll be sold.

Itunes doesn't work on ubuntu. There are lots of programs that let you write to you ipod and alot of music players that can play it's content.

---

### Post by billgoldberg on 2008-01-28
Originally Posted by Nider  View Post
Thanks guys, you were really really helpful... I still have some doubts... hehehe

What is Synaptics??? It is like terminal were I have to run the programs that I want to use!?

EDIT: Also, if there is a way to change the language of Ubuntu after been installed!?
And is there any website that have a lot of programs made for Linux to download, like [www.download.com](www.download.com) for Win!?

--------------------------------------------------

That's the windows way of installing programs.

In linux it's a tad different.

There are things know as repositories (there are alot of them) and they contain 20.000+ pieces of software.

Because of that you can download program without needing to surf the internet and also because of that you can update every piece of software in your computer with the update manager.

There are two (gui) ways to download from the repositories.

- the easy, more visually pleasing way is going to "applications -> add/remove" (unlike in windows xp, add/remove is also used to install programs)
- if you want less commonly used software you go to synaptic. Go to "system -> administration -> synaptic package manager" and hit the search button.

There is offcourse also software that isn't in the repositories. Everything in the repos is safe to be installed on your system. Download from the web on your own risk.
a good website is getdeb.net.

To change the language -> system -> administration -> language support

I see you are really new to ubuntu so it might be a good idea to take a look at [this forum page]("http://ubuntuforums.org/showthread.php?t=613462"). The script there will install most applications you will ever need in an easy way (including: flash, java, dvd support, ...).

Another website you might like is [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by sleepingdragon on 2008-01-28
Synaptic is a package manager for Linux. It is a central repository for downloading and installing software. In some ways it is like download.com, it contains a load of software you can download, but has the advantage that software that is no longer needed can also be removed in pretty much the same manner as installing it - to install, tick the box, to remove, untick the tick... easy. Each piece of software comes with a description and is checked for compatibility before being made available. If any further files are required to make software run, then these will also be downloaded and installed. 

The Synaptic Package Manager can be found in your System menu.

Further to the list of Windows equivalent software, here's my list:

eMule - aMule (found in Synaptic)
uTorrent - KTorrent (found in Synaptic)
Limewire - try Frostwire, there's a native Linux version
Media Player - VLC (in Synaptic)
WinAmp - Audacious (in Synaptic - XMMS is no longer supported)
CDisplay - not sure, but there are online comic readers in... you guessed it... Synaptic. Synaptic does have a search function. Try "comic reader".

Changing language should be easy enough, it's in the System menu, but I can't help you with the keyboard layouts! 

As for MSN Messenger, Pidgin works very well, as does aMSN. Guess where you'll find those...

iTunes.... never owned an iPod!

---

### Post by Nider on 2008-01-29
Ok, now I get how does Synaptic works...

Now i have a bigger problem... I changed a bunch of things in the resolution of the monitor, and now when I run ubuntu, the monitor is all black after it loads.

:confused::confused: What should I do!?

Sorry for the bother...:lolflag:

---

### Post by RomeReactor on 2008-01-29
What video card are you using? did you have the restricted drivers enabled (from 'System->Administration->Restricted Drivers Manager')?

---

### Post by Nider on 2008-01-31
Hi, I know that it's a nvidia, but not sure which one. I think that I must have the restricted drivers enabled because it was working before I started messing around. Ill try to fix it today, I have been busy before. I will report if I need help, thx.

---

### Post by Aeph on 2008-02-22
Check out Songbird as an iTunes alternative.

---

### Post by justinmiller87 on 2008-02-22
Another great site to try is [http://www.osalt.com](http://www.osalt.com) (Open Source Alternative). It tells you plenty of software to help you out. If you know the name of the proprietary, type it in. If you know the name of the Open-Source, type it in. It will give you a list of alternatives for them all.

---

