---
title: "Struggling with Media Players"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-09-22
My migration from Windows to Linux is /almost/ complete.

The only thing I havent managed to get to grips with in Linux is multimedia. For a start I own a Sony Walkman NW-A1200 mp3 player, which will not work unless you use Sony's crappy Windows software with it *sigh*. I've clearly got much to learn about Wine, but I doubt that I'll ever be able to get some of my games or mp3 player working under it :S

Main problem is the fact that I just can't find an audio player which does, basically, what Winamp does. I've tried BMPx, AmaroK, Rhythmbox, XMMS and JuK.

All I want it to do is be compatable with my Xf86audio buttons, have an OSD  on track change and a central library. Oh, and it has to work with .wma files. I know AmaroK does all of this, but AmaroK cuts off the first 3 seconds of every song :confused: 

Any suggestions?

---

### Post by Brunellus on 2006-09-22
have you consulted the RestrictedFormats wikipage?

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by happy-and-lost on 2006-09-22
Yeah, I've got the w32codecs. WMA will play on most media players (Just not JuK).

Any idea how to get the Banshee repos working? Keep getting GPG key errors

---

### Post by Brunellus on 2006-09-22
I thought banshee was in the universe repo.

---

### Post by Dinerty on 2006-09-22
> **happy-and-lost said:**
> Yeah, I've got the w32codecs. WMA will play on most media players (Just not JuK).

Any idea how to get the Banshee repos working? Keep getting GPG key errors

Fire up the terminal batman and

```
gpg --keyserver subkeys.pgp.net --recv KEY 
```

then

```
gpg --export --armor KEY | sudo apt-key add -
```

The bunch of large characters it gives you get placed where it says KEY

---

### Post by happy-and-lost on 2006-09-22
That did the trick, thanks.

Banshee seems fab. Audio is a bit choppy sometimes, though.

---

### Post by jcrnan on 2006-09-22
Ive never had problems with either banshee or Amarok as far as audi quality goes. Do you use a special sound card or something?

---

### Post by happy-and-lost on 2006-09-23
It's an integrated Intel soundcard. Nothing fancy. The problem seems to have sorted itsself out, though.

---

