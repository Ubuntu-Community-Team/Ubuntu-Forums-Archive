---
title: "Resize Remote Desktoping via VNC"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by DrObviousSo on 2006-11-02
I have recently installed Ubuntu on one of my computers, and need to access it from another desktop running windows XP.  I don't have much experience with *nix, but I was able to get the VNC server on the Ubuntu box working without any real issues.

The problem I have though, is on my XP computer, I have a 19 inch monitor, and on the Ubuntu box, I have a 13 inch monitor.  When I VNC in in, I only get the very small 13 in window on a 19 inch screen.

A friend suggested that there's a way to get around this, but he didn't really know how.  I think he implied that a new Gnome session could be started, instead of just mirroring the 13 inch display, but he didn't have any details.

Any and all advice would be appreciated.

I've tried to set up SSH and Xwindows on the XP box, but I must have turned into an idiot in the last two days, because I can't seem to get that going, even with all the tutorials, man pages, and how to's I can find.

I'm half tempted to just dual boot my XP machine, and use the Ubuntu remote login with that, but that's really sub optimal, because I would really, really like to have my windows environment behind the Ubuntu one, because I have a lot of things there that I still want to have access to.

Thank you for your help.

---

### Post by GotGamble on 2006-11-02
I think your best bet would be to install FreeNX actually, I have used VNC to connect to my Ubuntu box for awhile, and it is not a nice way to control my Ubuntu sessions. 

FreeNX apparently works like terminal services or remote desktop protocol for Windows. My friend told me about it when I described how slow VNC is, and having similar problems with screen resolution and such. 

Look around the forums for the install FAQs for FreeNX, I am not at home, so I don't have a link for you, but there are plenty of guides on the forums for FreeNX, should be able to muddle through.

---

### Post by bmathis on 2006-11-02
try this Howto: 

[http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc+sessions]("http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc+sessions")

this will show you how to setup a remote desktop almost like windows terminal services

---

### Post by DrObviousSo on 2006-11-02
Thank you both for your suggestions.  I'll be trying them out today.

---

### Post by dannyboy79 on 2006-11-02
i didn't read thru EVERY page of that tut so maybe it is there but all I would like to know is how to change the resolution so that it'll fit my screen better. I think i have the opposite problem as DrOb....... because I try to vnc into my Ubuntu machine which is hooked up to a 17 flat panel FROM my little 13 or 14 inch laptop screen. So when I do it, i have to scroll over just to see the right side of the desktop etc etc. Is this easy to fix? I want to vnc session to come up mathcing the laptop resolution which is 800x600, i think. any help would be appreciated

---

### Post by DrObviousSo on 2006-11-02
Well, I managed to get NX working with [this guide from ubuntuguides.org](http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX), and it's working out perfectly.

Dannyboy, I would highly recommend trying out NX, based on the 20 minutes I've been playing with it vs. the days of VNC I've been using.  Specifically, it automatically fits with your current screen resolution, among other things.

---

### Post by dannyboy79 on 2006-11-02
sounds awesome, i'll give it a try, did you install it from the repo's? or did you have to build it from source? if so where did you get it from? oh, is there a client as well as a server for this? I am guessing so but I figured i'd ask.

---

### Post by Marsolin on 2006-11-02
NX is also a lot faster than VNC. [FreeNX]("http://linuxappfinder.com/package/freenx") is an NX server and [NX Client]("http://linuxappfinder.com/package/nxclient") is just what the name suggests. NX Client is also available for Windows, so you can access your Linux system from anywhere.

Neither app is in the Ubuntu repos, but you can get both from the [Seveas]("http://free.linux.hp.com/~brett/seveas/freenx/") repo.

---

