---
title: "Is there any truly &quot;light&quot; music player for Ubuntu?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by JPorter on 2007-07-21
I'm using Listen at the moment, and with my full library loaded (40,000 tracks) it slows to a crawl and the whole user interface develops a slight lag.  It's clocking ~255mb in memory for Listen alone, but it feels like more than that.

I have tried Exaile, Rhythmbox, and AmaroK, and they all have their own issues.  I can't remove tracks from the library in Exaile, Rhythmbox takes three hours to import the library (it's on an external), and AmaroK... well, AmaroK is nice but it's a KDE app and it tends to bring the whole KDE chain gang to the party, as well as a MySQL database service running in the background.


Is there ANY truly "light" music player for Ubuntu?  I don't want an iTunes clone with a library... I want a Foobar2000 clone, where I can drag and drop a whole directory structure into an app and have it be able to function smoothly with 40,000+ tracks in its playlist, and randomize if I want, while only taking 20-30mb in memory.  


Help?   Thanks!!

---

### Post by benx009 on 2007-07-21
don't know if it's what you're looking for, but there is banshee...

also, wine should be able to run foobar2000 if you really like it that much....

---

### Post by Motoxrdude on 2007-07-21
Have you tried xmms? It's similar to winamp.

---

### Post by JPorter on 2007-07-21
> **benx009 said:**
> don't know if it's what you're looking for, but there is banshee...

also, wine should be able to run foobar2000 if you really like it that much....

From what I understand, Banshee is pretty much like Rhythmbox/Exaile/Listen/Amarok/etc ?   Or am I wrong on that?


The Wine thing really doesn't appeal to me.  I'm not looking to run Foobar on Ubuntu... I'm looking for a simple native app that will behave as reliably.

---

### Post by Nythain on 2007-07-21
hehe... mpd coupled with ncmpc or mp321 (i think thats whats it scalled)
doesnt get much lighter than that as far as i know

---

### Post by jimrz on 2007-07-21
> **JPorter said:**
> I'm using Listen at the moment, and with my full library loaded (40,000 tracks) it slows to a crawl and the whole user interface develops a slight lag.  It's clocking ~255mb in memory for Listen alone, but it feels like more than that.

I have tried Exaile, Rhythmbox, and AmaroK, and they all have their own issues.  I can't remove tracks from the library in Exaile, Rhythmbox takes three hours to import the library (it's on an external), and AmaroK... well, AmaroK is nice but it's a KDE app and it tends to bring the whole KDE chain gang to the party, as well as a MySQL database service running in the background.


Is there ANY truly "light" music player for Ubuntu?  I don't want an iTunes clone with a library... I want a Foobar2000 clone, where I can drag and drop a whole directory structure into an app and have it be able to function smoothly with 40,000+ tracks in its playlist, and randomize if I want, while only taking 20-30mb in memory.  


Help?   Thanks!!

try audacious, available from the repos ... similar to WimAmp ... have it running and just checked System Monitor and it shows 10Mb memory use. used to use xmms but it is no longer being developed, audacious is a fork that still is, and had some issues trying to use it on feisty.

---

### Post by RomeReactor on 2007-07-21
> **Nythain said:**
> hehe... mpd coupled with ncmpc or mp321 (i think thats whats it scalled)
doesnt get much lighter than that as far as i know

Yes [it does]("http://mask.tf.hut.fi/~flu/cplay/")! Look for Cplay in Synaptic. or from the command line:
```
sudo apt-get install cplay
```
On a more serious note, I agree that Audacious is probably the way to go.

---

### Post by init1 on 2007-07-21
> **Motoxrdude said:**
> Have you tried xmms? It's similar to winamp.
XMMS is my favorite. It's light, easy, and has all the features I need.

```
sudo apt-get install xmms
xmms

```

---

### Post by Flashgordon20 on 2007-07-21
You can try sonata

[http://www.getdeb.net/app.php?name=Sonata](http://www.getdeb.net/app.php?name=Sonata)

Description
"Sonata is a lightweight GTK+ music client for the Music Player Daemon (MPD). It aims to be efficient (no toolbar, main menu, or statusbar), user-friendly, and clean."

---

### Post by init1 on 2007-07-21
> **RomeReactor said:**
> Yes [it does]("http://mask.tf.hut.fi/~flu/cplay/")! Look for Cplay in Synaptic. or from the command line:
```
sudo apt-get install cplay
```
On a more serious note, I agree that Audacious is probably the way to go.

cplay is only a frountend. I may be small, but I relies on other apps to actually play the music.

---

### Post by JPorter on 2007-07-22
Thanks for the help, guys!

Audacious is proving itself to be pretty much what I was looking for.  Light, fast, good audio quality, no major frills.

I'll let you know how it does with 40k tracks... it only has about 200 at the moment.


Thanks again!

---

