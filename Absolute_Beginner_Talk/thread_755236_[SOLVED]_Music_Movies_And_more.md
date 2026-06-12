---
title: "[SOLVED] Music Movies And more?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by tmofarns on 2008-04-14
so i recently built a new comp and my buddy aske me to check out ubuntu for the os. I LOVE IT! everything is much cleaner and faster i hit a lil over 600kbs while downloading last night! my only issue so far is u built this comp for my music and movies you know mostly storing and listening and view . only issue is i cant find a player or mixer anywhere that i actually enjoy using. and then when i do find one i really want to try i dont know how to install it, i feel like a whiny noob but i dont know where to start!

---

### Post by OldTimeTech on 2008-04-14
If you have the names of the programs you have found, you might go to system->administration->Synaptic Package Manager.  Go to tools make sure you have all the repositories checked.  Then use search and type in the name of the program your wanting to check out.

---

### Post by Aeph on 2008-04-14
A great way to find programs is to go to the Applications menu (top left of screen) and go to add/remove programs at the bottom. You'll also probably want to go to system->administration->software sources and check some, if not all, the boxes if you haven't already. If you're looking for media, go to sound and video (back in add/remove programs) and you'll get a list of programs that you can easily install by selecting them and clicking install. For programs that you already know about, you can go to system->administration->synaptic package manager and search for the program. This is sometimes more useful than entering apt-get into the terminal because it gets all of the dependencies for what you want to install.

As for a good music player, I recommend Amarok. Video: haven't really found anything better than Mplayer.

---

### Post by temujin77 on 2008-04-14
I'm a n00b myself, so perhaps we can learn together :)

For movies, I use VLC Player.  I find it very robust; I never run into codec missing type of errors, and it handles my multiple audio track movies perfectly (I have many foreign DVDs that I ripped to my HD with multiple audio tracks on them).  The library function is lacking, but I like the player itself nevertheless.

If you're looking into multimedia stuff, and can dedicate a box to it, I recommend MythTV.  I just installed Mythbuntu over the weekend and absolutely love it!

---

### Post by Inxsible on 2008-04-14
Tell us which app you want to install and maybe we can tell you how to install it.

---

### Post by northern lights on 2008-04-14
A comprehensive test of Linux audio players can be found [here]("http://www.pcworld.com/article/id,128636-page,1-c,linux/article.html").

For video +1 for VLC from my side.

---

### Post by artblakey on 2008-04-14
For video the best two really are VLC or mplayer... I'd give my vote to mplayer but that isn't based on much more than personal preference.

The best audio player depends on what your looking for, if you want a program similar to iTunes your best options are Rhythmbox on GNOME or Amarok on KDE, Amarok being the far more advanced of the two. If you're looking for a more lightweight music player on GNOME try looking at Muine, it's quite different to iTunes-style players but once you get used to it (which doesn't take long) it's a great app.

---

### Post by tmofarns on 2008-04-14
[SIZE="3"]well not to be stuck in the xp mindset but winamp. i love the interface the program works flawlessly and can be made to be my own thats all i really want to find is something that looks and works like winamp [/SIZE]

---

### Post by Inxsible on 2008-04-14
> **tmofarns said:**
> [SIZE=3]well not to be stuck in the xp mindset but winamp. i love the interface the program works flawlessly and can be made to be my own thats all i really want to find is something that looks and works like winamp [/SIZE]XMMS (no longer supported or developed -- i think) or Audacious are the two which are very much like Winamp.

---

### Post by stchman on 2008-04-14
> **tmofarns said:**
> so i recently built a new comp and my buddy aske me to check out ubuntu for the os. I LOVE IT! everything is much cleaner and faster i hit a lil over 600kbs while downloading last night! my only issue so far is u built this comp for my music and movies you know mostly storing and listening and view . only issue is i cant find a player or mixer anywhere that i actually enjoy using. and then when i do find one i really want to try i dont know how to install it, i feel like a whiny noob but i dont know where to start!

For music, I use Rhythmbox to organize my music.  VLC is a great media player and supports all the formats.

To play MM you need to install the proper CODECs and DVD support.

CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

MP3 and CD ripping
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

DVD playback
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This all works well.

---

### Post by tmofarns on 2008-04-14
well too bad i have to go to work cant wait to get home and try this stuff out some more. anyone know how i can increase my bandwith? i toldd my buddy about hitting 600kbs he says that weak sauce should be around 750 or 8

---

### Post by ranlil on 2008-04-14
I can't seem to have a bit of luck installing mplayer or vlc.  On vlc is say it won't install nox and a ttf.  Getting a little frustrated with gutsy.

---

### Post by artblakey on 2008-04-15
@tmofarns

...the amount of bandwidth you have has nothing to do with what OS you're using, it's down to external factors (your ISP, broadband package, modem/router, your phone lines capability etc). There are ways to make sure you're getting the maximum possible download speeds in certain programs, especially bittorrent clients, but if your connection's maximum speed is 600k you aren't going to be able to get any higher than that. Search for speed test websites to give yourself an idea of how fast your connection actually is, and remember that a connection speed of 6000k equals an actual maximum download speed of 600k (roughly). Another thing to remember when trying to achieve higher download speeds is that slow speeds are often not a result of anything on your computer but rather based on the limits of the server you're downloading from.

---

