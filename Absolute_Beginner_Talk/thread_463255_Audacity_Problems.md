---
title: "Audacity Problems"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-06-03
Hi, I installed Audacity with a view to recording an old cassette onto my PC. Connected the cassette deck via the line in and got that working. Thought I had the recording working well too until I tried adjusting the input volume at which point the mouse pointer disappeared and the PC froze. Had to revert to resetting and rebooting. After that at first it did not record. Then it decided to come up with an error when I clicked on the record button :

"Error opening sound device. Please check the input device settings and the project sample rate"

Tried uninstalling and reinstalling audacity, but with the same result.

I'm not a great expert at this, though I when I have done similar exercises on XP with audacity I have not had any trouble at all.

Any help gratefully received.

---

### Post by rickycodie on 2007-06-03
i have had these myself, go to edit, profiles, and ensure that the oss driver is selected.

---

### Post by OldGrey on 2007-06-03
Thanks. A partial success, The error message has gone, but even with the input volume on max it isn't recording anything

---

### Post by OldGrey on 2007-06-03
Fixed it. Needed to change the device in the Volume Control to one with (OSS Mixer) in it.

---

### Post by ramjet_1953 on 2007-06-03
Usually, problems with Audacity come about because it uses OSS and not ALSA.

However, there is an easy fix.

Firstly, make sure that [COLOR="Red"]alsa-oss[/COLOR] is installed, using Synaptic.

Secondly, Audacity needs to be started with this command:

[COLOR="Red"]aoss audacity[/COLOR]

You can modify the start command in[COLOR="Blue"] System>Preferences>Main Menu[/COLOR] .

Right click on [COLOR="Blue"]Audacity[/COLOR] and choose [COLOR="Blue"]properties[/COLOR]

In the command section type in [COLOR="Red"]aoss audacity[/COLOR].

Regards,
Roger :cool:

---

### Post by ubromtoo on 2007-06-04
RAMJET_1953 :

     Thanks for the "aoss audacity" command info. that should take care of a long-

standing irritation, since I always had to close all other sound-using apps before I 

could use Audacity.  

      Changing the command in Dapper requires :

  Applications > Accessories > Alacarte menu editor > Sound & Video

                                                  Thanks again  :)

---

### Post by Patrick K on 2007-06-04
> Changing the command in Dapper requires :

Applications > Accessories > Alacarte menu editor > Sound & Video Or right clicking on the menu.

---

### Post by OldGrey on 2007-06-04
My euphoria was short lived. It recorded alright, but the quality was awful. I'll try the suggested fix when I get home.

---

### Post by p_quarles on 2007-06-04
Had the same problem, and this thread solved it. The AOSS setting was default for me, actually, but apparently Audacity also requires you to change the controlled device to "Digital 1" (the default, in my installation, was "volume."

---

### Post by discmaster on 2007-06-04
I implemented all the changes that ramjet listed, & my audacity still will not work. I have changed the device settings, etc., & at one point I was able to get horribly distorted recording, but that's it. 

I am trying to record audio from the sound card, i.e. play a file with totem or streaming audio & then record it with audacity.

---

### Post by ubromtoo on 2007-06-06
Looks like I spoke too soon....using the aoss command makes things worse, not better,

for some reason. Maybe it's a Dapper thing. Oh well, back to the drawing board lol....

---

### Post by OldGrey on 2007-06-08
Hi again

been busy so not been able to try this out sooner

> Usually, problems with Audacity come about because it uses OSS and not ALSA.

Seems to fix the sound quality problems, however there were some weird side effects:

1. I cannot adjust the input or output levels from within Audacity - I have to use the mixer controls.
2. The volume control applet only controls the the PC volume.

I fixed the latter by replacing the applet

:confused:

---

### Post by FSHero on 2007-12-08
> **ramjet_1953 said:**
> Usually, problems with Audacity come about because it uses OSS and not ALSA.
However, there is an easy fix.
Firstly, make sure that [COLOR="Red"]alsa-oss[/COLOR] is installed, using Synaptic.
Secondly, Audacity needs to be started with this command:
[COLOR="Red"]aoss audacity[/COLOR]
You can modify the start command in[COLOR="Blue"] System>Preferences>Main Menu[/COLOR] .
Right click on [COLOR="Blue"]Audacity[/COLOR] and choose [COLOR="Blue"]properties[/COLOR]
In the command section type in [COLOR="Red"]aoss audacity[/COLOR].
Regards,
Roger :cool:

Thanks very much for this fix! I was simply having problems playing a song so I could transpose it.

Note: I am referring to Kubuntu Feisty Fawn i386 in the following. 
I was having a peculiar problem whereby I got the error mentioned in the first post. I changed the Playback device to OSS. This worked... except that there was no way to control the volume level through software. (I had to actually turn the knob on the speaker... which is damaged slightly. :P)  The volume slider in Audacity didn't work, and neither did changing the PCM channel level in KMix.

I followed your instructions, and keeping playback device as "OSS" works. I cannot change the volume through Audacity, but I can through KMix. Good enough for me!

---

### Post by FSHero on 2007-12-08
Okay, it is actually being problematic.

Now, after about a minute of playing, Audacity hangs. (The window is still open, but is unresponsive, and sound ceases to play.)

Below is the output from the terminal:

```

fshero@medion-p4:~$ aoss audacity
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->playback, outParams, self->primeBuffers, hwParamsPlayback, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1662
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783
Expression 'bytesWritten = write( component->fd, component->buffer, len )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1089
Expression 'PaOssStreamComponent_Write( stream->playback, &frames )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1646

```

Can anyone help me to fix this please?

---

