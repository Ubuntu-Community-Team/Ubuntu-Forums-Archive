---
title: "[SOLVED] Downloading Codecs and Long startup"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by triskit on 2008-01-30
I've just installed ubuntu on my old laptop and it cannot play any media files. It shows pictures just fine, but music and movies of any formatt do not seem to work on it. 

When I try to play them, A window pops up about downloading a suitable codec and leads me to a "install multimedia codecs" window.

This window lists two plugins
1/ GStreamer extra plugins
2/ GStreamer ffmpeg video plugin

when i try to highlight the box that corresponds to either of these codecs, a "confirm installation of restricted software window pops up. If I select confirm, A new window pops up saying " the list of aplicatons is not available" I can click refresh or cancel.

When I click refresh, I enter my admin pass and It puts me right back where I started at the "install multimedia codecs" window. This happens no matter how many times I do it, and has been ahppening since I installed the OS three days ago. Ive tried avery combination of the options that are given to me 
(clicking cancel instesd of refresh, etc) and nothing is working.


Similarly, when I try to listen to music on myspace music pages, the music player says that I need additional plugins to use it. When I click on this, it shows a list of available plugsins (aadobe flash, gnash SWF) when I select either one, a window pops up saying "Can not find 'plugin name here'

I close that window and it says that what I clicked on has been installed and firefox needs to restart, but when i restart firefox or the computer, the player still says that it is missing the plugin

Am I dong something wrong or what?


SECOND PROBLEM

the computer also takes about three minuets to get to the login screen from start up... decently longer than it did w/ XP... is this normal?


Background Info: the computer is an old dell inspiron 600m w. 512 mb ram, a86, nothing spectacular, but windows XP used to work fine on it.

It is connected to the internet through my college dorm's wireless network.


Sorry for the book/ Thanks for your time

-Tristan

---

### Post by jordanmthomas on 2008-01-30
For your first problem I might not be so helpful.  What I would do is this:
```
gksudo gedit /etc/apt/sources.list
```
and delete the # from lines that start with deb
Then, run
```
sudo apt-get update
```
and try again.

Your boot speed problem:  Ubuntu isn't the fastest booter I've seen.  It takes a minute and a half or so to boot for me, but with my Arch install I can be on the internet browsing in 26 seconds.  Three minutes seems a bit long, but Ubuntu isn't built for speed.

You may want to disable services you don't use / need.  Not using debian in so long, I am not the one to tell you exactly how to do it, but a quick lookup on the Internet should give you what you need.  Does it slow down when a particular service is starting up (or does Ubuntu have a splash screen that hides this?) ?

---

### Post by eolson on 2008-01-30
On your Codecs try
    Applications > Add Remove

in the upper right corner select "All Available Applications"
In the lower left corner "Preferences"  Check all the boxes except source code and uncheck the cd box if it is checked


On your slow start up here is what fixes most of them

[http://ubuntuforums.org/showthread.php?t=662592&highlight=slow+boot](http://ubuntuforums.org/showthread.php?t=662592&highlight=slow+boot)

---

### Post by triskit on 2008-01-30
Thanks for the quick replies. The thing in Add/ Remove programs Preferences seemed to solve the first problem. The codecs downloaded just fine after that and seem to be working well. 

The computer is now installing a bunch of updates now, but when it is done ill try some of the things that you all suggested for the startup

During the startup, the screen seems to be completely blank for about a minuet or more... the backlight doesnt even seem to be on... I believe that this happens before anything else, but it might happen mid start up... Ill check that out again when the updates finnish installing

Thanks a lot!

---

### Post by eolson on 2008-01-30
that seems to be a fairly common problem with Gusty and laptops.  The good new is the fix works.

---

### Post by jordanmthomas on 2008-01-30
Definitely check out eolson's link then, it seems like it would be helpful for you.

---

### Post by triskit on 2008-01-30
Updates fnnished and i tried that link.

 Along with having a much more visually pleasing screen during startup, it now only takes 43 seconds to get to the login screen and another 35 seconds to get logged in and load everything. Not too bad considering the quality of the hardware (or lack thereof)

Thanks a lot, Both problems solved in about an hour!

---

### Post by eolson on 2008-01-30
Don't forget to mark the thread solved.

---

