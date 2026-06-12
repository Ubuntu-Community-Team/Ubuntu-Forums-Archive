---
title: "64bit Mplayer config need help!! error"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-02-12
Hi I'm trying to configure my Mplayer by doing this:

gedit ~/.mplayer/config

Then cut and paste the following block into the file:

# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Drop frames to preserve audio/video sync.
framedrop = yes

# get a default OSD font from fontconfig
fontconfig = yes
font = "Sans"
subfont-text-scale = 3


BUT i CANNOT SAVE THE EDITED FILE...IT WONT ALLOW ME. ERROR SAYS CANNOT SAVE TO THE DIRECTORY(IE DAN/EDIT ETC). aNY IDEAS?

---

### Post by Freddd on 2006-02-14
I'm having the same problem :(

---

