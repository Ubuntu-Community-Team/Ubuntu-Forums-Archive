---
title: "No sound in Real Media files"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2007-05-05
I have no sound in real media files. All other formats seem to work. It doesn't matter which player I use no sound in Real Media format. Any help would be appreciated.

---

### Post by starcraft.man on 2007-05-05
Ok, I think I know how to fix this, at least for the real player.

[QUOTE=Ubuntuguide.org wiki]    * To avoid issues of flickering or screen going blank when switching windows, goto
          o RealPlayer 10 -> Tools -> Preferences -> Hardware -> Uncheck XVideo 

    * To avoid issues with sound
          o Make sure you have ALSA OSS driver. 

Open the terminal (Applications > Accessories > Terminal)
```
sudo aptitude install alsa-oss
```

then edit the startup script 

```
sudo gedit /usr/lib/realplay-10.0.8/realplay
```

 and change line 73 from

$REALPLAYBIN “$@”

to

aoss $REALPLAYBIN “$@”[/QUOTE]

I assume you probably didn't install the also-oss module :)

---

### Post by ~chinook~ on 2007-05-05
No dice.

---

