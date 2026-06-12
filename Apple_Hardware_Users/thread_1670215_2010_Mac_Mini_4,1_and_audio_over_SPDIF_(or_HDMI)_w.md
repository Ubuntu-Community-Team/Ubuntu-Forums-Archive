---
title: "2010 Mac Mini 4,1 and audio over SP/DIF (or HDMI) with 10.10 Maverick"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by aaronjb on 2011-01-18
Alright, I don't post much (because I hate posting, and would much rather search for a while and fix it myself), but this has me at my wits end now..

I've read up on getting audio working on the current-gen Mac Mini 4,1 around various resources:
[https://help.ubuntu.com/community/Macmini4-1/Maverick#Sound](https://help.ubuntu.com/community/Macmini4-1/Maverick#Sound)
[http://forums.gentoo.org/viewtopic-t-858617-start-0.html](http://forums.gentoo.org/viewtopic-t-858617-start-0.html)
[http://ubuntuforums.org/archive/index.php/t-1495460.html](http://ubuntuforums.org/archive/index.php/t-1495460.html)

And .. well, I seem to have tried just about everything.  At one point I did have working audio when gdm started (the 'chime') but not via the Settings->Sound 'Test' page or via any other program (like the default music player) - now I have nothing, zip, nada, nil.

My /etc/modprobe.d/alsa-base.conf ends with the following lines:
```
aaronjb@link:~$ tail -n 3 /etc/modprobe.d/alsa-base.conf 
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=mbp55
```

I've tried most Mac options from the [HD Audio Models table](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) inclding imac24, imac27, mbp55, macbook5 and macmini3 - even though the latter should definitely be the wrong card;

```
aaronjb@link:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Cirrus Logic CS4206
Codec: Nvidia MCP89 HDMI
Codec: Nvidia MCP89 HDMI
Codec: Nvidia MCP89 HDMI

```

My alsamixer looks like this:
[http://i55.tinypic.com/14tq7gg.jpg](http://i55.tinypic.com/14tq7gg.jpg)

My Sound Preferences like this (I've tried every option available here - I've tried HDMI and SP/DIF, to no avail):
[http://i54.tinypic.com/2iaze9w.jpg](http://i54.tinypic.com/2iaze9w.jpg)

I have the following Alsa packages installed, and the standard pulseaudio stuff:
```
aaronjb@link:~$ aptitude search alsa | grep ^i
i   alsa-base                       - ALSA driver configuration files           
i   alsa-utils                      - Utilities for configuring and using ALSA  
i   bluez-alsa                      - Bluetooth audio support                   
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA                 
i A linux-backports-modules-alsa-2. - Ubuntu supplied Linux modules for version 
i   linux-backports-modules-alsa-ma - Backported drivers for alsa-driver snapsho

```

The Mini is hooked up to an A/V amplifier via both HDMI and SP/DIF (when testing, I switch the amp to look at either HDMI or SP/DIF for audio depending on what I have the Sound Preferences set to) - I've tried direct to the TV via HDMI as well with no change.

Oh - audio via SP/DIF and HDMI work fine under OS X (I ended up so twisted around I had to go back and double check that, just in case!)


Help! Any suggestions gratefully received.

---

### Post by xboxgame on 2011-02-23
same problem here
sound only work with anolog stereo out

"**digital stereo (HDMI) output** and **digital stereo IEC958** Output not working

in xbmc error message (Failed to initialize audio device):confused:

---

### Post by Ravennoir on 2011-04-27
Same problem here...exactly the same setup.

There seems to be a solution [here]("http://assaf-tech.blogspot.com/2011/04/perfect-linux-audio-setup-alsa-with.html"), but content has been to technical for me.

---

### Post by macbuntumini on 2011-08-15
I recently got myself a 2010 model mac mini with a nice discount and installed Ubuntu 10.10 on it (with the goal of running XBMC and hook it up to my TV). 
Everything worked fine, except audio via HDMI. 

It took me some time to get it working but in the end it did, so I'm writing this in case anyone else has the same problem. 

Out of the box, analog audio output can be made to work as described here:
[https://help.ubuntu.com/community/Macmini4-1/Maverick](https://help.ubuntu.com/community/Macmini4-1/Maverick)

For digital output there are 3 devices (as running aplay -l will show).
Device id=3 is the SP/DIF output
Device id=7 is the Display Port output
Device id=8 is the HDMI Port output

I only tried the HDMI output, but simply replacing the 8 by the other device number below should do the trick.

You could try if running the following command already gives output:

```
aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Center.wav
```If not then install the latest ALSA development drivers as follows:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

To get audio output via ALSA working I used the following /etc/asound.conf:

```

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
                pcm "hw:0,8"
                period_time 0
                period_size 1024
                buffer_size 4096
                rate 48000
        }
        bindings {
                0 0
                1 1
        }
}

ctl.dmixer {
        type hw
        card 0
}
```I'm not an ALSA expert, so these settings could probably be improved, but they work for me.

With this aplay will work without explicitly having to mention the device:

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```But since GNOME uses pulseaudio most other applications will still produce no audio at all. 
To get around this problem edit /etc/pulse/default.pa and look for the line containing

```
#load-module module-alsa-sink
```and replace that with

```
load-module module-alsa-sink device=hw:0,8
```Restart pulseaudio using
```

pulseaudio --kill
pulseaudio --start

```now you can select HDMI output in the GNOME sound settings and the audio will actually work :).

Hopefully someday this will work out of the box as it does for Mac OS X ;-)

---

### Post by BrianDK on 2011-08-15
> **aaronjb said:**
> Alright, I don't post much (because I hate posting, and would much rather search for a while and fix it myself), but this has me at my wits end now..

I've read up on getting audio working on the current-gen Mac Mini 4,1 around various resources:
[https://help.ubuntu.com/community/Macmini4-1/Maverick#Sound](https://help.ubuntu.com/community/Macmini4-1/Maverick#Sound)
[http://forums.gentoo.org/viewtopic-t-858617-start-0.html](http://forums.gentoo.org/viewtopic-t-858617-start-0.html)
[http://ubuntuforums.org/archive/index.php/t-1495460.html](http://ubuntuforums.org/archive/index.php/t-1495460.html)

And .. well, I seem to have tried just about everything.  At one point I did have working audio when gdm started (the 'chime') pc game seller onlinecdkeyseller.com 'Test' page or via any other program (like the default music player) - now I have nothing, zip, nada, nil.

My /etc/modprobe.d/alsa-base.conf ends with the following lines:
```
aaronjb@link:~$ tail -n 3 /etc/modprobe.d/alsa-base.conf 
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=mbp55
```I've tried most Mac options from the [HD Audio Models table]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") inclding imac24, imac27, pc game store onlinecdkeyseller.com - even though the latter should definitely be the wrong card;

```
aaronjb@link:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Cirrus Logic CS4206
Codec: Nvidia MCP89 HDMI
Codec: Nvidia MCP89 HDMI
Codec: Nvidia MCP89 HDMI

```My alsamixer looks like this:
[http://i55.tinypic.com/14tq7gg.jpg](http://i55.tinypic.com/14tq7gg.jpg)

My Sound Preferences like this (I've tried every option available here - I've tried HDMI and SP/DIF, to no avail):
[http://i54.tinypic.com/2iaze9w.jpg](http://i54.tinypic.com/2iaze9w.jpg)

I have the following Alsa packages installed, and the standard pulseaudio stuff:
```
aaronjb@link:~$ aptitude search alsa | grep ^i
i   alsa-base                       - ALSA driver configuration files           
i   alsa-utils                      - Utilities for configuring and using ALSA  
i   bluez-alsa                      - Bluetooth audio support                   
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA                 
i A linux-backports-modules-alsa-2. - Ubuntu supplied Linux modules for version 
i   linux-backports-modules-alsa-ma - Backported drivers for alsa-driver snapsho

```The Mini is hooked up to an A/V amplifier via both HDMI and SP/DIF (when testing, I switch the amp to look at either HDMI or SP/DIF for audio depending on what I have the Sound Preferences set to) - I've tried direct to the TV via HDMI as well with no change.

Oh - audio via SP/DIF and HDMI work fine under OS X (I ended up so twisted around I had to go back and double check that, just in case!)


Help! Any suggestions gratefully received.

Have the exactly same problem. Found any solution?

---

