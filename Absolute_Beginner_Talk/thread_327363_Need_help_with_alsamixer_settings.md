---
title: "Need help with alsamixer settings"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-12-29
Can someone compare what their alsamixer levels look like compared with mine? Thanks in advance.

Master: On
Master Mono: 100%
PCM: 100%
Surround: 100%
Surround Jack Mode [Shared]
Center: 100%
LFE: 100%
Line: 100%
CD: 100%
Mic: 71%
Mic Boost (+20dB) [Off]
Mic Select [Mic1]
Video: 100%
Phone [Off] 100%
IEC958: On
IEC958 Capture Monitor [Off]
IEC958 Capture Valid [Off]
IEC958 Playback AC97-SPSA: 0%
IEC958 Playback Source [Analog]
PC Speaker: 100%
Aux [Off] 100%
Mono Output Select [Mix]
Channel Mode [2ch]
External Amplifier [Off]

Thanks in advance.

---

### Post by kolinab on 2006-12-29
If you tell me what command you used to see that output I'll post mine.

---

### Post by pseudonym on 2006-12-29
> **kolinab said:**
> If you tell me what command you used to see that output I'll post mine.
That would be 'alsamixer'. You can then store the changes with 'sudo alsactl store' . Once you're satisfied with the settings, you can use your GUI mixer app like Gnome Mixer :)

@ ricardisimo - Also, it would be good to know what soundcard you have. 

Just on what you have posted, if you'e unhappy with your sound quality it would be a good idea to drop 'PCM' back to about 80%. The other mixers look OK as far as volume goes.

---

### Post by kolinab on 2006-12-29
Yeah, I've used alsamixer before, but I can't remember seeing a screen with the levels summarised like that.

---

### Post by dwblas on 2006-12-29
I would turn the PC speaker off if you don't use it.  Also, there have been posts about PCM causing problems with some apps.  If you are having problems, try turning PCM off also.

---

### Post by ricardisimo on 2006-12-29
Hey everyone. Thanks for the replies, and sorry I wasn't more clear about everything. Here's my soundcard info:
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device a00b
        Flags: bus master, medium devsel, latency 64, IRQ 169
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: [48] Power Management version 2
```
     And the background story here is this... I had a dandy of a time trying to get Audacious up and running on my comp, and had to install and uninstall it two or three times, and then tinker with all of the Output plugin settings, etc. At some point my system sounds, like my customized login.wav at startup, stopped playing. Later I lost all sound while trying to fix this.
     I'm now back to square two on this issue. I can play audio with audacious or another player, but the system has no access to the audio, like that little nautilus function that gives you a taste of any mp3 over which your pointer might linger. Also, I get error messages while on webpages with embedded audio or videl that Totem is trying to play, saying that the device is being used by some other app.
     So, in some ways I'm thinking my alsamixer settings might need tinkering, but in others it looks like there is some bigger conflict going on regarding my sound properties. Any help here would be greatly appreciated. Thanks.

---

### Post by pseudonym on 2006-12-29
Hmm...sounds like you may be having trouble with your sound server settings. I haven't used Gnome in a long time but I remember a useful thread [here]("http://ubuntuforums.org/showthread.php?t=44753") had some fixes. It's a tad old but I *think* it should still apply in Edgy. Curiously, though, nothing like this is mentioned in the [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), but you already checked there, right? ;)

---

### Post by ricardisimo on 2006-12-29
> **pseudonym said:**
> Hmm...sounds like you may be having trouble with your sound server settings. I haven't used Gnome in a long time but I remember a useful thread [here]("http://ubuntuforums.org/showthread.php?t=44753") had some fixes. It's a tad old but I *think* it should still apply in Edgy. Curiously, though, nothing like this is mentioned in the [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), but you already checked there, right? ;)

I did... which is how I went from no system sounds to no sound at all. Fortunately I have just enough brain cells to have undone the damage. Thanks for the other link, though. Wish me luck.

---

### Post by ricardisimo on 2006-12-29
> **pseudonym said:**
> Hmm...sounds like you may be having trouble with your sound server settings. I haven't used Gnome in a long time but I remember a useful thread [here]("http://ubuntuforums.org/showthread.php?t=44753") had some fixes. It's a tad old but I *think* it should still apply in Edgy. Curiously, though, nothing like this is mentioned in the [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), but you already checked there, right? ;)

Interesting that the link you mention says this: > Side-Effect: The Ubuntu startup sounds will go away, but i think the trade-off is worth it. This is, indeed, one of symptoms right now. Hmmm... I'm going to shop around a little more before I experiment with this guy's recommendations.

---

### Post by deadgobby on 2006-12-29
If you have a secoundary sound card. You may want to go into BIOS and disable the onboard sound card. There is GMOME ALSA mixer that can be install via synaptic. A little bit more graphcal, but does the same thing. 
Gobby

---

### Post by pseudonym on 2006-12-29
> **ricardisimo said:**
> Hmmm... I'm going to shop around a little more before I experiment with this guy's recommendations.
You're right - in its entirety that guide is a little drastic. If you narrow it down to these options it may, however, prove useful -

1. Goto System->Preferences->Sound and disable "Enable Sound Server Startup"
2. Make /etc/esound/esd.conf look like this - ```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
3. Reboot.

