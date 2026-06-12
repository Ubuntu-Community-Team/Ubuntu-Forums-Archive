---
title: "Remote controlled computer on network for music"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Valir on 2008-02-13
Hi, 

I wonder if I could do this: I have an ubuntu laptop, and my girlfriend a xp-laptop, and I also have a old third laptop that I would like to rig up as a music-server and connect to our soundsystem speakers. 

What would be really nice if we could access that computer each from our own computer and play the music. 

I wonder if I need to install the third computer with xp and do this from Itunes :(  because my girlfriend has a xp-computer - but I really would like to find an Ubuntu solution.

Now, has any one already tried this out? Couldn't find anything specifically with this combo on the forums. Would be nice to hear if anyone has good ideas, (this is not mission critical for my ubuntu sessions, but would be nice).

best regards

Valir

---

### Post by KCormier on 2008-02-13
Install ubuntu 7.10 on the laptop

open a command prompt and run

```
sudo apt-get install ubuntu-restricted-extras
```
This will add in support for wma, wmv, swf, and a lot of other stuff :)

then to system -> preferences -> remote desktop and set that all up.

Then, whenever you wanna play music, you just remote desktop in, set up your playlist, and disconnect and off it goes playing your music.  That's how I do it now.  I'm working on finding/building a better set up though! :)  If you really wanna go crazy you can set up a media center pc but that's a whole different ballgame.  google "htpc" for that!  lol

---

### Post by Whiffle on 2008-02-13
mpd! 

I have mpd installed on my little home server, I can control it with any mpd client from any computer on my network.  Its really slick.

---

### Post by nemilar on 2008-02-13
I second the mpd suggestion.  It's specifically designed for situations like you're trying to setup.

---

### Post by Valir on 2008-02-15
:KS 

Thank you very very much - this was precisely what I was looking for :guitar:

---

### Post by Valir on 2008-02-15
mpd solved this setup, and then combined with subsonic I can also access my music elsewhere outside my home. Very good indeed.

---

