---
title: "few questions about amarok"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-03-26
here we go:

1. Does Amarok work well on ubuntu?

2. Is it really as good as it is supposed to be?

3. I plan on getting amarok to play music of an external, networked(mounted) HD, does Amarok have a feautre where it will automatically add new music in the target directory to it's library (a bit like that great feature in picasa - but for music)?

4. That last one is really essential, so if not, what music player would? I've already tried lTunes (horrible and slow), Songbird (nice, but too slow and buggy) and Banshee (kept on freezing up)

thanks, all replies are really appreciated...

---

### Post by Lacrimstein on 2008-03-26
1. Yes :)
2. This one is an opinion question; But in my case - Yes!
3. I don't know about networked, but i can play music fine from my other partitions, and Amarok doesn't freeze when they are unmounted - it simply doesn't show the songs on those partitions if they aren't mounted. Should be the same for networked drives.

---

### Post by Paqman on 2008-03-26
> **benji.ijneb said:**
> 
1. Does Amarok work well on ubuntu?

Yes!
> 
2. Is it really as good as it is supposed to be?

Yes!
> 
3. I plan on getting amarok to play music of an external, networked(mounted) HD, does Amarok have a feautre where it will automatically add new music in the target directory to it's library (a bit like that great feature in picasa - but for music)?

Yes!
I have all my music on network storage. You can tell Amarok how regularly to scan the library for changes.

---

### Post by POW R TOC H on 2008-03-26
It worked fine for me, but I have rather basic needs when it comes to music (just shuffle the bloody playlist) so I soon dumped Amarok and went back to Rhythmbox... Why use cannons to shoot pigeons?

---

### Post by forestpixie on 2008-03-26
> Why use cannons to shoot pigeons? Because it looks really funny when they try to escape?

I haven't managed to get anything other than amarok to do what I want - which is to remember the playlist and remember where it got to in it. Tried a lot off different ones - but they all fall down on that.

On the other hand if someone knows how to get one to do so I'd like to know.

---

### Post by benji.ijneb on 2008-03-27
thanks for all your replies!
one more thing, though, when i try to install amarok, it wants to install all of this:

> amarok amarok-xine fftw3 kdebase-bin kdebase-kio-plugins kdelibs-data
  kdelibs4c2a kdesktop libarts1c2a libartsc0 libavahi-qt3-1 libdbus-qt-1-1c2
  libgpod2 libifp4 libkonq4 liblua50 liblualib50 libmtp6 libmusicbrainz4c2a
  libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libpq5 libpulse0
  libqt3-mt libruby1.8 libtunepimp5 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxcb1 libxine1 libxvmc1 mysql-common python-qt3 python-sip4 ruby ruby1.8


that's just ridiculous! it's 160mb! it's practically the whole of KDE!

does everyone get this? will this install KDE?

thanks again...

---

### Post by forestpixie on 2008-03-27
Yep - that's what you get if want to use it. No this won't install KDE - but it is installing what it needs to run.

---

### Post by meindian523 on 2008-03-27
Everyone gets that,only you don't KDE with it,for that you need to install kubuntu-desktop.

---

### Post by hyper_ch on 2008-03-27
> **benji.ijneb said:**
> 1. Does Amarok work well on ubuntu?
Yes

> **benji.ijneb said:**
> 2. Is it really as good as it is supposed to be?
Even better

> **benji.ijneb said:**
> 3. I plan on getting amarok to play music of an external, networked(mounted) HD, does Amarok have a feautre where it will automatically add new music in the target directory to it's library (a bit like that great feature in picasa - but for music)?
Yes, for larger collections (2000 songs and more I'd use mysql instead of sqlite)

> **benji.ijneb said:**
> that's just ridiculous! it's 160mb! it's practically the whole of KDE!
KDE Desktop is about 500 MB

---

### Post by linux phreak on 2008-03-27
160 mb is too much for a music player

---

### Post by forestpixie on 2008-03-27
160mb isn't for the music player is it - amarok is about 20-30Mb. It's for the dependencies. 

I think that 4Gb is too much for windows media player - but that's the way it is.

---

### Post by meindian523 on 2008-03-27
yup,that's mostly accurate.

---

### Post by benji.ijneb on 2008-03-27
> **hyper_ch said:**
> 
Yes, for larger collections (2000 songs and more I'd use mysql instead of sqlite)


how do i use mysql, and what does it do?

---

### Post by meindian523 on 2008-03-27
MySQL is a DBMS,it manages your collection,don't worry,amaroK gives you the choice of which DBMS to use in it's Settings,you will come across it when you build your collection.

---

### Post by meindian523 on 2008-03-27
Correction:Rather,you will come across it when you tell amarok to build it's library by scanning whatever your folder you have put your music in.

---

### Post by hyper_ch on 2008-03-27
you'll have to install mysql server first and setup an amarok db before you can alter it in amarok itself...

---

### Post by meindian523 on 2008-03-27
hyper_ch:
Doesn't SQLite need that?IIRC,I just selected SQLite and it did everything without bothering me anymore.

---

### Post by hyper_ch on 2008-03-27
no, but at a certain data storage sqlite just becomes a lot less effective than a mysql database.

---

### Post by meindian523 on 2008-03-27
hmmm,thanks for that.Could you elaborate?

---

### Post by jamieh on 2008-05-06
> **forestpixie said:**
> 160mb isn't for the music player is it - amarok is about 20-30Mb. It's for the dependencies. 

I think that 4Gb is too much for windows media player - but that's the way it is.

WMP is 4gb?? My GOD!!

---

