---
title: "Qupzilla browser on PPC"
date: 2014-11-20
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-11-20
I installed this browser and am just impressed with the performance I am getting on my PowerBook G4 with it. You will need to compile it from source and download the needed dependancies first but I would some feed back on it. My only issue is that geck-media plugin I use on firefox does not seem to be compatible Qupzilla. I am also having the same issue with midori as well and post a thread in the multimedia forum here with no response. Anyways below are the dependencies for anyone who would like to try.

openssl libssl-dev libqt4-webkit libqt4-dev libqt4-sql-sqlite g++ pkg-config hunspell

Here is where you can get the source [http://www.qupzilla.com/download#source](http://www.qupzilla.com/download#source)

---

### Post by este.el.paz on 2014-11-22
@r-l:

Haven't tried it yet, but I did see "qupzilla" listed in the "synaptic package manager" yesterday in my iBook running 14.04 . . . so I don't think it has to be "compiled"???  Of course that could be "the fun of it" . . . .

e.e.p.

---

### Post by rican-linux on 2014-11-22
It is not in the 12.04 packages so I had to compile it from source.

---

### Post by ibjsb4 on 2014-11-22
I find it easier to use the ppa.

[https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla?field.series_filter=precise](https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla?field.series_filter=precise)

---

### Post by dr.david.maloney on 2014-11-30
It's in Jessie and Sid, so if you don't mind installing pure Debian on your 'buntu system that is easier than compiling it. But there is no fun if you don't compile your own stuff....

---

### Post by rican-linux on 2014-12-01
I moved to Jesse and yes while it is easier is there some fun in saying you compiled it yourself ;)

---

### Post by rsavage on 2014-12-02
What's the state of webkit in Jesse then?  Do you get crashes?  Qupzilla crashes on startup in Trusty, although I haven't tried the version in the proposed repo.  I'm assuming it is a webkit problem.

Rican-linux, I see you got a mention on the un-liberated website!  That guy (Zen) is full of hate, I wouldn't take everything he says as gospel.  It's an awful site.

There is no perfect PowerPC linux distribution, and so whatever you choose, to get the best out of it you're going to have to do some compiling.  I've just compiled Mate under Trusty, and I have to say marco on my machine outperforms openbox by a mile!  Combined with compiz0.8.* it is even better.  You won't find that on the un-liberated site!

---

### Post by rsavage on 2014-12-02
Webkit bugs - [https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1274167](https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1274167)

---

### Post by rican-linux on 2014-12-02
Qupzilla and Iceweasel work fine in Jesse. Midori and surf are crashing on me. I already put a bug in for that. The biggest issue I had was Xvid. Under Jesse you to enable KMS for it to work. Well got that workkng but 3D acceleration was not. I discovered that to get it working I needed to my display from 24 to 16. It worked but at a cost. There were two patches suggested to apply to Mesa. I applied them recompiled Mesa and installed but still no go. I need to stay at 16. 

All in all though at least on my PowerBook G4 I have really liked Debian with LXDE.

---

### Post by rsavage on 2014-12-03
How does LXDE perform?  Do you have slow window dragging? -and do you get the same in Lubuntu 14.04?

---

### Post by rican-linux on 2014-12-03
It runs great! No issues with window dragging.

---

