---
title: "Internal Microphone not working"
date: 2011-09-30
forum: Any Other OS
---

### Post by josiahkeller on 2011-09-30
Besides the problem in [this]("http://ubuntuforums.org/showthread.php?t=1852607") thread, I have one other.
The integrated microphone on my netbook doesn't work. At least, it doesn't work on most things.

I can listen to it on the speakers/headphone by playing  it in VLC through 'devices: audio capture: ~'
And in Audacity, if I select the devise in the recording mediums it works, but having 'default' selected doesn't work.

The microphone doesn't work in web browsers, or in Skype.

And in the sound preferences menu in Linux, the 'input level' indicator does nothing.


These things *all* work if I have an external microphone, but not with the internal one.



Please help! :popcorn:

---

### Post by theyranos on 2011-09-30
I can't guarantee that it'll actually work, but this is at least something to try:

Open up the input level indicator so you'll be able to see any effects. Then, fire up a terminal and type 'alsamixer'.  Usually alsamixer starts with the view mode set to Playback. Hit <Tab> to get it over to [Capture]. Here, you should see bars for the line in port and the internal mic. Use the arrow keys and <M> to fiddle with the settings while making noises.

With any luck, one of the bars on your mixer will correspond to your internal mic.

---

### Post by josiahkeller on 2011-10-01
Okay, so I tried that, but no real luck.

I thought that there might have been something, because (by looking at the picture attached you can see what I'm talking about) 'capture 1' didn't make any difference on microphone volume when an external mic was connected. And you can see with the dashes underneath the bar, there ought to be something I figured.

But I then tried adjusting the levels while doing a mic playback (internal) through VLC. But it made no difference. Again, it was the 'capture' setting that adjusted input volume. What's somewhat odd though, is that the 'mic boost' setting only has an effect on external microphones...

Thanks for the help, but it didn't help.](*,)

Any other help anyone?

---

### Post by theyranos on 2011-10-01
Can you paste the results of **lsmod | grep snd** and **arecord -L**?

---

### Post by josiahkeller on 2011-10-01
lsmod | grep snd:```
snd_seq_dummy          12686  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm

```

And arecord -L:
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC272X Analog
    Hardware device with all software conversions
```

(thank you for coming to my aid):-o

---

### Post by Perfect Storm on 2011-10-01
Moved to Other OS/Distro Talk.

---

### Post by theyranos on 2011-10-02
Based on your output, I have two more things to try. If neither of these works, hopefully somebody more knowledgeable can chime in.



**First Idea: force alsa to use dmix as your default sound device**
Create a file in your home folder called *.asoundrc* (note the leading .). This file should contain the following:
```

pcm.!default dmix:Intel

```
Then, log off and back on. See if your mic works. This trick probably won't make a difference, because this should be the default anyway, but it's worth a shot.



**Second (crazier) idea: enable_msi in your driver configuration**
Open up the alsa driver configuration file. On ubuntu, this is */etc/modprobe.d/alsa-base.conf*, but I notice that Artificial Intelligence moved and renamed the thread. I've never used Mint. Some linuxen keep this file in */etc/sound.conf*. If you can't find it, you may have to use **grep -Fr 'options snd-' /etc** to look for it.

Add this line to the end of that file (you'll need to sudo privileges to do this).
```

options snd-hda-intel enable_msi=1

```
If there are other lines in the same file that start with **options snd-hda-intel**, comment them out with a leading **#**.

Next, you'll have to reload your sound driver. This is usually impossible as long as something is using it. The lazy way is to reboot. The less lazy way if you don't want to reboot for whatever reason is to kill off your desktop manager and reload the module. Press Ctrl+Alt+F1 to get a framebuffer, log on, and then type:
```

sudo service gdm stop # replace "gdm" with whatever desktop manager your system uses.
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel
sudo service gdm start

```

Since this suggestion is messing with driver settings, be sure to back up the alsa-base.conf file. If this trick doesn't work, revert the change.

> **josiahkeller said:**
> (thank you for coming to my aid):-o

I'm barely competent. Don't thank me unless I fix it :)

---

### Post by josiahkeller on 2011-10-02
No luck. :(

I have a friend who also has an Acer Aspire One (slightly different model, and running Ubuntu), and he is having the same problem as me. So I know I'm not the only one with this problem.

Does anyone else have any help?

---

### Post by josiahkeller on 2011-10-03
Interesting...
After I put that .asoundrc file in my home folder, sound would no longer play within Chrome or Firefox. But I fixed it by deleting it.
Still no microphone though.

---

