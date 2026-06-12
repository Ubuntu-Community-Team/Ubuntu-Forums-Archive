---
title: "Xmms gives me errors"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by gummylindz on 2006-04-30
It won't play stuff and it says:

Couldn't open audio.
Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard

Totem won't play mp3's either.... and I keep installing new programs, i've tried Juk, Amarok, RealPlayer.... they all have one thing wrong with them and I want one that'll do it all!!!

I like Xmms so can anybody help me with that??

---

### Post by Rinzwind on 2006-04-30
Did you install the w32codecs?

From here:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

there's a list of codecs you might want to install that should let you play MP3s.

Oh and it's not inside Ubuntu install cuz those who own the MP3 format want $$$ for it.

---

### Post by gummylindz on 2006-04-30
thanks i'll try that :)

---

### Post by gingermark on 2006-04-30
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) will tell you how to install pretty much everything you need to play non-free media.

As far as the xmms problem goes, if that doesn't fix it, check the output plugin being used. I'm a Kubuntu user, but I seem to remember GNOME uses ESD (is that right?)

If that output plugin isn't available you can use Synaptic to install it - it'll be called xmms-esd or something similar.

---

### Post by Mustard on 2006-04-30
[QUOTE=gingermark][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) will tell you how to install pretty much everything you need to play non-free media.

As far as the xmms problem goes, if that doesn't fix it, check the output plugin being used. I'm a Kubuntu user, but I seem to remember GNOME uses ESD (is that right?)

If that output plugin isn't available you can use Synaptic to install it - it'll be called xmms-esd or something similar.[/QUOTE]

Just to add to your information above, I'm pretty sure that on gnome it likes to use the ALSA output plugin (with xmms).

---

### Post by gingermark on 2006-04-30
[QUOTE=Mustard]Just to add to your information above, I'm pretty sure that on gnome it likes to use the ALSA output plugin (with xmms).[/QUOTE]
Thanks for that. I only ever used Warty before I switched to Kubuntu - I remember it being esd back then.

---

