---
title: "Gens Help!"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-09-05
Hey guys!

I downloaded the gnens (sega emulator) source, but If I follow the directions in it's readme to install it, it does not work.

Anyone give me a quick step by step on how to install this app?

Thanks!
CM

---

### Post by aysiu on 2005-09-05
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

[i]sudo apt-get update
sudo apt-get install dgen[/i]

---

### Post by TristanMike on 2005-09-05
Hey, thanx, I didn't know there was a sega emulator included in the repo's. Sweet, Phantasy Star, your mine!

---

### Post by gord on 2005-09-06
id note that Dgen isn't a perfect emulator though, i for one have a huge problem with speed with that, namely it runs far too fast (no frame limiter it seems).

i managed to get gens to compile just fine with the [latest source code](http://prdownloads.sourceforge.net/gens/gens-rc3.tar.gz?download) , you just need to unpack it to a directory, cd into said directory and type 
```

./configure
make
make install

```

the 'make install' command might need to be 'sudo make install', i can't remeber but its prolly best to try it without first.
if you come accross any errors in the form of 'x cannot find command y' then just do a search in synaptic for whatever it is, and install that (usually need the -dev version)

if youv not done any compling before you might need to get a copy of gcc and sdl from synaptic.


one thing to note is that gens runs rather slow on non windows os's. it was originally built to use directX and was ported to SDL to get it to work in other os's, apprently the SDL code is rather 'unoptimised'. i can get most games to work fine on my 1.8ghz Athlon XP though.

---

### Post by the_purulent on 2005-09-06
Dgen seems to work fine for me, with the exception that it has no graphic interface that I can see (which is quite handy).  BUt I've setup a desktop launcher with the -j and -f switches enabled so that I can just drag a rom file to it, and it launches full screen with gamepad / joystick enabled.

```

Example Run: dgen -f -j

```

---

