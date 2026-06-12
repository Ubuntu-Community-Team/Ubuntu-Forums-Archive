---
title: "I can't play my X-Files DVDs on my laptop anymore!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by DrTaylor on 2007-06-21
I put them in the drive and they just won't load. I'm serious. It knows there's something there, it keeps trying to load the drive, but then... nothing. It just keeps trying to load. When I try to open the drive it says "cannot mount," and then "there's probably no media in the dirve".

The problem, I think, lies in the fact that it's a "DVD ROM" and not just a normal DVD. How do I get beyond this to successfully watch said DVD on my computer?

For the record, I got it to work once about a month ago, after eighteen tries.

---

### Post by Sokraates on 2007-06-26
I assume, you have all the required software installed. Are you shure, the drive is okay? 

I experienced something similar (when still using windows) with my CD/DVD-reader. From one day to another it could read CDs, but not all DVDs and over time this became worse. A friend of mine then told me, that the mechanics or optics or whatnot were broken, so I bought a new drive, eventually. 

Even tried a firmware update to no avail. No ... wait the update did do something: it went wrong and totally busted the player. :D

---

### Post by techno-mole on 2007-06-26
im having similar problems with my dvd drive.
do you vlc installed ? (its plays dvds and such) see if i put a dvd film in the drive nothing happens, the drive will just spin a little, but if i open vlc and then click on file and then open disc it opens up another box with some options in it and then i just click ok and away it goes, but if you go looking for the mount points you cant find anything.
ps - vlc is the only application i have that will work for me, the other medi player/dvd players i have like mplayer movie player dont work as they cant find the disc.
sorry - you can do a search in synaptic for vlc, or i think sudo apt-get install vlc should work.
also one other thing, i take it you have all the right codecs and such like installed ?
cheers.

---

### Post by lisati on 2007-06-27
You might want to check which libraries you have installed. There's a link in another thread with further details, do a search on "can't play DVDs" on this forum.

From memory, the needed libraries include:
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

They can be installed from a terminal window with something like:
sudo apt-get install libdvdcss2
sudo apt-get install libdvdnav4
sudo apt-get install libdvdplay0
sudo apt--get install libdvdread3

You also might want to try
sudo apt-get install totem-xine

---

