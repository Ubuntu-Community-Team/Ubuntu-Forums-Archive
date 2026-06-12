---
title: "Banshee with iPod unmount error"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-24
here is the screen shot:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-Banshee.png[/IMG]

troubleshooting tips? explanations? I would love to have 'em. btw, I can eject it fine and listen to it...just its annoying that I have to close banshee and eject it on the desktop every time..

sv

---

### Post by tgalati4 on 2007-09-24
What version of banshee?

>banshee --version

---

### Post by staticvoid on 2007-09-24
Banshee 0.12.1
i'll get 0.13.1 and see if that changes any thing

thanks

---

### Post by tgalati4 on 2007-09-24
I updated to 0.13.1 yesterday, but I have yet to try 3 iPods that I have (mini, 1g shuffle, 2g Nano)

---

### Post by staticvoid on 2007-09-24
Well you are gonna find that your shuffle will work perfect :) The fuzzy ipod icon that pops up (when syncronizing) is fixed, plus it synced and ejected flawlessly :D I do not own those iPods, but if you get stuck you should try GTKpod. That program works great :D

Static Void

---

### Post by tgalati4 on 2007-09-24
GTKpod has always worked for me with my older iPods.  I like Banshee because I can daap share my music collection to my powerbook (running Tiger OS X) on iTunes 7.0.2.  This keeps my iTunes library small and I only use iTunes for stuff that won't play on Linux otherwise.

The autoscrobbler seems to work with Lastfm.com.  It's fun to see related artists come up and explore new tracks without the in-your-face iTunes music store.  To get tracks to play in lastfm I had to upgrade to Flash 9 which was just released.

Of course, I'm running Dapper so getting the new stuff to run can be a challenge.  A lot has changed over the past year.

---

### Post by staticvoid on 2007-09-24
Yeah...
I was trying to add tait to my ipod shuffle but it did not show up. I tried it with gtk and it did work...but not with Banshee. I'll try starting fresh formatting my iPod with iTunes then plugging it in with banshee. gtkpod gives me this error when I plug it in:

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

Is that because of the Apple update for the shuffle? Did it mess with the file? Do they do that so you can't keep up with updates? :P

Static V

p.s. when Ubuntu 7.10 comes out you should def get on the "cutting edge" of things man ;)

---

### Post by staticvoid on 2007-09-24
ooooo :) here is what I did :D I downloaded this .py script and put it on my ipod shuffle, then in banshee I just drag whatever I want onto my pod and then run the py script. Works perfect :D!!

SV

EDIT: Here is where I got the py script:  [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)   in the package comes a .exe file. GET THAT IF YOU WANT TO USE IT ON WINDOWS TOO :D

---

### Post by tgalati4 on 2007-09-24
A good tip indeed.  I also get the error in gtkpod.  I think it has something to do with album art, ratings, last played, etc that is stored in the Apple iTunes database.  I just ignore it.

I'm having trouble getting the lyrics server to work under Banshee 0.13.1.  I installed the lyrics plugin, but I get an error that says can't find gtk-sharp 2.10.0.  Well, 0.13.1 is compiled against 2.8.0.  So much for living on the bleeding edge.  I suppose I could compile from scratch.

Here's a tip for those who live dangerously:

Run banshee --debug in a terminal.  You will get a debug menu item that gives you some info as well as a terminal full of warnings and thread info.

I can certainly appreciate the anti-mono/.net microsoft sentiment, but Banshee 0.13.1 really works!  Search is pretty snappy with 3K tracks and counting.

---

### Post by staticvoid on 2007-09-25
Yeah... The bleeding edge can... make you bleed, if you will :P. Amorak does lyrics...but we're talking about banshee ;). it *is* a fast search!! :D
I'll try the debug thing.

sv

---

