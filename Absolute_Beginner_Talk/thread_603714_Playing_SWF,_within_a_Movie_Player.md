---
title: "Playing SWF, within a Movie Player?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Ondkloss on 2007-11-05
Hi. Here is the site I'm having trubble playing files from:
[http://atvs.vg.no/player/?id=12333](http://atvs.vg.no/player/?id=12333)

It seems Firefox uses the MPEG player plugin, and tries to use it to play the logo_intro.swf file before the actual movie/videoclip is to be played. Unfortunatly for me neither MPlayer or Movie Player handles SWF files the way I've got them set up now (Automatix2).

Any hints? Do you people get it to work? The file that has trubble playing here plays perfectly if I open it in a separate window, which is why I've concluded that Firefox wants to play both the SWF and the MPEG within the same player (which probably works with Windows Media Player, but not my players).

Any fixes?

---

### Post by travis31 on 2007-11-05
Try using the Media Player Connectivity plugin in Firefox. You will be able to configure different players for the different types of streams.

---

### Post by qamelian on 2007-11-05
You could just install the flashplayer browser plugin. Or if you are downloading the files to play locally, I think gnash will let you do that. 

If you are trying to view them locally using Totem Movie Player with the GStreamer back-end (which may not be the case since you mentioned using Automatix), Totem should prompt you that another component is needed and offer to download it for you. 

Honestly, for multimedia stuff, Automatix really doesn't serve any purpose with the current version of Ubuntu.

---

### Post by FuturePilot on 2007-11-05
I'm not sure, but there doesn't seem to be any Flash videos on that site. Everything played back fine through the Mplayer plugin.

---

### Post by Ondkloss on 2007-11-05
TY all. I'll have to plunder some more with this info to see if I get it working.
Actually Automatix2 helped me out alot for some basic codecs and getting them to work in the Totem player.
And no, it doesn't look like there are any SWF files trying to play, but the "VG"-logo showing at the start is a SWF file, and it refuses to play using my MPlayer plugin here.

I'll do some more testing and see what I come up with...

BTW:
This is the file that I can't play [http://atvs.vg.no/video/gfx/logo_intro.swf](http://atvs.vg.no/video/gfx/logo_intro.swf)
Can you guys play this using Open URL/Open Location in Movie Player (Totem)/Mplayer?

---

### Post by FuturePilot on 2007-11-05
Interesting. I never saw that show up:confused:

---

