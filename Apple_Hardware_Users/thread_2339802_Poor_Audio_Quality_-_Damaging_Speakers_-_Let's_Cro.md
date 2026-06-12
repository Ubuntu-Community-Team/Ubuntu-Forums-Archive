---
title: "Poor Audio Quality - Damaging Speakers - Let's Crowdsource Fix This"
date: 2016-10-12
forum: Apple Hardware Users
---

### Post by dylanetaft on 2016-10-12
Ubuntu 16.04 - iMac 2011 27 in -  compared to OSX, the audio quality is not good.  It's tinny, and sounds overdriven. 

Also, the device comes across as a surround40 pcm, that doesn't make any sense.

I spent time researching, and thinking, and sleeping on it.  I bet apple just has 4 speakers inside, and no hardware cutoff filters.  I bet the treble speaker is being overdriven by bass, and the bass speaker overrun by midrange frequencies!
That actually does seem to be the case, and running an iMac with no lowpass or highpass filters is probably going to damage the speakers.

Alsa can do filtering with LADSPA.  First I tried lowpass filters on the bass speakers, highpass on the tweeters.  Sounds better, but still very off.

I am NOT an audiophile.  This is a pretty severe issue.  

I need help adjusting ramps.  Here is what I have so far - see the section with controls?  That's a 10 channel equalizer.  See if you can find better settings.  The first two channels are the tweeter, second two "bass speaker"
I think we can get this working with Pulse too.

If you want to try it - 

Edit: Updated with latest settings
apt-get install build-essential
Grab this and install it [http://quitte.de/dsp/caps.html#Install](http://quitte.de/dsp/caps.html#Install)  - very nice LADPS filters.

/etc/pulse/default.pa
add two lines
load-module module-alsa-sink device=upmix20
load-module module-alsa-source device='plughw:CARD=PCH,DEV=0'

~/.asoundrc 
pcm.default pulse


pcm.upmix20 {
    type route
    slave.pcm "plug:bandpass"
    slave.channels 4
    ttable.0.0 0.7
    ttable.1.1 0.7
    ttable.0.2 0.9
    ttable.1.3 0.9
}



pcm.bandpass {
    type ladspa
    #slave.pcm "plug:mydmix"
    slave.pcm "plughw:CARD=PCH,DEV=0"
    #slave.pcm "dmix:CARD=PCH,DEV=0"
    path "/usr/lib/ladspa"
    channels 4 
    plugins {
        0 {
            id 1773 #per listplugins
            policy none
            input.bindings.0 "in";
            output.bindings.0 "out";
            input {
controls [ -48 -48 -48 -48 -30 -36 -30 -20 -4 5 ]
            }
        }
        1 {
            id 1773
            policy none
            input.bindings.1 "in";
            output.bindings.1 "out";
            input {
controls [ -48 -48 -48 -48 -30 -36 -30 -20 -4 5 ]
            }
        }
        2 { #bass
            id 1773
            policy none
            input.bindings.2 "in";
            output.bindings.2 "out";
            input {
controls [ 3 5 -4 -30 -35 -40 -40 -40 -48 -48 ]

            }
        }
        3 { #bass
            id 1773
            policy none
            input.bindings.3 "in";
            output.bindings.3 "out";
            input {
controls [ 3 5 -4 -30 -35 -40 -40 -40 -48 -48 ]
            }
        }
    }
}

pulseaudio -k, it will reopen with the new settings

alsamixer I set speaker to ~75, bass speaker to ~94

---

### Post by dylanetaft on 2016-10-12
[ -48 -48 -48 -48 -48 -48 -48 -48 -28 -10 ]
[ -48 -48 -48 -48 -48 -48 -48 -48 -28 -10 ]
[ -6 -4 -34 -30 -30 -40 -40 -40 -48 -48 ]
[ -6 -4 -34 -30 -30 -40 -40 -40 -48 -48 ]
Is closer I think to what OSX sounds, still very slightly off...but maybe not enough to think OSX is doing anything different.

---

### Post by dylanetaft on 2016-10-13
I am working with the Pulseaudio mailing list on moving this kind of configuration to Pulse - it looks like Pulse supports ladspa, or using the Alsa PCM as a pulse Sink - whatever the best direction is.
So far, using pavucontrol to turn off the profile for the sound card in the config tab, and then putting load-module module-alsa-sink device=upmix20 in /etc/pulse/default.pa, rebooting, that gets pulse running ontop of Alsa with this configuration.  Trying to work towards the best solution, very close.

---

### Post by dylanetaft on 2016-10-16
Updated OP with what I think is my final .asoundrc.  Keeps dangerous bass frequencies away from the tweeter speaker, adds a bit of mid-range.  Feel free to tweak it, comment, if you find improvements with the ramps to make it sound like OSX.  Please!  Thanks.

Also, it seems it's better to do this at the Alsa layer, Pulse you can't do it without splitting the sink into 4 sinks, applying a LADSPA filter to each, then recombining.  Pulse runs happily ontop of this, however.

---

