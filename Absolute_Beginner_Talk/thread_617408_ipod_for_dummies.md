---
title: "ipod for dummies"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jd8001 on 2007-11-19
Hey,
     I was thinking about getting an ipod and was wondering how exactly it worked with ubuntu. I tried downloading itunes and running it in wine but to no avail, thus is there a replacement program out there that is used to communicate with the device? And how am I supposed to download music (legally) w/o itunes? Thanks

J.D

---

### Post by zach12 on 2007-11-19
Try the amazon store
haven't used it my self(no videos) but read the it works with linux

---

### Post by laidback on 2007-11-19
Amarok reads and writes to an ipod, well it does to mine.
Install via Synaptic.
You cannot run itunes in Linux as far as I know.

---

### Post by LowSky on 2007-11-19
older versions of itune 7.2 will sorta work, but it is a real pain.. please dont try unless you know linux  and wine really well

Amazon.com is great place to buy MP3s, try them out. As for getting them onto an iPod use Banshhe, exaile, amarok, gtkpod, and many more programs can help with that.

---

### Post by jd8001 on 2007-11-24
Okay... so I got ipod nano 8gb and I can't get it to work with Amarok, gtkpod, or banshee for the life of me. I was able to use itunes to load some stuff, but then when I tried to migrate it over to my linux machine It deleted every song on it. I disabled auto synching and formatted over to the fat32 file format with itunes. 
   So here's the breakdown of what I got to happen in banshee (which I think was my least unsuccessful attempt at anything) I moved files into a music folder and told the program to synch with my ipod. It appeared to be doing something and when it was finished I could see my music when I clicked on the ipod tab, but when I tried to play my music with the ipod it claimed there was no music on the device. I would guess that it didn't update the database properly because the music was on it (even Rythmbox could find and play the music). 
    Another fiasco I ran into is that it seems that I can't find the same version of gtkpod that everyone else has. Mine has no read or synch button, but it does have a load ipod button. Anyway I had a similar experience with gtkpod, i.e. it would store music on the device, but the device could not find it. 
    So my questions: what do people use with their ipods that work? Am I missing a library (more specifically the libgpod library)? Is there any hope? 


J.D Beck

---

### Post by bluepowder7 on 2007-11-24
i don't have an iPod, but you could try swapping the Apple's own firmware with some version of RockBox firmware.  i've heard that it's quite good.  don't use it on my player, since i've got a Cowon iAudio U3 that works as a USB mass storage device - drag-n-drop.

---

### Post by kryrinn on 2007-11-24
There is a crack for the new-gen ipods, but it is not readily availalble, or easy, I would guess.

I bought a new ipod classic yesterday, and spent four hours trying to get mine to work...  and finally just copied all of my music over to a vista machine and loaded it that way.

If you have a win machine around, don't bother trying to get it working with ubuntu at the moment.  Not going to happen lately, thanks to Apple.

Although I heard Apple is supposed to release a developer's package for the ipods in Feb, anyone else heard that?  That should help in allowing linux to use the newer ipods...

---

### Post by Mike Armstrong on 2007-11-25
I have had great problems trying allsorts of software with a Gnome based Gutsy install. I have installed and looked at gtkpod, banshee, exaile, amarok (with KDE dependencies installed), songbird and listen. Eventually I have settled on banshee for music file transfer ripping and collecting album art, gtkpod for manipulating and creating playlists and Gpixpod for transferring photos though it continually installs all the photo files and dirs to the calendar folder of my ipod (a simple drag and drop into a newly created "photos" folder in the root of the ipod sorts that. It's not pretty and not slick but it works. 
exaile: looks flash  but after following all the instructions adnd advice etc I could get it to see the ipod play my music files etc but not transfer anything ...gave up.
Listen: easier to install and set up than exaile but end result ditto ...see above.
Songbird: pain to install for a newbie need to create a dir and install to it, then if album art required the java install instructions (which are inadequate as they don't detail the need to create a dir to put the download file in and install to), gave a perfect mozilla jre install in firefox but not in songbird ...?what? Also could not rip (it doesn't) or transfer files (it should),
Conclusion : ipod support is problematic and if you are a gnome install user don't be envious of the KDE Amarok bunch  ...often it is just as flakey as the rest of the softwware on offer. 
Tip: If you are using Banshee and it reformats the database on your ipod don't let it sync to itunes after, it will overwrite the  db file and when next connecting to banshee it may work or may make all your  music files appear 0.00secs in length and unplayable!
If you just want to back up your music use gtkpod it is unintuitive and ? clunky but powerful. I still have not found a way to make it see my music library but it reads my ipod accurately every time I connect and playlist manipulation is drag and drop.
As for podcasts ...yeah right!

---