I'm 99.9% sure this is what I and many other users had to do back in Hoary Hedgehog to get the esd sound server to play ball.

Sorry I didn't make this clear above.

---

### Post by ricardisimo on 2006-12-29
I don't actually have the option "Enable Sound Server Startup" anywhere in that dialogue. Are you referring to "Enable software sound mixing (ESD)"?

---

### Post by pseudonym on 2006-12-29
> **ricardisimo said:**
> I don't actually have the option "Enable Sound Server Startup" anywhere in that dialogue. Are you referring to "Enable software sound mixing (ESD)"?
This is where someone who is a current Gnome user would be more helpful to you. But, to answer your question, I would say so.

---

### Post by ricardisimo on 2006-12-29
By the way, it just happened again while trying to listen to a snipe on allmusic.com... 
```
The Totem plugin could not startup.
The audio output is in use by another application. Please select another audio output in the Multimedia Systems Selector. You may want to consider using a sound server.
```
And now we return to our regular programming...

---

### Post by pseudonym on 2006-12-29
You using totem-xine or totem-gstreamer? If the latter, get rid of it in favour of the former. I started on Ubuntu 2 years ago and gstreamer is still not up to par IMHO.

---

### Post by ricardisimo on 2006-12-29
> **pseudonym said:**
> You using totem-xine or totem-gstreamer? If the latter, get rid of it in favour of the former. I started on Ubuntu 2 years ago and gstreamer is still not up to par IMHO.

It was gstreamer, but I changed it back to xine just now at your recommendation. Doesn't matter. Neither is working, altough at least I'm no longer getting the error messages, thanks to you; I changed the sound configuration file as per your instructions. I also got back at least the conga hit at login, which is something. Nothing else is back, though. Please keep the ideas coming.

---

### Post by dbqp on 2006-12-30
> Please keep the ideas coming.

Within the past few days I have also been experiencing sound issues. It seems after I installed some programs (XawTV and gYachi for webcam chat) is when the problem started. My GAIM sounds don't work as well as the problems you stated previously (login, mouseovers, etc...).

Sorry, not trying to hi-jack your post - just letting you know I am going through the same. I'll post back with any further successes/articles.

---

### Post by ricardisimo on 2006-12-30
> **dbqp said:**
> Within the past few days I have also been experiencing sound issues. It seems after I installed some programs (XawTV and gYachi for webcam chat) is when the problem started. My GAIM sounds don't work as well as the problems you stated previously (login, mouseovers, etc...).

Sorry, not trying to hi-jack your post - just letting you know I am going through the same. I'll post back with any further successes/articles.

Much appreciated. I now have one other "system sound" - the email notification from the Mailman plugin on Firefox. It's not much, but it's something.

---

