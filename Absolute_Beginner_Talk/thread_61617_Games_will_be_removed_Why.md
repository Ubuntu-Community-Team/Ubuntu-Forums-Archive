---
title: "Games will be removed?? Why???"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-09-01
As I have problems with some games that refuse to play with sound, I searched some threads and this command seems to work for other users.

> sudo apt-get install libsdl1.2debian-all

Running it gives me almost every game I have as well as some other apps.

Here is the output.

T> he following packages will be REMOVED:
  bos bugsquish bumprace chromium chromium-data enigma enigma-data
  frozen-bubble gcompris gemdropx gravitywars icebreaker junior-gnome
  libgcompris-1-0 libopenal0 libpt-1.8.3 libpt-plugins-alsa libpt-plugins-v4l
  libsdl-console libsdl-gfx1.2 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2
  libsdl-perl libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-nas libsmpeg0
  neverball scorched3d scorched3d-doc sopwith stratagus tuxpaint tuxracer

I have no intention of downloading everything and add them again. Is there a way to prevent the removing?

---

### Post by poofyhairguy on 2005-09-01
[QUOTE=GrootBrak]As I have problems with some games that refuse to play with sound, I searched some threads and this command seems to work for other users.



Running it gives me almost every game I have as well as some other apps.

Here is the output.

T

I have no intention of downloading everything and add them again. Is there a way to prevent the removing?[/QUOTE]

Did you already try the

> killall esd

command to get your games to work?

---

### Post by GrootBrak on 2005-09-02
[QUOTE=poofyhairguy]Did you already try the



command to get your games to work?[/QUOTE]
 Yes, killall esd, won't work. Since I got my sound configured I never got the volume up, so I am still amplifying the output to start with. But at least most sounds work.

---

### Post by Knyven on 2005-09-02
Maybe disabling the "sound server at startup" might help with sound problems with other games.

---

### Post by GrootBrak on 2005-09-09
Done it, won't work.

---

