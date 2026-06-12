---
title: "No Sound in Amarok"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by FlintyVamp on 2007-11-27
Hey,

I'm fairly new to Linux and Ubuntu but so far I'm extremely impressed. I am however having a tiny problem. I've install Amarok to listen to my .MP3's but I don't get any sound out of it no matter what format it is. I've also tried .OGG but no luck..

The MP3's play fine in Totem Movie Player... 

Any ideas?

Scott

EDIT: I am using a Creative Audigy 2 ZS Soundcard

Here is my Amarok Settings [[IMG]http://imagecloset.com/7/abbce084af995e3c7f5cd9349af6a1dd/Screenshot_thumb.gif[/IMG]](http://imagecloset.com/view7/abbce084af995e3c7f5cd9349af6a1dd/Screenshot.png)

---

### Post by danm-koder on 2007-11-27
I'm sort of a n00b myself but I think you could check the engine Amarok is using, just go to the tools menu, then 'Configure Amarok' and then engine, and make sure you are using Xine, if you have anything else in there, your mp3's most likely won't ever play...

I hope this helps you a little...

---

### Post by forestpixie on 2007-11-27
you might need to install

```
sudo apt-get install libxine1-ffmpeg
``` I did

---

### Post by lespaul_rentals on 2007-11-27
Did you run:

```
sudo apt-get install ubuntu-restricted-extras
```

Try that.  Also make sure you have your sound levels turned up on the mixer, and the correct engine is selected in the Settings for Amarok.

---

