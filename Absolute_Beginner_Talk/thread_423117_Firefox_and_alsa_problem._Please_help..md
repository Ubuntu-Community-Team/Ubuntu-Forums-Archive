---
title: "Firefox and alsa problem. Please help."
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by garbage792 on 2007-04-25
Hi there,

Please help me. I am having a lot of trouble :(

I am using an external sound card so I have disabled by onboard sound card by putting it in the blacklist. I am using ALSA. The sound is coming perfectly except for two problems.

1.) When I am using firefox and watching some flash, if I try to listen to an mp3 or watch a video in vlc or mplayer at that time I get the error  "The audio output is in use by another application.....Try using a sound server",  I am unable to run sound in firefox and any other player with sound at the same time :( Please help.

2.) Every few minutes the flash sound goes dead in firefox. For example while watching youtube in the middle the sound would just go away. I have to then close fireox and restart it to get the sound again.

Please please help. I promise to give you popcorn if you do :popcorn: 

My  /etc/firefox/firefoxrc is below.

# which /dev/dsp wrapper to use
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).


Tell me if you need more information.

---

### Post by garbage792 on 2007-04-25
> **garbage792 said:**
> Hi there,

Please help me. I am having a lot of trouble :(

I am using an external sound card so I have disabled by onboard sound card by putting it in the blacklist. I am using ALSA. The sound is coming perfectly except for two problems.

1.) When I am using firefox and watching some flash, if I try to listen to an mp3 or watch a video in vlc or mplayer at that time I get the error  "The audio output is in use by another application.....Try using a sound server",  I am unable to run sound in firefox and any other player with sound at the same time :( Please help.

2.) Every few minutes the flash sound goes dead in firefox. For example while watching youtube in the middle the sound would just go away. I have to then close fireox and restart it to get the sound again.

Please please help. I promise to give you popcorn if you do :popcorn: 

My  /etc/firefox/firefoxrc is below.

# which /dev/dsp wrapper to use
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).


Tell me if you need more information.

I just discovered that if I use any two applications trying to output sound, the first application locks the sound and the other application cannot output sound. I am using alsa and have it configured in System-->Preferences-->Sound .Also in he vlc and mplayer options I am using alsa but still cannot get multiple sounds. :confused: 

help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by garbage792 on 2007-04-26
> **garbage792 said:**
> I just discovered that if I use any two applications trying to output sound, the first application locks the sound and the other application cannot output sound. I am using alsa and have it configured in System-->Preferences-->Sound .Also in he vlc and mplayer options I am using alsa but still cannot get multiple sounds. :confused: 

help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I searched more and found that I might have to use a plugin called dmix. But then I discovered in the faq that 
"NOTE: For ALSA 1.0.9rc2 and higher you don't need to setup dmix. Dmix is enabled as default for soundcards which don't support hw mixing."

I have 1.0.13 which is higher than 1.0.9rc2 right? So then it should work by default. But it doesn't, please help.

*crickets chirping*

Anybody?
Somebody?

---

### Post by troelsjc on 2007-06-05
I have [the same problem.]("http://ubuntuforums.org/showthread.php?t=455980")
Some help would be greatly appreciated :KS

---

