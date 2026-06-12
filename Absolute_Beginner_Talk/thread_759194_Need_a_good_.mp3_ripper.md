---
title: "Need a good .mp3 ripper"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by WBL on 2008-04-18
I want a good .mp3 ripper that both rips as .mp3's AND recognizes the songs off of my music CDs.  Sound Juicer recognizes the songs off my CDs, but does not have .mp3 as an option.  I couldn't figure out how to make grip do .mp3's either.  I'd like a GUI, not command  line program.  Any help would be greatly appreciated!  :)

-WBL

---

### Post by freduardo on 2008-04-18
Sound Juicer seems to be able to encode .mp3's just fine on my system.

Are you sure you have the correct codecs installed?

To check, see this page:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Then you should be able to select .mp3 in the preferences of Sound Juicer (under 'Format' select "CD Quality (mp3)").

---

### Post by northern lights on 2008-04-18
I guess you don't have the right codecs installed. Run ```
sudo apt-get install ubuntu-restricted-extras
``` from a terminal.

---

### Post by WBL on 2008-04-18
> **freduardo said:**
> Sound Juicer seems to be able to encode .mp3's just fine on my system.

Are you sure you have the correct codecs installed?

To check, see this page:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Then you should be able to select .mp3 in the preferences of Sound Juicer (under 'Format' select "CD Quality (mp3)").

Thanks, I'll see if that helps.

-WBL

---

### Post by starcannon on 2008-04-18
Best and easiest to use mp3 ripper is RipperX available in the synaptic package manager.
It's the easiest I've used in windows or linux, and its got all the features a quality ripper should have.

Try it, you'll like it.

P.S. be sure to install Lame from the synaptic package manager as well.

---

### Post by Triggerhapp on 2008-04-18
```
sudo apt-get install lame grip
```
set it up to use lame as the encoder (it happens to make mp3's)
grip is fairly easy to understand :)

---

