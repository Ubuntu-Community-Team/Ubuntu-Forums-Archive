---
title: "Software Equivalent?"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Septicaemia on 2006-01-18
I do alot of sound recording/production, and I'm a recent convert to Ubuntu/Linux. I know Linux isn't really intended for Multimedia development, but it'd be a nice touch for me to be able to properly compose on this wonderful operating system.

I already am familiar with using Audacity for my final mixing/recording of Guitar parts for things, but am yet to find a proper sequencer, ala FL Studio/Cakewalk/*insert other alternatives here*.

So, what would be your personal recommendation for that sort of thing? I've tried Hydrogen, but it's not a Sequencer, it's a Drum Machine. I'd prefer not to use Wine, because it lacks ways to communicate with Linux to access MIDI Devices and USB stuff, so yeah.

Sorry if this is the wrong place :P

---

### Post by 23meg on 2006-01-18
Look into Rosegarden and Ardour. Both are in the repositories. I also heard of LMMS which is similar to FLStudio but haven't tried it myself.

---

### Post by Septicaemia on 2006-01-18
Quick Reply! Thanks for the names, i'll have a look at all three I suppose.

---

### Post by 23meg on 2006-01-18
You're welcome. Here's more from the repos; the command I typed in is in bold: ```
$ **apt-cache search sequencer**
aconnectgui - graphical ALSA sequencer connection manager
blop - Bandlimited wavetable-based oscillator plugins for LADSPA hosts
brahms - Graphical music editor and MIDI sequencer
freebirth - Bass synthesizer/sample player/sequencer similar to Rebirth
galan - modular audio processing and synthesis system
hydrogen - Simple drum machine/step sequencer
jack-rack - LADSPA effects "rack" for JACK
libtse3-0.2.7c2 - TSE3: portable sequencer engine in C++ - development files
libtse3-dev - TSE3: portable sequencer engine in C++ - development files
muse - Qt-based midi/audio sequencer
pmidi - A command line midi player for ALSA
python-oss - Open Sound System (OSS) interface for Python
python2.3-oss - Open Sound System (OSS) interface for Python
python2.4-oss - Open Sound System (OSS) interface for Python
rosegarden - An integrated MIDI sequencer and musical notation editor
rosegarden2 - An integrated MIDI sequencer and musical notation editor
rosegarden4 - music editor and MIDI/audio sequencer
seq24 - Real time MIDI sequencer
shaketracker - MIDI sequencer with tracker GUI
spiralsynthmodular - An Object orientated modular softsynth / sequencer / sampler
terminatorx - A realtime audio synthesizer
timidity - Software sound renderer (MIDI sequencer, MOD player)
timidity-el - An Emacs front end to Timidity++
timidity-interfaces-extra - TiMidity++ extra user interfaces
tk707 - drum sequencer for a sound card or MIDI device
tse3play - MIDI/TSE3MDL player/converter
vkeybd - Virtual Keyboard program
xmp - A module player supporting AWE32, GUS, and software-mixing
xmp-common - Common files for xmp, xxmp and the xmp XMMS plugin

```
And even more amazing audio apps: [http://www.linux-sound.org](http://www.linux-sound.org)

---

