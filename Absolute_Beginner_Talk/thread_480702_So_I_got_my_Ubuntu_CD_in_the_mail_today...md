---
title: "So I got my Ubuntu CD in the mail today.."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-21
Okay, my CD came with Ubuntu 7.04 today. I'm really excited to get it installed and functional, however, I need to know quite a few things.

**My current PC specifications are the following:**
Intel P4 2.0ghz processor
768mb PC2100 RAM
40GB Hard Drive
Onboard Intel Graphics Adapter (no AGP/PCI/PCI-E graphics card)
Onboard Sound Card (no PCI/PCI-E sound card.)

**I use the following drivers for audio and display:**
Display: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Audio: SoundMAX Integrated Digital Audio

Will my computer be able to run the normal version of Ubuntu 7.04 very well with those specs?

**Moving on, the main programs I need a linux replacement/compatible version are the following:**
dvdSanta (I use it to convert AVI files into DVD files)
uTorrent
Winamp
WS_FTP Pro (I use it to FTP files to my web server, etc)

Can anybody help me find a suitable replacement that functions good and looks good?

Thank you all for your time. ^_^ I hope you can be of some assistance.

---

### Post by Majorix on 2007-06-21
To see if your hardware is supported on Ubuntu you could launch it from LiveCD and see for yourself. I don't think people here will really know if they will be Ubuntu-compatible or not, unless they are computer engineers :)

I know replacements to 2 of the programs you counted.
Instead of utorrent you can use Azureus or gnome-btdownload, which are both in the repos.
Instead of Winamp you can try the various followups to xmms (which is a dead project thought to clone Winamp on Linux) or xmms itself, which works quite well too.

---

### Post by bren on 2007-06-21
hi exershio

set bios to boot from cd

boot from the cd

most things should work straight away

if you like it click install button on desktop and people here will help you get up and running

there is torrent client for you Ktorrent is one for example
Amarok is very powerful (and some say best of music players)
ftp can be done from nautilis (default files browser)

bren

---

### Post by Skrynesaver on 2007-06-21
> **Exershio said:**
> Okay, my CD came with Ubuntu 7.04 today. I'm really excited to get it installed and functional, 
Welcome to Ubuntu
> however, I need to know quite a few things.

Will my computer be able to run the normal version of Ubuntu 7.04 very well with those specs?
Should run quite well

Replacement apps
[I]
dvdSanta (I use it to convert AVI files into DVD files)[/I] Don't do much video
* uTorrent *bittornado-gui or gnome-btdownload[I]
Winamp[/I] Oh where to begin, Amarok will blow you away
* WS_FTP Pro *again the choice is almost endless gftp ties in well with the default window manager

[This]("http://linuxappfinder.com/") is a useful tool for finding replacement apps

---

### Post by liveforfunnow on 2007-06-21
That hardware sounds fine for Ubuntu. Toss in the LiveCD, and test it out (no changes are made to your system ). If everything works, click INSTALL on the desktop, and follow the instructions. If something doesn't work, post the details, and the community will try to help.

uTorrent >> ktorrent
Winamp >> VLC or RythmBox 
WS_FTP Pro >> gFTP

to install any of the programs above, open Synaptic Package Manager (System >> Administration) and start typing the name. Click the box next to the name of the program, and click "Mark for Installation." Once all three (or four or five or x) are selected, click "Mark All Upgrades" followed by "Apply" at the top. 

Welcome to Freedom.

---

### Post by Exershio on 2007-06-21
okay, thanks a lot for your comments. I'm gonna try the Live CD out and see how it all works

---

### Post by ubuntu27 on 2007-06-21
I have similar a computer with a similar specification as yours. I believe it would work flawlessly as it did to me. 
TO be sure, just insert the Disc that you received in the mail and boot with it. It won't install anything (nor touch the Hard Drive) unless you tell it to.  When you boot with the CD, you will be in a Live CD environment, where you can Run the OS (Ubuntu) directly from the CD and RAM. This means that the Live CD section is the same as when the OS is installed in the Hard Drive. If something does not work in the Live CD, then, after install it won't work by default. If you find some problems, it can be solved, like Wrong Screen resolution.

Moving on:

> dvdSanta (I use it to convert AVI files into DVD files)

DOn't know about this one. 

> uTorrent
There are a lot of replacements for this one, like gnome-torrent,[ K-kTorrent (KDE's Torrent]("http://ktorrent.org/")) , [Gnome BitTorrent]("http://gnome-bt.sourceforge.net/") (too simple for many), [Azureus]("http://azureus.sourceforge.net/"), [BitTornado]("http://bittornado.com/"), [Deluge]("http://deluge-torrent.org/"), etc. To name a few.


> Winamp

. You can try [Amarok]("http://amarok.kde.org/") (believed to be the best music player by many), [Beep Media Player]("http://beep-media-player.org")

> WS_FTP Pro (I use it to FTP files to my web server, etc)

Many FTP clients also. Can't list them since I don't use them.

---

### Post by paparucino on 2007-06-21
> **Exershio said:**
> 
Will my computer be able to run the normal version of Ubuntu 7.04 very well with those specs?

You can bet on it :-)


> 
dvdSanta (I use it to convert AVI files into DVD files)
uTorrent
Winamp
WS_FTP Pro (I use it to FTP files to my web server, etc)

Can anybody help me find a suitable replacement that functions good and looks good?

Thank you all for your time. ^_^ I hope you can be of some assistance.
I dont' know a replacement for dvdSanta, but the reps a full of those kind of programs
utorrent: deluge or the simple transmission
Winamp: audacious, a clone of xmms which is a clone of winamp (the same skins)
gFtp.

I prefer they work and not they looks good :-) :-) (jocking)

---

### Post by haricharan on 2007-06-21
winamp -> u can try **exaile** or **amarok **... 
gFTP -> FileZilla...i think its in the repos..or u can just download from Sourceforge...

---

### Post by deadlikeoscar on 2007-06-21
Amarok is amazing and you can even enable lyrics so you can read the lyrics for many if not most songs. uTorrent you can install in wine but I would recommend using Transmission or Deluge. Transmission works with most private trackers if that matters so you may like it. Not sure about Deluge. The only thing about Transmission is I THINK you have to use another program to create torrents for upload. DVD Santa...Linux can be difficult in that area. I run ConvertXtoDVD under wine and it runs flawlessly as far as converting goes. There are a few display bugs but it works like a charm. Heck, if you can't find a replacement you can try installing DVD Santa under wine. I prefer not to use wine but when there is no alternative I use it. When I use ConvertXtoDVD I have to open K3B and burn the results manually because ConvertXtoDVD doesn't know what the heck to make of my burner in Linux. There is a version of Nero for Linux as long as you have a valid Windows license. The Windows version converts avi to DVD so this one may as well.

---

### Post by Phixion on 2007-06-21
My suggestions:

For music try 'mpd' - it basically runs a daemon on your computer with a list of all your mp3s, you the need a frontend for it, maybe gmpc or sonata.

For torrents... rtorrent is probably the best client there is on any platform - although it's terminal based.

I guess 'gftp' for an ftp client (if you're using GNOME)

---

