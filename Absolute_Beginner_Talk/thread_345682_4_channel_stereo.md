---
title: "4 channel stereo"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by conradcliff on 2007-01-24
Hello all, I have a Turtle Beach Santcruz 6 channel sound card. My question is, how do I get 4 channel stereo. The sound seems to be beautiful so far while listening to music, I haven't tried to listen to anything with a true surround sound output yet, like a DVD. I'm just wanting my surround speakers to clone my front speakers while I listen to music. Thanks for any help!

Also, is there a good equalizer out there. The windows driver for the card had some great features that I will be missing, one of which was an equalizer.

---

### Post by conradcliff on 2007-02-03
I hope I haven't offended anyone...

---

### Post by pseudonym on 2007-02-03
Unless you are able to control speaker output from your receiver/surround system, you'll need to overwrite the default ALSA configuration via an [~/.asoundrc]("http://alsa.opensrc.org/.asoundrc") file for that card, according to the [ALSA wiki]("http://alsa.opensrc.org/Cs46xx") . The same wiki includes some [examples]("http://alsa.opensrc.org/Playing_stereo_on_surround_sound_setup_%28Howto%29") which should help you. A fairly simple example which should also work for you is [here]("http://ubuntuforums.org/showthread.php?t=31829").

Many people might say you don't need an ~/.asoundrc file with recent versions of ALSA, but depending on your soundcard, you do often need to create one to get the best out of it.

As far as mixers go, the standard ALSA mixers (eg. alsamixergui, GNOME ALSA Mixer) only control volumes on particular sound card inputs/outputs. They don't function like graphic equalizers. Such a feature does exist in Linux, but only on a per application basis eg. XMMS audio player has an equalizer, and some others do.

Have a read of the ALSA wiki info and if you have problems setting up your ~/.asoundrc file, just post back.

---

### Post by conradcliff on 2007-02-03
Thank you very much, I'll look into it.

---

