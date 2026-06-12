---
title: "Problems with PulseAudio and TiMidity"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-04-03
Hi,

I have PulseAudio installed and am trying to get TiMidity working with it (I need TiMidity for TuxGuitar).

Help please :-)

---

### Post by Ozor Mox on 2008-05-11
Bump!

Timidity used to work fine under Gutsy with ALSA, but now with PulseAudio it won't install. Apt says:

> 
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                               ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
                                                                                                                                                                     [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)


Since PulseAudio is meant to be more advanced than ALSA, I hope reverting to ALSA isn't the solution...

---

### Post by dwally89 on 2008-05-12
I managed to get TuxGuitar to work in the end.

---

### Post by Ozor Mox on 2008-05-12
If it involved installing TiMidity, do you mind saying how?

---

### Post by dwally89 on 2008-05-12
I ended up using a java synth instead of timidity

---

### Post by yappmeister on 2008-05-28
Could you give a little more detail on which java synth u used etc?

Or if anyone else has managed to fix this problem with timidity. I get exactly the same error and so far no luck in sorting it.

---

### Post by dwally89 on 2008-05-28
Sorry I can't remember exactly how I did it.

After all the problems with Pulseaudio (and the seemingly lack of advantages for the everyday user) I have reverted back to ALSA, and TuxGuitar, Timidity, and every other program works.

Sorry I can't be of more help.

---

### Post by jukingeo on 2008-06-17
> **Ozor Mox said:**
> Bump!

Timidity used to work fine under Gutsy with ALSA, but now with PulseAudio it won't install. Apt says:



Since PulseAudio is meant to be more advanced than ALSA, I hope reverting to ALSA isn't the solution...


Hello, I am getting this same error message.  I had Pulse Audio installed with OSS and it was working fine, but Pulse Audio knocked out my streaming audio capability on the internet.  There was a fix guide that I followed, but what I (or the author of the document) didn't know was that the fix doesn't work with OSS.  Needless to say, I blasted my sound out completely.  So I began to prepare to redo everything and I uninstalled OSS and Pulse.  The trouble is that now that I want to reinstall OSS, I get that same error message you have.

This is the later part of my OSS installation on my Terminal:

nvoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
ubuntustudio-audio depends on timidity; however:
Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
timidity
ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

You see?  same thing.   So I don't know if OSS or Pulse installs timidity.  After the problem happened, I did upgrade to Ubuntu Studio in the hopes that I would get some leeway into correcting this problem (and I wanted Ubuntu Studio anyway).  But that didn't happen.  But I do know that I didn't get any timidity problems prior to installing Ubuntu Studio.

SEMI SOLVED:  Since Timidity was interfering with my reinstallation of OSS and I didn't find anything conclusive here, I just opted to go into Synaptic, find Timidity and fully removed it from my system.  With it gone I was able to reinstall my OSS and I do have partial sound now.  However, I hope that deleting Timidity doesn't come back to haunt me in the near future.

---

