---
title: "Install program from command line"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by von Stalhein on 2007-11-14
Hello all,
I've been searching for ages, and I've gotten close, but I'm stumped.

I d/l Alien Arena, and when I tried to unzip it into usr/games I needed to do it as root.

So, OK, I can cd to the directory where I keep stuff, and I think I can tell it that I want it to unzip and use folder names etc,  but I don't know how to to tell it where to go from that stage: -

```
sudo unzip alienarena2007-20071011-linux.zip -d 

```

I want to put it in usr/games which is in / but I'm not sure how that is designated via command line. I think there's a tilde involved, but I'm not sure.

Thanks for any assistance.

---

### Post by Sef on 2007-11-14
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by ByteJuggler on 2007-11-14
Don't install it manually.  Alien Arena is already in the Gutsy multiverse repositories.  Simply enter in a terminal window:

```
sudo apt-get install alien-arena
```

Or go into Synaptic package manager (Under System->Administration->Synaptic Package manager), then search for "alien-arena" and install it from there.

---

### Post by von Stalhein on 2007-11-14
> **ByteJuggler said:**
> Don't install it manually.  Alien Arena is already in the Gutsy multiverse repositories.  Simply enter in a terminal window:

```
sudo apt-get install alien-arena
```

Or go into Synaptic package manager (Under System->Administration->Synaptic Package manager), then search for "alien-arena" and install it from there.

Yep, that's OK, but it's an older  version AFAIK .

This way I can get the up to date one, and learn something on command line use.

Thanks for you help guys, I'll do some more reading.

---

### Post by taurus on 2007-11-14
If you want to copy the new directory with the game in side to /usr/games, then just put the sudo in front of the cp command.

```
sudo cp -R directory_of_that_game /usr/games
```

---

### Post by von Stalhein on 2007-11-14
Thanks taurus, I'll give it a crack when I get home from work later today.

Cheers!!

---

