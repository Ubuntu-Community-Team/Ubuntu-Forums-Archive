---
title: "Audacity 1.3.12-7 Beta issues"
date: 2011-06-08
forum: Any Other OS
---

### Post by Inoki on 2011-06-08
Hi lads and gurls,

I had to come ask for advice here since the Audacity forums are slow as hell and maybe some techies amongst you may be able to help me out.

First of all, I have to say I'm disappointed with the approach to certain releases, when something that hasn't been properly tested for the public is pushed out without a proper documentary on how to troubleshoot an issue. I am talking about the Beta versions of Audacity, which shouldn't have seen daylight before going through a number of tests.

I experienced the following:

Using Linux Mint 10 x64 bit and with the 1.3.12-7 Beta version of Audacity I can't do literally anything. When I try to import a file using File > Open nothing happens, Audacity just hangs and that's it, doesn't even react to closing, the only option is to use Terminal > xkill to get rid of the pesky window. I don't get any error message.

Now I don't know much about compiling stuff, I tried according to manuals but I always got some error. Could someone post a link to the latest working stable release (1.2.6) .deb file for easy installation on Maverick-based systems?

---

### Post by Perfect Storm on 2011-06-08
Moved to Other OS/Distro Talk.

---

### Post by Inoki on 2011-06-08
I don't think that was necessary since Linux Mint is like most say just "rebranded Ubuntu", but ok, thanks.

Any ideas regarding the issue?

---

### Post by Perfect Storm on 2011-06-08
Have you checked this PPA?
[https://launchpad.net/~audacity-team/+archive/daily](https://launchpad.net/~audacity-team/+archive/daily)


Otherwise post your compiling errors.


> I don't think that was necessary since Linux Mint is like most say just "rebranded Ubuntu", but ok, thanks.

It's because UF is meant for support of Canonical 'products' or approved by Canonical. But we have re-open Other OS/Distro talk for other distros etc. (like other distro forums have).
Though we highly recommend to use a distros own support and help line (you can see it in the sticky in this forum.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by Inoki on 2011-06-08
Thank you very much, I tried the option you suggested, got an update of 1.3.14 Alpha but still the same.

Could maybe someone suggest what to do when I try to open an .mp3 for editing in Audacity but the file isn't loaded at all? Maybe clean up some cache?

---

### Post by Toz on 2011-06-08
On my Xubuntu box, audacity will log to ~/.xsession-errors. Not sure about mint. Try opening a terminal window and typing in: ```
tail -f ~/.xsession-errors
``` then run audacity and open a file. See if some error messages are being logged to the terminal window. Could provide a clue.

---

### Post by Inoki on 2011-06-08
Got my Terminal output:

```
innerdistance@innerdistance-Satellite-L650 ~ $ audacity
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3857
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1035
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1192
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1433
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2105
```

---

### Post by Inoki on 2011-06-08
As suggested in other forums I de-installed the current version and installed 1.3.5, the problem is now, I can add the .mp3, it does play, but without sound >.>

---

### Post by Toz on 2011-06-08
> **Anathaen said:**
> Got my Terminal output:

```
innerdistance@innerdistance-Satellite-L650 ~ $ audacity
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
bt_audio_service_open: connect() failed: Spojenie odmietnuté (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3857
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1035
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1192
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1433
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2105
```

Try running from the command line as such:```
padsp audacity
```

From **man padsp**:>  padsp starts the specified program and redirects its access to OSS com&#8208;
       patible audio devices (/dev/dsp and auxiliary devices) to a  PulseAudio
       sound server.

In case its a issue with pulseaudio.

---

### Post by Toz on 2011-06-08
> **Anathaen said:**
> As suggested in other forums I de-installed the current version and installed 1.3.5, the problem is now, I can add the .mp3, it does play, but without sound >.>

Make sure you have correct sound source in Edit->Preferences->Devices.

---

### Post by Inoki on 2011-06-08
Still the same, no sound.

---

### Post by Inoki on 2011-06-08
> **Toz said:**
> Make sure you have correct sound source in Edit->Preferences->Devices.Tried those also, no success.

---

### Post by Toz on 2011-06-08
> **Anathaen said:**
> Still the same, no sound.

Is pulseaudio running? I assume you have other system sounds.

---

### Post by Inoki on 2011-06-08
I'm normally listening to music so yer, all is well, except for Audacity >.>

Off topic: I only ask myself why why why do people need to do such things like releasing Betas publicly. What was so wrong with the previous version. Why all that haste with updates. >.> I say "keep it until it's working or until we get something properly tested and then release it, so there are no issues with it." >.>

---

