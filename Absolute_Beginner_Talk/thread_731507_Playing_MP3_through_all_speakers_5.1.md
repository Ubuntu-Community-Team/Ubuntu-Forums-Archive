---
title: "Playing MP3 through all speakers 5.1"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by DnOberon on 2008-03-21
My sound is working fine, VLC plays 5.1 dvd's just perfect. Amarok however, doesn't. In windows I used winamp which piped the mp3's through all my speakers no matter if they were 5.1 or not, is there anyway I can have amarok play an mp3 through all of my speakers?

---

### Post by herbster on 2008-03-22
Definitely, I've had this going for some time. Most likely it'll be your ~/.asoundrc that needs to be set.

Which sound card do you have and can you paste your ~/.asoundrc, if it exists:

```
cat ~/.asoundrc
```

Also, in amarok, hit Settings > Configure Amarok > Engine, what is it using for the engine? Xine/default/alsa/etc?

---

### Post by DnOberon on 2008-03-22
it doesn't have an "cat ~/.asoundrc" command doesn't exist? I'm extremely new to linux sorry. I'm running a SB Audigy 4!

---

### Post by rocketangel on 2008-03-22
Open Terminal by going to Applications > Accessories > Terminal. Type ```
cat ~/.asoundrc
``` and copy-paste into your post. 

Start Amarok and go to Settings > Configure Amarok > Engine. What engine is it?

---

### Post by DnOberon on 2008-03-22
The command yields no such directory, and the engine is Alsa

---

### Post by DnOberon on 2008-03-22
Anyone? This is one of the few things preventing my from switching =\

---

### Post by herbster on 2008-03-22
Be patient, DnOberon, we are all helping one another in our spare time :)

Open a terminal, do the following:

```
gedit .asoundrc
```

This will open gedit, the notepad-like text editor, with a blank file. Paste the following into it:

```
pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
   }
}
pcm.duplicate {
    type plug
    slave.pcm "dmixs51"
    slave.channels 6
    route_policy duplicate
}
```

Save the file.

Now quit Amarok (CTRL+Q in the amarok window) and restart it, go back to Settings > Configure Amarok > Engine and in the Output plugin make sure alsa is checked as it already is from your post, and then in the "6 Channels" field make sure it has this:

```
plug:dmixs51
```

And just below that ensure that Speaker arrangement is Surround 5.1. Hit ok and try playing a song now, listening to each channel to see if playback is there.

---

### Post by DnOberon on 2008-03-22
I'm sorry I'm just getting anxious with all this ubuntu stuff. Unfortunately that did not solve my problem =\ Now it says Xine unable to iniatilize any sound drivers

---

### Post by herbster on 2008-03-22
No sweat, close Amarok and any other application you have running which uses sound (Firefox with flash, etc.) and open a terminal:

```
speaker-test -c6 -Dplug:dmixs51 -twav
```

Paste the output using [code] tags please, and hit CTRL+C to end the command whenever you wish (After some output of course).

---

### Post by DnOberon on 2008-03-22
Here you go

```
speaker-test 1.0.14

Playback device is plug:dmixs51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

```

---

### Post by herbster on 2008-03-22
Alright, try the same command but with "duplicate" instead:

```
speaker-test -c6 -twav -Dplug:duplicate
```

Again, paste output.

---

### Post by DnOberon on 2008-03-22
Again here ya go

```
Playback device is plug:duplicate
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory

```

---

### Post by herbster on 2008-03-22
Paste the output of:

```
lsof | grep snd
```

And make sure amarok isn't running.

---

### Post by DnOberon on 2008-03-22
This is it

```
mixer_app 5905   dnoberon   19u      CHR             116,13             14947 /dev/snd/controlC0

```

---

### Post by DnOberon on 2008-03-22
Ok I fixed it, put it on auto detec and that worked =P Thanks for all your help and sorry I'm not patient

---

### Post by LavianoTS386 on 2008-03-24
> **herbster said:**
> Alright, try the same command but with "duplicate" instead:

```
speaker-test -c6 -twav -Dplug:duplicate
```

Again, paste output.

I've got the same problem that **DnOberon ** had. I have a 5.1 Creative Audigy and when I tried your advice to him I got this as my out put.

> ~$ speaker-test -c6 -twav -Dplug:duplicate

speaker-test 1.0.15

Playback device is plug:duplicate
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
ALSA lib pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
Broken configuration for playback: no configurations available: Invalid argument
Setting of hwparams failed: Invalid argument
anthony@anthony-desktop:~$ 


?

---

### Post by herbster on 2008-03-24
Did you edit your ~/.asoundrc as well as I posted?

---

### Post by LavianoTS386 on 2008-03-27
I believe so. I'm not sure what he meant by "auto detc"

---

### Post by DkkD on 2008-04-11
I have had the same problem. After installing 8.04 beta stereo to surround upmixing stoped working. In the end this solved it.

My .asoundrc file:

```

pcm.!default {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}
```

It is named "!default" so you don't have to setup Amarok or any other player to use it and it will automatically convert stereo to 5.1 in every other application as well.

---

### Post by herbster on 2008-04-11
Laviano, you need to be sure about your ~/.asoundrc file, that's the key here. Using the command I gave to DnOberon wouldn't work unless you are using the same sound driver and .asoundrc. You can paste what DkkD has put above into your ~/.asoundrc file and test it using:

```
speaker-test -c6 -twav -Ddefault
```

---

