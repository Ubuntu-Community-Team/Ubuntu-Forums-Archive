---
title: "not getting 5.1 sound"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by fayazskarim on 2007-07-17
Hi I have the riviera turtle beach spdif sound card, I installed all packages necessary for the sound but I am only getting Stereo, not 5.1... Do I have to download any special codec or mp3 player because in my xp OS I am getting 5.1 surround sound...

Thank you

---

### Post by Al3xK3aton on 2007-07-17
You need surround sound speakers (and a subwoofer) to get surround sound.

---

### Post by rillip on 2007-07-17
I'm not real sure on anything different you would need ot do, maybe configure alsa.  I'd recommend searching the multimedia forum and if you don't find anything, post this over there.

---

### Post by asmoore82 on 2007-07-17
to get 5.1 from DVD use vlc or xine and dig into their options to enable 5.1 output

to get fake 5.1 from regular stereo mp3's try using kaffeine with 5.1 plugins

---

### Post by KIAaze on 2007-07-18
Maybe this might help you:
[http://www.halfgaar.net/surround-sound-in-linux#speaker-test]("http://www.halfgaar.net/surround-sound-in-linux#speaker-test")

Apparently, you'll need to add an entry to "/etc/asound.conf" and then specify it as plugin in the players you want to use.

Like I said, I don't know a lot about setting up 5.1, but if you find instructions on the web and don't understand them, I might help. ;)
An ALSA forum or mailing list or IRC channel would be the best place to ask about this.

---

