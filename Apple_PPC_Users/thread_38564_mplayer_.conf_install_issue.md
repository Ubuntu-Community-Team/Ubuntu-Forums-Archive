---
title: "mplayer .conf install issue"
date: 2005-06-01
forum: Apple PPC Users
---

### Post by trash on 2005-06-01
sorry for yet another mplayer question but I followed the Ubuntu powerpc guide and everything seemed to go without a hitch until i went looking for the mplayer.conf which doesn't exist in /etc/mplayer or anywhere else.
i've tried the mplayer-g4 and the mplayerppc but nothin... but it does install fonts and skins in /usr/share/mplayer. 
anybody?

---

### Post by pvz on 2005-06-01
I noticed as well that installing the mplayer-g4 and mplayerppc doesn't seem to install any binaries. The files are way too smal for that too. So I decided to compile my own, which works fine when I use --disable-altivec as a configuration flag on my iBook G4. For a graphical interface, use --enable-gui, and don't forget to download and install fonts and a skin from the mlayer site. Or you can use the ones that were installed before, I suppose.
You could try to add the ppc repository for mplayer as well, but that's for Debian unstable, so there can be glitches with dependencies.
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/
Besides, compiling your own is more fun :-)

---

### Post by trash on 2005-06-01
ah i see that kinda sucks
I'm not crazy about mplayer I just want to watch one dvd iso... S Wars :P
i might give it a shot though i'm not crazy about compiling either lol

I thought I had installed it from
deb [http://honk.physik.uni-konstanz.de/...nux-ppc/debian/](http://honk.physik.uni-konstanz.de/...nux-ppc/debian/) mplayer/
before but i guess it was when i was with Warty and it did work, but since it wasn't in te ubuntu guide I figured it no longer worked.. will go that way.

thanks!

---

### Post by pvz on 2005-06-01
In that case, just apt-get install vlc, that should give you the vlc-player, which plays about everything, including dvds, and is leaner and meaner than mplayer.
[http://videolan.org/](http://videolan.org/)

---

### Post by trash on 2005-06-01
SWEET! I know what i'm going to watch tonight :D

million thanks pvz

---

### Post by trash on 2005-06-02
Um, it's VLC from this day forth... it's awesome!
the movie was pretty good too:D

---

### Post by pvz on 2005-06-02
Jup, it's pretty cool :-) But sometimes it won't play some files like Windows .wmv files, and mplayer will, or vice versa. So I still like to keep both players around even though I prefer vlc..

---

