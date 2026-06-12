---
title: "hi and hello and i need your help badly!"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by halutzparilla on 2006-11-15
first i wana say hi to everyone...

i'm halutz, from NY, first time user of Ubuntu / linux.

and i greatly appreciate if you can help me find the drivers for my Mobo so i can use this Ubuntu...

drivers missing 
LAN: Intel® PRO Network Connections
INF: Intel® Chipset Software Installation Utility
Intel® Audio Studio
Audio: Sigmatel 92XX

and i can't do mp3, dvd playback, read my partition which i installed my ubuntu...

TY in advance

---

### Post by Mimsy on 2006-11-15
I can help you with the media formats, I think. For anything else, you need to ask someone who actually knows how Ubuntu works. :)

The very easiest way to get the mp3 and dvd playback that I've found, is to install Automatix2, and have it install the codecs for you. Follow the link in my signature, and you'll get to a how-to for installing Automatix2.

Good luck with the rest of Ubuntu!

/Mimsy

---

### Post by KhaaL on 2006-11-15
> **halutzparilla said:**
> first i wana say hi to everyone...

i'm halutz, from NY, first time user of Ubuntu / linux.

and i greatly appreciate if you can help me find the drivers for my Mobo so i can use this Ubuntu...

drivers missing 
LAN: Intel® PRO Network Connections
INF: Intel® Chipset Software Installation Utility
Intel® Audio Studio
Audio: Sigmatel 92XX

and i can't do mp3, dvd playback, read my partition which i installed my ubuntu...

TY in advance

Hello & hi & welcome!

Ubuntu installs the drivers for the mobo automatically, so you don't need to install them seperately (at least, usually). When it comes to mp3 and dvd playback, you need to install additional codecs. there is another solution: there is a media player named vlc that has those codecs installed and has support for dvd playback. open up a terminal and type:

[INDENT]sudo apt-get install vlc[/INDENT]

and it will install.

Regarding your partitions, what type of partitions did you create? ext3? HFS? NTFS? did you formart them?

/KhaaL

---

### Post by Ocxic on 2006-11-15
yes he's right about the drivers, my Intel 865GBF bored works fine sound and all.

---

### Post by taurus on 2006-11-15
What does your /etc/fstab look like?  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/fstab
```

---

### Post by halutzparilla on 2006-11-15
thanks, i'll follow your instruction and take it from there...

i hope to enjoy the Ubuntu Linux environment... 

thank you again

---

