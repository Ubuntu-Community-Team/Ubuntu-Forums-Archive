---
title: "A beginners Guide help needed"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by HobbitCy on 2007-06-01
Hello all.
My names Christopher AKA HobbitCy.
Iv just come across to linux, always wantted to never thought i could, till ubuntu.
iv seen ubuntu and kubuntu, seems i must be  a GNOME guy.

So the main reason for the thread is i want to sort get a beginners guide kind of thing going.
To get the idea i have an after format disk for windows which has all my programs on it that after i install windows i pop the disk in and install my fav progies.

i want to set up something the same for ubuntu so that if i go to a mates house i can set him up with everything in one go and get him using ubuntu.

I have to also say that since i have had some experiance coding html/php that i love the use of the terminal i thought it was magic telling it to get_ap stuff.

so not to make my first thread to long winded as i normaly do i ask for all to join in and help my on my quest to get started.

ill start of with what would be needed on my day to day basic usuage

music player - winamp in windows
video player - bsplayer/vlc player/ windows media player/ rmalternative ( im happy with vlc player) need something that can change aspect ratio properly vlc doesnt seem to do it. (codecs- xvid mainly)
download - newsleecher and bitcomet - in windows
internet - firefox so we are okay there native to ubuntu :P
office work - open office works just fine from a first look
comunitation - msn and irc - in windows

so to close, there are two ideas im thinking of
the first to complie a txt file with all the terminal comands to download and install all the above software
or to download the software and burn it to a disk and then run a terminal comand to install all of them.
thanks guys

---

### Post by aysiu on 2007-06-01
[http://www.ubuntuguide.org](http://www.ubuntuguide.org) is your friend.

---

### Post by brooksbp on 2007-06-01
sure you can create your own packages... 

but I think you're better off sticking to something like this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

people already are doing what you want to do. reinventing the wheel isn't always the best

---

### Post by HobbitCy on 2007-06-01
thanks for the links
i dont think i want to reinvent the wheel
or create my own package
i just want a quick and eazy way to get everying into the system after iv installed it.

---

### Post by Cyvros on 2007-06-01
Ubuntu Guide suggestions thirded. ;)

> **HobbitCy said:**
> music player - winamp in windows
video player - bsplayer/vlc player/ windows media player/ rmalternative ( im happy with vlc player) need something that can change aspect ratio properly vlc doesnt seem to do it. (codecs- xvid mainly)
download - newsleecher and bitcomet - in windows
internet - firefox so we are okay there native to ubuntu :P
office work - open office works just fine from a first look
comunitation - msn and irc - in windows

A few quick recommendations:

**Music player** - XMMS and BMP are both similar in interface to WinAmp (indeed, XMMS started off **as** FreeAmp)

**Download** - Don't know about NewsLeecher, but I'd suggest using uTorrent through Wine for torrents. Either that or something like BitTornado.

**Communication** - MSN and IRC can both be taken care of by Pidgin (nee Gaim).

> so to close, there are two ideas im thinking of
the first to complie a txt file with all the terminal comands to download and install all the above software
or to download the software and burn it to a disk and then run a terminal comand to install all of them.
thanks guys

I know the second can be done (can't remember tool it is, though, but I'm fairly sure it's built-in) - you can download packages to a CD for easy reinstallation on another computer or if you reinstall.

For the first, it's fairly easy just to write a simple bash script for downloading and compiling apps (don't know about using it for apt, but you should be able to).

---

### Post by HobbitCy on 2007-06-01
thanks guys so iv looked around and iv seen some screen shots and made a small list

winamp => XMMS (looks like winamp)
bsplayer/vlc player => VLC Player
nero => nerolinux 
firefox => firefox
office => Open Office Comes with Ubuntu
newsleecher => found Pan or hellafox+hellanzb
bitcomet => Azureus 
msn => aMSN 
mirc => xchat

is that a good list of programs?


adding there commands know as iv found them

sudo apt-get update
sudo apt-get -y install xmms
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
sudo apt-get dpkg -i  nerolinux-3.0.0.0-x86.deb
sudo apt-get pan_0.119-1_i386.deb
sudo apt-get amsn_0.96+dfsg1-0ubuntu2_i386.deb
sudo apt-get xchat_2.8.0-0ubuntu4_i386.deb

i havent tested these yet since im at work in windows please correct them if they are wrong thanks
this is the kind of thing i want to compile so you can just copy past the whole thing and get them all

---

### Post by aysiu on 2007-06-01
You don't have to keep updating and installing separately. You can just do something like ```
sudo apt-get update && sudo apt-get install xmms vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2 xchat amsn pan
``` That one command will install all the above packages.

By the way, as far as I know, you have to *pay* for NeroLinux. Why not just use K3B instead? ```
sudo apt-get install k3b
```

---

### Post by HobbitCy on 2007-06-01
thanks you aysiu thats the best im  going tio try it know

---

### Post by HobbitCy on 2007-06-02
i checked out k3b looks simple and eazy to use so i suppose that will replace nero
only thing i couldnt get was a nice alterantive to newsleecher :(

---

### Post by Cope57 on 2007-06-02
> **HobbitCy said:**
> i checked out k3b looks simple and eazy to use so i suppose that will replace nero
only thing i couldnt get was a nice alterantive to newsleecher :(


Newsleecher? something like [Liferea]("http://liferea.sourceforge.net/"), [Blam]("http://developer.imendio.com/projects/blam"), [RSSOwl]("http://www.rssowl.org/"), and [Straw]("http://www.gnome.org/projects/straw/") are a few that I know about.

Others may post more links for a news reader, and give their opinions of which they think is best.
sudo apt-get whichever one you would like to try, or use synaptic and use the "search" feature to see if it is available in your repositories.
Just choose the one you are most comfortable with.

---

### Post by hyper_ch on 2007-06-02
k3b rocks and as audio player I'd recommend amarok...

---

### Post by HobbitCy on 2007-06-04
i use newsleecher for nzb files
in the end i got grabit to work in wine not the best solution but better than nothing
also amarok looks cool too 
took me 4 hours of working on newsleecher and pan and hellanzb ans SABnzbd to get no were fast till i tried grabit
very disapointed that its so hard to get a nice gui for a newsreader with simple nzb support
wish i could get newsleecher to work

---

