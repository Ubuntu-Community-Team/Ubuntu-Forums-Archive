---
title: "Ubuntu bittorent is horrible"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-15
in windows you can have torrents downloading, and restart your computer, and they will pick up where they stopped.  With ubuntu bittorrent, you have to keep each single torrent window up, and they don't resume when you restart.  Is there a better method for this?

---

### Post by Jareth on 2007-11-15
I have gone through all sorts of torrent clients, mainly cos of my old machine.

At the moment I'm using one called Transmission which is also the easiest one I've been able to use so far. I don't think its in the repositories but if you google transmission and deb, someone has made a deb to install it on Ubuntu.

Hope it helps!

---

### Post by twistedbydesign on 2007-11-15
I use Deluge. if You are using Gutsy it should be in the Add/remove Programs.
It works great for me.
Best of luck!
let me know if you find something better (i'll check back on here)

---

### Post by shirilover on 2007-11-15
Sure, if you want a GUI based solution, try Deluge -> [http://www.deluge-torrent.org](http://www.deluge-torrent.org)
On the other hand, if you can use a console based solution, running rtorrent ( [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/) ) in a screen session will allow you to detach it and still have it running in the background, even if you log out.

---

### Post by fedex1993 on 2007-11-15
also Deluge is a nice easy simple torrent that picks up if you restart. its simple as a click to add. transmission is nice but deluge is even better also if you realy like to use a terminal like i do use rtorrent i use it on my server and also on my desktop.

---

### Post by underdog512 on 2007-11-15
Yea the default torrent application is pretty lacking.  However there are a few others out there that are a ton better than the default.  My favorite is KTorrent which is available through Add/Remove Programs and Synaptic. It offers as much functionality as the more popular Windows clients such as uTorrent. It will pick up where it left it left off just as you are used too.  Just be sure set it up to start at log in. You can accomplish by going to: System -> Preferences -> Sessions, from the desktop.  You might also try Deluge which is also easily available through Add/Remove programs or Synaptic.

Hope this helps!!

---

### Post by geirha on 2007-11-15
deluge, azureus and rtorrent are worth testing. You'll find them in the gutsy repository. Azureus has the most features, but hogs a lot of memory, deluge is smaller, with a little less features, but does the job. rtorrent uses ncurses (text based) which is practical if you want to control it from a different host.

---

### Post by vvlist on 2007-11-15
Here's another vote for deluge. It's great. Fast, simple, powerful with plug ins too.

---

### Post by jordank on 2007-11-15
Tried out deluge, definitely like it.  Good choice, and thanks guys.  Now, i'm thinking of testing out rtorrent, can someone explain how the terminal would work as a torrent client?

---

### Post by rfruth on 2007-11-15
Another vote FOR ktorrent here (Gnome or KDE)

---

### Post by nikolas68 on 2007-11-15
...stiil prefering Ktorrent....

---

### Post by delphiguy on 2007-11-15
I only have one windows application running in my Ubuntu and that is uTorrent.
Until they come with a linux version of it, I'll stick with this one.

---

### Post by jordank on 2007-11-15
Definitely impressed with deluge. nicer than windows bittorrent.

---

### Post by barney385 on 2007-11-15
rtorrent how to:

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by Inxsible on 2007-11-15
> **jordank said:**
> Tried out deluge, definitely like it.  Good choice, and thanks guys.  Now, i'm thinking of testing out rtorrent, can someone explain how the terminal would work as a torrent client?
The deluge available in the repos is 0.5.4.1 and it doesnt support selective file download and such.

you may want to download the latest version from Deluge's webpage. The latest version is 0.5.6 i think

---

### Post by vishzilla on 2007-11-15
Deluge is quite good, though you do get some problems here and there. But, the development is hot, consider sticking with it!

---

### Post by Chilongola on 2007-11-15
My vote is with ktorrent.  Especially when it comes to having it detect a torrent.  Deluge comes in second for me.  Have had problems with it recognizing a torrent.  Never with ktorrent.  Apart from that both have the functionalities I desire.

---

