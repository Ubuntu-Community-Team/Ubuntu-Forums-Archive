---
title: "mp3 frustration"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by Minyaliel on 2005-10-22
I finally managed to install LimeWire on my computer. I knew I would have to get mp3 support on Ubuntu, so I did what the Wiki told me to. And it worked for a while. But suddenly it refused to co- operate. So now I can't play mp3's anymore. I can't even burn them to a cd so I could listen to them externally. So here I am with lots of new music and no chance of listening to it whatsoever. I'm feeling a little frustrated right now. Any help would be appreciated.

---

### Post by jasmuz on 2005-10-22
Please explain your issue with more detail, because you dont mention wich programs you are using to listen to your Mp3 files and if you can play any other file format.

---

### Post by Minyaliel on 2005-10-22
Alright, I've tried playing the mp3's (only music format on my puter right now) in these players:

- Mplayer
- LimeWire player
- Totem
- XMMS

and I tried burning them with

- Gnomebaker
- Serpentine

I know my hardware's alright, I mean, it did work for an hour or so :P

---

### Post by jasmuz on 2005-10-22
Can yo hear any other sounds?

---

### Post by Minyaliel on 2005-10-22
Yeah, on start up and when people respond to me on GAIM...

---

### Post by jasmuz on 2005-10-22
Did you check if the sound players are using ESD?

---

### Post by Minyaliel on 2005-10-22
What's ESD?

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=Minyaliel]Alright, I've tried playing the mp3's (only music format on my puter right now) in these players:

- Mplayer
- LimeWire player
- Totem
- XMMS

and I tried burning them with

- Gnomebaker
- Serpentine

I know my hardware's alright, I mean, it did work for an hour or so :P[/QUOTE]

You don't need to know what ESD is. I barely do. You do need to install the codecs like this page says:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

And then try to install my favorite player:

> sudo apt-get install muine

that command should do it.

---

### Post by Minyaliel on 2005-10-22
Alright, now it seems to play them (had to use the root account though) but I can't hear anything! That's the strangest thing ever....

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=Minyaliel]Alright, now it seems to play them (had to use the root account though) but I can't hear anything! That's the strangest thing ever....[/QUOTE]


Damn, I guess you might need to know what esd is. Or at least how to stop it.

Try this command then try to play a file, and tell us if it works:

> killall esd

---

### Post by Minyaliel on 2005-10-22
> This is an audio-only file, and there is no audio output available

Whatta?! (That was in the default Totem)

---

